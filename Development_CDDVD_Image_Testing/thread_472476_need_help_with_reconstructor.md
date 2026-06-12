---
title: "need help with reconstructor"
date: 2007-06-13
forum: Development CD/DVD Image Testing
---

### Post by Sir P on 2007-06-13
hi there,

I'm using reconstructor to customise a live CD, though having trouble working out how to install problems on it - i see the module and apt-get (install) box but nothing really happens when I click apply.

Second question is, the modules on the site you can download are in a rmod format, how do I build a live boot image from one of these modules?

many thanks for any support or pointers you can give
regards
Sir P :D

---

### Post by smartboyathome on 2007-06-13
I have had much trouble with Reconstructor. If you would like to remaster a livecd, then I would suggest you use UCK (Ubuntu Customization Kit). If you would still like to use Reconstructor, I have a few tips:

The mods don't work (at least not for me), and neither does the apt-get line (there are no sources for apt-get to go off of) so I would not even try to use them. Instead, use the terminal (located in the bottom left corner). You will have to be running the same distro as the one you are remastering in order for you to copy/paste your sources from your running linux to your remaster. I have a complete set of instructions here (it erases the repos and the keys to the ubuntu repos after the first remaster, so if you forgot something, then you will have to start fresh):

[http://reconstructor.aperantis.com/index.php?option=com_joomlaboard&Itemid=&func=view&catid=3&id=369#369](http://reconstructor.aperantis.com/index.php?option=com_joomlaboard&Itemid=&func=view&catid=3&id=369#369)

You will want to do everything from the command line. I hope this helps you! ^_^

---

### Post by SalgerKlesk on 2007-06-14
> **smartboyathome said:**
> I have had much trouble with Reconstructor. If you would like to remaster a livecd, then I would suggest you use UCK (Ubuntu Customization Kit). If you would still like to use Reconstructor, I have a few tips:

The mods don't work (at least not for me), and neither does the apt-get line (there are no sources for apt-get to go off of) so I would not even try to use them. Instead, use the terminal (located in the bottom left corner). You will have to be running the same distro as the one you are remastering in order for you to copy/paste your sources from your running linux to your remaster. I have a complete set of instructions here (it erases the repos and the keys to the ubuntu repos after the first remaster, so if you forgot something, then you will have to start fresh):

[http://reconstructor.aperantis.com/index.php?option=com_joomlaboard&Itemid=&func=view&catid=3&id=369#369](http://reconstructor.aperantis.com/index.php?option=com_joomlaboard&Itemid=&func=view&catid=3&id=369#369)

You will want to do everything from the command line. I hope this helps you! ^_^

How to change deeper graphic details from the terminal?

---

### Post by smartboyathome on 2007-06-14
If you are talking about themes, Metacity might be able to do that for you from the command line. Otherwise, I would not know. :-\

---

### Post by Sir P on 2007-06-14
Thanks for the reply Smartboy, I installed UCK and just removed/installed some packages, just burning to CD now to try it out :)

Coudnt find anyway to change boot logos or wallpapers in UCK though, is it possible through those?

Many thanks for your time :)

---

### Post by SalgerKlesk on 2007-06-14
> **Sir P said:**
> Thanks for the reply Smartboy, I installed UCK and just removed/installed some packages, just burning to CD now to try it out :)

Coudnt find anyway to change boot logos or wallpapers in UCK though, is it possible through those?

Many thanks for your time :)

I have the same problem. Is it possible to do this from the command line instead of using the gui (that obviously doesn't work)?

Thanks...

---

### Post by stepan2 on 2007-07-08
i don't know what you guys are talking about . reconstructor wokred wonders for me. everything worked there.

---

### Post by smartboyathome on 2007-07-09
You are lucky then. I could not get reconstructor to work at all. btw, did you test the ISO made with reconstructor to see if it worked?

---

### Post by candtalan on 2007-07-28
All I want to do is change boot screen usplash and a wallpaper, but Reconstructor does not work successfully for me. I note that when it first starts, In the Terminal I get

Terminal:
=================
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

Reconstructor -- (c) Reconstructor Team, 2006
       Version: 2.6
        [http://reconstructor.aperantis.com](http://reconstructor.aperantis.com)

Checking dependencies...
Ok.
=================

Any idea what this is about?

---

