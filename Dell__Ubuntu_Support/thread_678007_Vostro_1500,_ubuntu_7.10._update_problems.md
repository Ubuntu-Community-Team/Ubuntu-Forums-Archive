---
title: "Vostro 1500, ubuntu 7.10. update problems"
date: 2008-01-25
forum: Dell  Ubuntu Support
---

### Post by Brynet on 2008-01-25
Hello!

I Just installed Ubuntu 7.10 on my Vostro 1500, and it was quite ok, except some problems with sound and nvidia drivers, which i knew there would be problems with.
So i decided to Download all updates and install them, and after that i rebooted as it was required.
[COLOR="Silver"][I]But now nothing will work, not even the wireless card. Also, it looks like its in some kind of "safe" mode, less programs up in the right corner and some different colors.
does anyone know what could be wrong? and preferably a Fix for it?:)[/I][/COLOR]
Got that thing working now, don't know how, but pressing on everything and rebooting like mad solved it.

But i still cant get sound to work i've tried th:
"sudo apt-get install linux-backports-modules-generic"
But it says there is no such thing as "linux-backports-modules-generic"

i also read that one solution was to do several steps, but the second step didn't work which was: "sudo m-a update" it says unknown command.


And one other problem, since im swedish, i choose the language swedish in the start of the installation, but its still displaying in both swedish and english, and firefox is only in english.


Thanks!


ps. computer is:
Dell vostro 1500
C2D 2Ghz 7300
2048MB ram
8600M gt
Intel N-Draft


//Brynet

---

### Post by geoffatmk on 2008-02-04
try;

sudo apt-get install linux-backports-modules
sudo apt-get update
sudo apt-get upgrade

Make sure you update the system then install restricted drivers and (I suggest) using automatix2 (2.0.5)

Hope this helps

Geoff

---

### Post by StefAndrew on 2008-02-05
Also, you can search "backports" in the Add Programs from the bottom of the applications menu.  That's how I was able to find it.  Both times I've installed Gutsy on my Vostro 1500 now, after installing and rebooting, sound works perfectly.  I did find out why my sound was so quiet too.  I had to check all of the options and make sure all the volume sliders were at max.  It's working great now.

---

