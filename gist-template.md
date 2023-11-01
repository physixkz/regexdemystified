# Regex Tutorial Matching a Hex Value

Regex, short for regular expressions, are like secret codes used to find specific patterns in text. This tutorial will teach you how to use regex to identify Hexadecimal Values.

## Summary

/^(?:#)?([0-9a-fA-F]{3}|[0-9a-fA-F]{6})$/

This pattern helps you find hexadecimal color codes in text. To find a match, the color code must start and end the text.

This pattern works for both short (3-character) and long (6-character) color codes. Sometimes, the color code starts with a #, but it's not always necessary.

For example, #fff and 000aaa are okay, but fff9 or fffa won't work.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Flags](#flags)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Boundaries](#boundaries)
- [Back-references](#back-references)
- [Look-ahead and Look-behind](#look-ahead-and-look-behind)

## Regex Components

### Anchors

Anchors in regex are like boundaries that help you define where a match should start or end in a text. Let's break it down:

The caret (^) acts like a starting point. If you use it, the match must begin at the very beginning of the text. For instance, /^aee/ would match 'aee,' but not '123aee' or '0x123aee.'

On the other hand, the dollar sign ($) is like a finish line. When you use it, the match should end at the very end of the text. For example, /fff$/ would match '000fff,' but not 'fff000.'

You can also combine these anchors in the same pattern, like /000fff$/, which ensures the match begins at the start and ends at the end of the text. So, it's like marking both the start and finish lines for your match.

### Quantifiers

In regex, quantifiers are like counters that help you decide how many times something should appear:

The star () means "zero or more times." So, if you use /00f/, it will match '00,' '00f,' or '00ffffff' because it allows for zero or more 'f' characters.

The plus sign (+) means "at least once." If you use /00f+, it matches '00f' or '00ffffff' because it requires at least one 'f' character.

The question mark (?) means "zero or one time." For example, /00f?/ matches '00' and '00f,' but not '00ffffff' because it allows for either zero or one 'f' character.

Curly brackets let you specify an exact number of matches. x{n} means 'x' must appear exactly 'n' times, x{n,} means it must appear 'x' 'n' or more times, and x{n,m} means it can appear between 'n' and 'm' times.

Just the question mark alone means "zero or one time." You can also use it to make matches "lazy" when combined with other quantifiers.

By understanding these quantifiers, you can precisely control how many times something should match in your regex, making it a powerful tool for finding patterns in text.

### OR Operator

In regex, you can use the OR operator (|) to make choices. It's like saying, "I want to find one of these things."

For example, if you want to find values like 80, 90, a0, or b0 in text, you can write a regex like this: /80|90|a0|b0/. It means that if any of these values are in the text, it's a match. You have multiple options, and you'll find a match if at least one of them is there.

### Character Classes

In regex, character classes help you say which characters are okay in a match.

To match something like "ffx" in a hex number where 'x' can be any hex character, you can use a character class. For example, /ff[abcdef0123456789]/ means the match should be "ff" followed by any of these characters in the brackets.

You can also use shortcuts like /ff[a-f0-9]/, which covers the range of characters you want. This one says, "Match 'ff' followed by a character from 'a' to 'f' or a digit from '0' to '9'.

Shortcuts like 'd' (for digits), 's' (for spaces), and 'w' (for word characters) can save time.

The opposite of these shortcuts is 'D' (not a digit), 'S' (not a space), and 'W' (not a word character).

The dot (.) matches almost any character, except a new line. Think of it as a wild card.

So, character classes help you pick which characters you're looking for, and it makes your regex more specific.

### Flags

In regex, flags are like magic buttons that change how things work.

The "i" button (for case-Insensitive) makes regex not care about big or small letters. So, /ffff/i will find 'ffff,' 'FFFF,' or 'ffFF,' no matter how you type it.

The "g" button (for global) helps regex look for things everywhere, not just once. If you use it, regex keeps searching for more matches in the whole text, not just the first one.

The "m" button (for multi-line) makes regex pay attention to each line's beginning and end, not just the whole text's beginning and end. It's like focusing on each line separately.

Using these buttons can make regex much easier and more powerful, like turning on special features when you need them.

### Grouping and Capturing

In regex, think of grouping like putting words in brackets. It makes them act as one thing.

When you use ( ), each group gets a number. You can talk about it later if you want. But if you don't want to, use (?:text) to make it quiet.

For example, in /a(ff)/, it finds 'aff' and 'ff' together. You can use it for more things, like /a(ff)2/ for 'affff' or /f(11|00)/ for 'f11' or 'f00'.

Grouping helps you organize your regex, like putting stuff in boxes so you can work with it easily.

### Bracket Expressions

In regex, bracket expressions are like guest lists for a party. They help you say who's allowed in.

You can use them to make a list of characters you want to invite. For example, [a-f] means you're inviting everyone from 'a' to 'f' to your party.

If you add a caret (^) at the start, like [^g-z], it means everyone except 'g' to 'z' is on the guest list. You're saying, "Everyone's invited except 'g' to 'z.'"

So, it's like managing your party guest list with these brackets, making it easy to decide who's in and who's out in your regex match.

### Greedy and Lazy Match

In regex, it's like two ways of finding things in a string:

Greedy is like a big eater, grabbing as much as possible. For example, /fa+/ will take 'faaa' because it wants lots of 'a's.

Lazy is like a tiny nibbler, taking as little as possible. With /fa+?/, it gets just 'fa' in 'faaa' because it's careful and wants the smallest bit.

### Boundaries

In regex, boundaries are like fences that say where a match should be.

Imagine you want to find a word, like "af800," but only if it's surrounded by empty spaces. So, you use regex to make a rule: /af800/ means "find 'af800,' but only if there are spaces before and after it, like ' af800 '."

Boundaries help you set rules for where your match should be in the text. It's like telling regex where to look.

### Back-references

In regex, back-references help you use stuff you found earlier.

Let's say you found some special stuff like (123) and (fff) with your regex. You can give them numbers, like \1 for (123) and \2 for (fff). 

Back-references in regex are like using a magic stamp. Imagine you have a stamp with a star on it. You can stamp that star in one place, and then you can use the same stamp to put stars in different spots in your coloring book. It's like using the same stamp over and over to make your book look cool. In regex, it means finding something special and using it again in different parts of your pattern.

### Look-ahead and Look-behind

In regex, look-ahead and look-behind are like secret codes that help you make more specific matches based on what comes before or after something.

Think of look-ahead like a detective who needs a specific clue to find something. In our case, we're searching for 'ffff' in a text, but we only want it if it's immediately after '0x'. So, our detective uses a special tool, like /(?=0x)ffff/, to say, "I'll find 'ffff,' but only if '0x' is right in front of it in the text." It's a way to be very precise in our search.

On the other hand, a look-ahead is like checking what comes after. For instance, in '0xcafed00d,' you can use /0xcafe(?=d00d)/ to match '0xcafe' only if it's followed by 'd00d.' It's like saying, "Find '0xcafe,' but only if it's followed by 'd00d.'"

So, look-ahead and look-behind are like looking for things with specific friends before or after them in your text. It helps you find things in a more precise way.

## Author

Freddy Guerra - Github: https://github.com/physixkz