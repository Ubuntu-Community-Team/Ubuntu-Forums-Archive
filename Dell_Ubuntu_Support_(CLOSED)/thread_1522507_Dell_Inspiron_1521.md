---
title: "Dell Inspiron 1521"
date: 2010-07-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by keveye on 2010-07-02
Hello,

I just installed the latest edition of Ubuntu, on a dell that was previously running Windows Vista.

At the end of the installation, after I clicked restart a list of errors came up on a black page, I'm not 100% sure about what they said as I didn't pay too much attention, I just manually shut the computer down. It was something like I/O port or along those lines.

Upon the reboot, after the bios page it went to another error page which said something along broadacom which I think is my wireless card, and some 'cannot find file xxx' it could not find multiple files, but continued to boot into ubuntu.

Everything seems okay, despite the errors but Ubuntu cannot detect my wireless card, on the bar at the top it just has a wireless symbol with a red exclamation mark over it and when you hover it says both wired and wireless networks are disconnected.


Is there something additional I need to do to get the wireless card working, and should I be worried about the errors I received at installation?


cheers,

Kevin.

---

### Post by keveye on 2010-07-02
I have got the wireless working with the aid of this tutorial: [http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html](http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html) but should I be worried about the errors I recieved at installation, or is it normal?

cheers,

Kevin

---

### Post by jarviser on 2010-07-03
It seems to be "normal" for Broadcom wifi to behave really badly. The rest of the install should be OK.  I reckon it must be one of the most common help topics on here, probably why nobody answered you. 
Personally I would get an Intel wifi card if Broadcom can't get their act together. 
 My 1520 with an Intel wifi card installed 10.04 and behaved perfectly straight out the box. However, the broadcom fixes do seem to work, but you may have to repeat it on major updates.

---

### Post by /b/rotard on 2010-07-03
go in the terminal and put "lspci | grep Network" so I can see what card you have exactly. The person above is rigth, the broadcom fixes from their site are USUALLY ok. but sometimes they have a history of being less consistent with thier wireless drivers.

---

