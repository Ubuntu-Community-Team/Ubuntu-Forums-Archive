---
title: "non-ascii characters"
date: 2009-06-01
forum: General Help
---

### Post by klirka on 2009-06-01
Hello, 

I am using as default a German keyboard layout on an English kubuntu system. Both is fine, and all my newer applications display let me type and display all those non-ascii characters from German and other European languages correctly. But two older applications do not, and since their development seems frozen, I would like to do something about this myself.

1) One application lets me type German characters and displays them, but cannot display the Slovak special characters that my friend is sending me in his text.

2) Another application goes even beyond that. When I type German characters with my default keyboard layout, then it does not know how to display them and gives me "Ã¶" instead of "ö", "Ã¤" instead of "ä" etc.

What can I do?

---

### Post by klirka on 2011-01-06
i will close this as "solved" now. 
just in case someone reads this: i have forgotten the exact procedure, but i think what finally helped me was:

```
- to find the right encoding on http://en.wikipedia.org/wiki/Code_page
- to read "man iconv" on konsole and change the file's encoding
- to check the file in kate.
```

cheers

---

