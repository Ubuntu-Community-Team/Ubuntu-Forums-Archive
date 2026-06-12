---
title: "odd Resolution???"
date: 2009-04-29
forum: General Help
---

### Post by Hellstudios on 2009-04-29
[IMG]http://i207.photobucket.com/albums/bb134/hellstudios/Screenshot-13.png[/IMG]



This only began to happen after I hooked my monitor up to an old windows ME computer to see if it worked... now I can't get my old 1600 by 1200 resolution back, and I'm stuck at 60 hz refresh rate....


Help! I hope someone knows the problem.


Thanks, Hellstudios.

---

### Post by Hellstudios on 2009-04-29
Somebody please help! :(

---

### Post by Hellstudios on 2009-04-29
*Bump* -- any bit of the tiniest of help will....HELP! please, someone!

---

### Post by Leed on 2009-04-29
All I can say is that something went wrong with the graphic drivers since upgrade to Jaunty


My resolution drops out on every reboot, fortunately it works when I set it up using the proprietary driver, it's just stupid doing it every time

---

### Post by regor210 on 2009-04-29
I do not Know what property driver you may or may not be using.

you could try sysinfo 

sudo apt-get install sysinfo

And see if you have a property Display Setting tap. If yes you could use.

sudo sysinfo

Root to lock in and save your settings


If your not using property display drivers you could try.

sudo dpkg-reconfigure -phigh xserver-xorg

or

When you first start your computer and see Grub press Esc. At the Grub menu select (recovery mode). At the next menu you could try Xfix.

---

