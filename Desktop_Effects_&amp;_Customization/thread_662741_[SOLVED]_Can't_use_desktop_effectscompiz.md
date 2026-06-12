---
title: "[SOLVED] Can't use desktop effects/compiz"
date: 2008-01-09
forum: Desktop Effects &amp; Customization
---

### Post by insertAlias on 2008-01-09
I can't enable desktop effects.  When I try to, I get an error message: (pic)
The Composite extension is not available.
[ATTACH]55813[/ATTACH]

This is what happens when I run the command compiz.
```
curtisr@curtisr-laptop:~/Documents$ compiz
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

```

I have attached the output from glxinfo and my xorg.conf.
Link: [ATTACH]55814[/ATTACH]
Link: [ATTACH]55815[/ATTACH]

I know that 3d acceleration is enabled, glxgears works fine and I can use my 3d screensavers.

Thanks in advance!

---

### Post by codesplice on 2008-01-09
Try changing the bottom of your xorg.conf file from 
```
Section "Extensions"
	Option		"Composite"	"0"
EndSection
```

to 
```
Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

```

Restart X and see if that works.

---

### Post by insertAlias on 2008-01-09
Thanks for your reply, codesplice.  When I do that, I get a new error message when I try to enable Desktop Effects (pic)
Desktop Effects could not be enabled.
[ATTACH]55817[/ATTACH]

---

### Post by codesplice on 2008-01-09
What happens when you try to launch compiz from a terminal?

---

### Post by insertAlias on 2008-01-09
The same:
```
curtisr@curtisr-laptop:~$ compiz
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
```

---

### Post by codesplice on 2008-01-09
Do you have XGL installed? :)

Package name is xserver-xgl, i believe.

---

### Post by insertAlias on 2008-01-09
Thank you very much.  That was the answer! (I kinda feel stupid now.  That was the first thing I should have checked!)

---

### Post by codesplice on 2008-01-09
Haha, no biggie.  I've pulled stunts like that before. 

I should've picked up on it quicker.  "Checking for xgl..... not present" should have been a dead giveaway.

Anyhoo, glad I could help :)

---

