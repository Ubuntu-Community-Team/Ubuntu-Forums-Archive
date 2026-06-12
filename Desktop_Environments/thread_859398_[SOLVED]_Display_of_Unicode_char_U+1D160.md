---
title: "[SOLVED] Display of Unicode char U+1D160"
date: 2008-07-14
forum: Desktop Environments
---

### Post by kkjaergaard on 2008-07-14
Why am I not able to see all Unicode characters in Gucharmap? I want to se U+1D160 (MUSICAL SYMBOL EIGHTH NOTE), but I just see the default box with the index of the char.

---

### Post by mcduck on 2008-07-14
> **kkjaergaard said:**
> Why am I not able to see all Unicode characters in Gucharmap? I want to se U+1D160 (MUSICAL SYMBOL EIGHTH NOTE), but I just see the default box with the index of the char.

Could be that the font you are using doesnt have that character..

---

### Post by kkjaergaard on 2008-07-14
> **mcduck said:**
> Could be that the font you are using doesnt have that character..

Which fonts support this character (or all Unicode characters)? I'm using the default font Sans (I suppose it's called the same in English).

---

### Post by mcduck on 2008-07-15
> **kkjaergaard said:**
> Which fonts support this character (or all Unicode characters)? I'm using the default font Sans (I suppose it's called the same in English).

I have no idea, and I haven't got access to any Linux machine right now so I really can't even check..

But if I remember right the character browser in Ubuntu allows you to try wiith diferent fonts. So you could try browsing with it to the correct character and then testing the different fonts until you find one that works.

Anyway, I don't think there even is a font that would support all characters available in Unicode. That would require adding characters for all living languages used in the whole world, and a lot more like old norse runes (actually supported in some of the fonts included in Ubuntu! :o) and some egyptian hieroglyphs etc.. Wikipedia mentions that the latest version of Unicode includes 100713 different characters..

edit: take a look at this: [http://en.wikipedia.org/wiki/Free_software_Unicode_typefaces]("http://en.wikipedia.org/wiki/Free_software_Unicode_typefaces")

---

### Post by kkjaergaard on 2008-07-15
I guess I have to consider this thread solved then. Thanks - though I didn't really find a solution.

---

### Post by simosx on 2008-08-30
There are different sources of fonts; for "Plane 1" Unicode characters (such as the musical symbols you mention), you can install the fonts from 
[http://users.teilar.gr/~g1951d/](http://users.teilar.gr/~g1951d/)

I think it covers whatever is available in Plane 1 (ancient scripts), including the recently-added new characters in Unicode 5.x.

---

