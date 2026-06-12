---
title: "Advice wanted for installing/setting up my laptop"
date: 2006-09-20
forum: Desktop Environments
---

### Post by n00b@linux on 2006-09-20
I have an IBM Thinkpad T40p with:
- 1.5GHz Pentium M CPU
- 512MB DDR RAM
- ATi Mobility Radeon 7500
- 100GB IDE Samsung
 
I have tried numerous distros on it (inc. Ubuntu and Xubuntu) and am currently using Kubuntu.
 
In terms of apps, I seldom use anything other than:
- web browser
- e-mail client
- video player
- file manager
- word processor
- spreadsheet
- GIMP
- Amarok
 
I have tried Xgl/Compiz on Kubuntu and it worked, but it was very slow.  I think this is because of my low end graphics card.  Is there anything I can do to speed it up?
 
I use transparency for my windows and this does slow things down.  Again, is there any thing I need to check in xorg.conf to make sure things have been optimised?
 
Finally, would I be better off running a different desktop, eg. fluxbox or enlightenment?
 
Any help you can give is appreciated.

---

### Post by lagagnon on 2006-09-20
> **n00b@linux said:**
>  
I have tried Xgl/Compiz on Kubuntu and it worked, but it was very slow.  I think this is because of my low end graphics card.  Is there anything I can do to speed it up?

Do you have the proper ATI driver installed? If so NO, if not read the HOWTOS on how to install the correct ATI drivers.
[http://www.ubuntuforums.org/showthread.php?t=131253&highlight=ATI](http://www.ubuntuforums.org/showthread.php?t=131253&highlight=ATI)
If that link is not right for you just search the HOWTO forum for ATI.
>  
I use transparency for my windows and this does slow things down.  Again, is there any thing I need to check in xorg.conf to make sure things have been optimised?

See above.
>  
Finally, would I be better off running a different desktop, eg. fluxbox or enlightenment?

Xgl/Compiz demand a fairly good graphics card with the correct drivers. If your system is too slow even with the correct ATI drivers and correct xorg.conf configuration then I would recommend removing Xgl and using the standard KDE desktop. You have 512MB of ram so it would not be necessary really, to use a lighter window manager.

---

### Post by nullmind on 2006-09-20
Looks like this has already been done for us:

[http://www.newt.com/debian/thinkpad-t40p/](http://www.newt.com/debian/thinkpad-t40p/)

You'll also want to install the ATI drivers, or check if you have any hardware acceleration currently:

```

glxinfo | grep -i rendering

```

If you see Direct Rendering: Yes, you are likely hardware-accelerated. If you see a No, this would explain why Xgl/Compiz was so slow. See the guide on installing ATI drivers in the HowTo section.

Cheers,
Kris

---

