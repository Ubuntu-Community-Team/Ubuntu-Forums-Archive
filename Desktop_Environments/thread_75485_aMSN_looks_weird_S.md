---
title: "aMSN looks weird :S"
date: 2005-10-13
forum: Desktop Environments
---

### Post by agu5tin on 2005-10-13
I've just upgraded to Breezy (rocks ;)) buttttt i have a problem with aMSN. I don't know why the letters in aMSN's window have BIG spaces between them. It's like this:
> 
T h i s   i s  h o w  i t  l o o k s.  I t ' s  a n n o y i n g,  p l u s  u n r e d e a b l e 


How can i fix this??

i asume it has something to do with TCL/Tk but i have no idea how to fix it.

Any help is welcome :)

---

### Post by mlomker on 2005-10-13
Is it the only program that does it?  I assume you've checked the font settings in kcontrol.

---

### Post by agu5tin on 2005-10-14
Yeap, is the only program that does that.
Both the Ubuntu Package of AMSN and the CVS Build of aMSN.

I've checked and re checked the Kcontrol Font configuration, and i asume it has nothing to do with that, because the front end of aMSN is done with TCL/TK and it doesn't use the same fonts that the rest of the system. Or at least that's what i've think i know.

---

### Post by mlomker on 2005-10-14
> Or at least that's what i've think i know.

Ah, I thought it might be a gtk application.  It looks like the gtk font applet is installed by default in Kubuntu now, which is nice (just did a fresh install this morning).

---

### Post by agu5tin on 2005-10-17
Problem solved... as silly as it might sound, just RE setting the general font on the aMSN options solved the problem. The thing is i couldn't see that option becuase of the size of the letters.

---

