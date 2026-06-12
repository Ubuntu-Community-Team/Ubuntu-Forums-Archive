---
title: "apt-get and regex matching"
date: 2008-12-09
forum: General Help
---

### Post by pytheas22 on 2008-12-09
A quick question: when I type 'sudo apt-get remove wine*', I get output like this:
```

Note, selecting libwine-print for regex 'wine*'
Note, selecting kwin-style-blended for regex 'wine*'
Note, selecting wxwin2.4-headers for regex 'wine*'
Note, selecting libwine-jack for regex 'wine*'
Note, selecting libchewing3-dev for regex 'wine*'
Note, selecting windows-el for regex 'wine*'
Note, selecting wxwin2.4-doc for regex 'wine*'
Note, selecting winefish for regex 'wine*'
Note, selecting wxwin-i18n for regex 'wine*'
Note, selecting libchewing3-data for regex 'wine*'
Note, selecting libwine-gphoto2 for regex 'wine*'
Note, selecting kdeartwork-theme-window for regex 'wine*'
Note, selecting plplot9-driver-xwin for regex 'wine*'
Note, selecting fte-xwindow for regex 'wine*'
```

(and that's only the beginning of the list).  In other words, apt-get seems to be matching packages with the string *win* anywhere in their names for the regex *wine**.  This is perplexing me for two reasons:

1) why does the 'e' in wine get ignored?
2) why does it match packages with *win* anywhere in their names, as opposed to only those that begin with the expression 'win'?  I thought I'd need to use a regex like 'apt-get remove *win*' if I wanted to make it behave as it is.

I'm no programmer or regex guru, so I could definitely be missing something simple.  But if anyone could point it out to me, I'd be grateful.

---

### Post by sisco311 on 2008-12-09
[quote=man apt-get] If no package matches the given expression and the expression
           contains one of ´.´, ´?´ or ´*´ then it is assumed to be a [B]POSIX
           regular expression[/B], and it is applied to all package names in the
           database. Any matches are then installed (or removed). Note that
           matching is done by substring so ´lo.*´ matches ´how-lo´ and
           ´lowest´. If this is undesired, anchor the regular expression with
           a ´^´ or ´$´ character, or create a more specific regular
           expression.
[/quote]

^ matches the starting position within the string.
$ matches the ending position of the string.
* matches the preceding element **zero or more times**. For example, ab*c matches "ac", "abc", "abbbc", etc. [xyz]* matches "", "x", "y", "z", "zx", "zyx", "xyzzy", and so on. \(ab\)* matches "", "ab", "abab", "ababab", and so on.


try
```
apt-get remove ^wine.*
```
or just:
```
apt-get remove ^wine
```

[http://en.wikipedia.org/wiki/Regular_expression#**POSIX**]("http://en.wikipedia.org/wiki/Regular_expression#POSIX")

---

