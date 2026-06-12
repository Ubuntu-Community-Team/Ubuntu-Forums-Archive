---
title: "how to insert a unicode character in kate?"
date: 2009-03-02
forum: General Help
---

### Post by 77bridge on 2009-03-02
Hi!

I want to insert a unicode character like the greek sigma or theta in the Kate editor, but how can I do this?  I assume I can enter its hexcode, but is there some escape character I need to use to tell the editor that this is supposed to be a unicode character?  What is the secret?

For example, I cannot just enter 0x03C3 and see the value.

Thanks!!!!!

---

### Post by yther on 2009-03-02
Have you checked Tools > Encoding to make sure it's set to Unicode/UTF-8?

If so, then assuming (1) you can enter those characters, and (2) your selected font can display them, it should work.

---

### Post by 77bridge on 2009-03-02
the encoding is UTF-8, and the current font is monospace.  I don't know how to check whether a font has the full range of unicode characters, so let me know if you have any ideas there.

Thanks!!!

---

### Post by JMeursault on 2010-11-05
Google always sends me here, when I've forgotten how to enter unicode characters in kate, so I decided to answer it by myself:
Press F7 to switch to command line and enter: char 0x03C3

---

### Post by The Cog on 2010-11-05
Press Ctrl-Shift-U then enter the hexadecimal unicode value then follow with Enter or Space. Pressing these keys:
```
Ctrl-Shift-U
3
C
3
Enter
```
produces &#963;

---

