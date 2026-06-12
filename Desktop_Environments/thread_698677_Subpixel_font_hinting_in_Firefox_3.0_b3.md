---
title: "Subpixel font hinting in Firefox 3.0 b3"
date: 2008-02-16
forum: Desktop Environments
---

### Post by darktempest on 2008-02-16
Is anyone else having trouble with font hinting in the latest firefox and gnome?  The application will render everything else great, but there's no font hinting to be seen.  It hurts the eyes something feirce.

---

### Post by nemilar on 2008-02-16
Seems to be working fine for me.  If I am understanding things correctly, Firefox 3 uses your system defaults for things like drop-downs, fonts, check-boxes, etc.  So maybe check that your font settings in gnome are configured correctly?

A screenshot would be helpful.

---

### Post by darktempest on 2008-02-16
> **nemilar said:**
> Seems to be working fine for me.  If I am understanding things correctly, Firefox 3 uses your system defaults for things like drop-downs, fonts, check-boxes, etc.  So maybe check that your font settings in gnome are configured correctly?

A screenshot would be helpful.

Sorry bout that, screenshots as requested

Firefox2.png is Firefox 2.0.0.12
Firefox3.png is Firefox 3 beta 3

I know its kind of hard to distinguish but on my LCD, firefox 3 has sparklies all around the font edges and look rough.  FF2 all nice and smooth.

---

### Post by oedipuss on 2008-04-02
Sorry to revive an old thread but I've been having the exact same problem from ff 3b3 through today with beta5... To be more specific, I think it's not that firefox doesn't do subpixel hinting, it's that it does it too much or just differently than everything else.. 
There is colorization on the edges of some letters, while others appear too crisp as if sharpened.


See below, firefox3 beta5 menu bar next to a menubar from another app. Compare with next screenshot, which is firefox2 menubar and terminal menubar. 
Also some text from ubuntuforums, the first one is from firefox3 beta5 and the second from firefox2.

Are others seeing this as well? Is there some way to fix this? 

PS: My font settings are set to subpixel smoothing with full hinting, and I'm using the Liberation fonts, in ubuntu gutsy.

---

### Post by mgol on 2008-04-03
> **nemilar said:**
>  Firefox 3 uses your system defaults for things like drop-downs, fonts, check-boxes, etc.
Actually, this is not true. I have hinting turned on and it works fine everywhere except for OOo2 and F3b4/5. It seems that Fx doesn't use system settings.

---

### Post by riven0 on 2008-04-04
Just wanted to say, I have the same problem. I tried starting firefox 3 with:** firefox --enable-system-cairo**, but it doesn't help, at all. I hope they get this fixed soon, I love everything about firefox 3 except for the awful font rendering.

---

### Post by oedipuss on 2008-04-07
Judging from [this thread ]("http://ubuntuforums.org/showthread.php?t=665486") firefox must be *compiled* with the -enable-system-cairo option, for fonts to look like other apps. This is both good and bad, good because the official package will presumably be compiled correctly , but I'm sure compiling something like firefox isn't an easy process. 
For the record, the current package in the repos (beta3 iirc) doesn't show any improvements.

---

