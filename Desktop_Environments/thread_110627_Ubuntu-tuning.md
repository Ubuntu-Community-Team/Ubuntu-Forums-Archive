---
title: "Ubuntu-tuning?"
date: 2005-12-31
forum: Desktop Environments
---

### Post by Edho on 2005-12-31
I think working in Ubunty is a little slower compared to WinXP.

Is it possible speeding up the Ubuntu OS breezy 5.10?
(I did just the install from the cd,... update/upgrade not yet)

In the view of hardware...
Will mounting more RAM- memory make the system remarkable faster?

AMD Duron 1 Ghz - 256Mb RAM.

Thank you and Happy Newyear !

---

### Post by drfalkor on 2005-12-31
you could try:
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install linux-k7 (EDIT: wops, forgot the install thingy)

reboot

and you can turn off all the eyecandy- or, you can install kubuntu (kubuntu is like ubuntu, only it use kde)

---

### Post by drfalkor on 2005-12-31
AND install the graphic card driver !
EDIT: more RAM would be great for you'r box ! :)

---

### Post by marks_linux on 2005-12-31
and you can never have too much memory ;) I have two systems one with 512mb and one with 1gig. the system with 512 lagged a bit with only 256mb.

Which desktop are you using? kde or gnome. Not wanting any flames wars, but I find gnome kinder to resources.

You could do a simple 'top' command and see if you are using swap space. Also what are you using the comp for? there may be services that can be closed, if for example you aren't running a web server etc.

---

### Post by Edho on 2005-12-31
Install the grap.card-driver?
Did'nt Ubuntu during install?
It's a SiS 730 all-in mobo and the screen works good.
------------------------
I use Gnome.
'Top' command is interresting. (thanks)
Mem: only 7.5 Mbyte free.
Swap: 12 Mbyte used
AND that's with only Firefox running!
Maybe more mem is recommanded.
------------------------
As a beginner with Linux, i am afraid to updating or messing around... to soon.
When things go wrong, i can't fix it.

BTW... is  a system-repair (goback) like in Windows available?

Edho.

---

### Post by Timokl on 2005-12-31
[QUOTE=Edho]Install the grap.card-driver?
Did'nt Ubuntu during install?
It's a SiS 730 all-in mobo and the screen works good.[/QUOTE]

If ubuntu does not find a suitable driver for your card, it uses a very basic driver. It shows graphics, but it might be rather slow -- at least in comparison how quick it could be. :smile: 

Happy New Year!

---

### Post by pharcyde on 2005-12-31
You could also try a light x-window manager.  I use fluxbox and it is very light and fast.

---

### Post by StepanIjin on 2007-07-19
How can I check if my Nvidia card drivers were installed? I used the procedure from Nvidia website and the name ov device changed from nv to nvidia. However, how can I check ny drivers?
Thank you

---

### Post by eentonig on 2007-07-19
Upgrading to the latest release doesn't always means 'slower'

I found that upgrading from edgy to Feisty actually improved a lot of experience.

---

