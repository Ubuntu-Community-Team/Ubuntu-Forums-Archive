---
title: "Hello everybody!"
date: 2008-02-04
forum: Desktop Effects &amp; Customization
---

### Post by luchino1976 on 2008-02-04
Hello. sorry for my english but I'm italian.
I have on my pc UBUNTU 7.10, and I've got a problem with all visual effects.
I have Motherboard Asrock P4VM900-sata2, with Pentium4 3.0GHZ.
If I make glxinfo | grep rendering

luca@luca-desktop:~$ glxinfo | grep rendering
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
luca@luca-desktop:~$

and if I make lspci | grep VGA

luca@luca-desktop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: VIA Technologies, Inc. Chrome9 HC IGP (rev 01)
luca@luca-desktop:~$

so, I need somebody to help me!!!:(:(:(
Thanks 
Luca

---

### Post by luchino1976 on 2008-02-04
Please, help me!!!:(:(

---

### Post by luchino1976 on 2008-02-05
:confused::confused:THERE'S NOBODY????:confused::confused:

---

### Post by Keks01 on 2008-02-05
What kind of graphics card do you have? Ati or nVidia? Have you tried installing drivers for your card?

edit:
hmm.. just noticed you have an integrated vga.. no experience with these.. sorry ;)

imo. more people would visit your thread if it had a better title - something that describes your problem, not just a greeting.

---

### Post by Fraktyl on 2008-02-05
Try following the steps on this website:
[https://help.ubuntu.com/community/UniChrome](https://help.ubuntu.com/community/UniChrome)

---

### Post by vikasvishnu on 2008-02-05
> **Fraktyl said:**
> Try following the steps on this website:
[https://help.ubuntu.com/community/UniChrome](https://help.ubuntu.com/community/UniChrome)

Well, IMHO, the very first thing that you need to check is for the correct drivers for your graphic card. I see that you are using one from VIA (might be an integrated VGA that comes along with your MoBo). The visual effects needs Graphics acceleration and so you need to make sure that the direct rendering is enabled first. I will search for some guides which shall help you do this and if I get one, I will certainly post that in your thread itself. I also believe that others here who got the same config as you should be able to help you with this. 

-:Vikas:-

---

