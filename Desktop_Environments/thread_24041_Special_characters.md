---
title: "Special characters"
date: 2005-04-05
forum: Desktop Environments
---

### Post by jeremy on 2005-04-05
I use a spanish keyboard which does not have a tilde ( ~ ), know that with windows   one can type ALT + 126 to get this, is there anything similar in linux?

I can do it by copying and pasting from character map, but would like to do it with the keyboard.

---

### Post by bonifacio on 2005-04-05
Applications/Accessories/Character Map

---

### Post by Svictor on 2005-04-05
Yes there should be. Just use CTRL+SHIFT instead of ALT. However, it appears that 126 is not the unicode codenumber for the tilde. I'm not quite sure about the charset used in WindowsTM, but in Ubuntu (Hoary), it seems to be unicode. So you'd better try CTRL+ SHIFT +7E in order to get a tilde. You can find all unicode characters in Applications --> Accessories --> Character Map. Look for their number at the bottom of the window. Hope it helps

---

### Post by wmcbrine on 2005-04-05
[QUOTE=Svictor]However, it appears that 126 is not the unicode codenumber for the tilde. ... So you'd better try CTRL+ SHIFT +7E in order to get a tilde.[/QUOTE]
126 decimal = 7E hexadecimal. Different entry methods, not different codes. This character is (barely) in the ASCII range, so it's the same in UTF-8, Windows-1251, and most other character sets.

---

### Post by jeremy on 2005-04-05
CTRL+ SHIFT +7E works perfectly, many thanks for your trouble.

---

### Post by ipixel on 2005-05-22
I, too, need to type international characters, and am at a total loss in Kubuntu PPC. I tried using a combination of 'US INTERNATIONAL' keyboard, + a 'compose key' setting. This helped me get a couple of my needed characters, but not all.

I tried following the instructions on the previous messages in this thread, but I must be missing something obvious, because when I type CONTROL+SHIFT+7E all I get on my screen is : '&E'.

The characters I need to get are:

c + ^ = c circumflex
g + ^ = g circumflex
h + ^ = h circumflex
s + ^ = s circumflex
j + ^ = j circumflex
and u + breve (I don't even know where the breve would be on my keyboard). The 'breve' is a downwards semicircle, like the bottom half of a circle.

These 6 characters are used in Esperanto, the international language.

I also need to type LOTS of other international characters, which I have no idea how to get: the s-z in German, the french cedilla, umlaut over a, o and u, o-slash, and - of course - the tilde (not just over the n, but also over the a and o, for Portuguese).

Kubuntu/Ubuntu is supposed to be 'internationalised´, but I'm finding it *extremely* hard to use it for anything other than standard English...

Any suggestions greatly appreciated.

---

### Post by jeremy on 2005-05-22
In kubuntu you will have to play around with th Alt Gr key, eg 'Alt Gr + 5' gives me '½' on my spanish keyboard.

---

