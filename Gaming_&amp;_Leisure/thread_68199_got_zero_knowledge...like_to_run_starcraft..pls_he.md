---
title: "got zero knowledge...like to run starcraft..pls help"
date: 2005-09-22
forum: Gaming &amp; Leisure
---

### Post by kismelts on 2005-09-22
sorry guys i really need to post...i got zero knowledge with linux...i got no experience either...but i really need to learn it...no matter how much i read still cant relate...
ive installed ubuntu 5.04 and cedega...problem is hw to run games frm windows...pls help me...

i like to start with starcraft....

(been using xp pro for almost a year...and a week ago im forced to use linux)

---

### Post by jyank on 2005-09-22
Do you have your windows partition mounted? and is starcraft installed there?

If the answer above is yes to both, then simply open a terminal and load nautilus with sudo, browse to the folder where where starcraft is installed (for example, mine would be /mnt/win/Program Files/Blizzard) then just open a normal nautilus and drag it onto your ubuntu partition into the TransGaming Drive that cedega made for you.

Then run the game by typing in a terminal- cedega /pathtostarcraft/starcraft.exe

and it should boot up

---

### Post by Mishura on 2005-09-22
_**HOWTO:  Starcraft on GNU/Linux**_

Disclaimer:  I haven't played starcraft in a year.  I'm pulling this from memory.  Should work, nonetheless.  I won't cover Brood War, cuz I don't have it.

Materials you'll need:

1.  StarCraft CD (Brood War optional)
2.  Wine or Cedega
3.  3D accelerated video card drivers (nvidia-glx or fglx..)
4.  Um.. 650 MB disk space?  Probably less if you play off CD.

Right!  Lets get this thing going!

1.  Place Starcraft CD into your CD/DVD Rom.  We will assume its path is /media/cdrom.
2.  Open up a terminal.  (Konsole on KDE)
3.  Type the following... (everything AFTER $)

```
$ mount /media/cdrom
$ cd /media/cdrom
$ ls
```

Now, find your setup program.  Should be either Setup.exe or Install.exe, I can't remember.  I'll assume it's "setup.exe".

```
$ cedega ./setup.exe
```

OK.  Follow the installation just as you would in Windows.  Be smart on where you put it since Cedega/Wine translate DOS Drives (C:, D:...) to Unix paths.  C:\ = ~/.transgaming/c_drive and stuff.  

If you are unsure, load "~/.transgaming/config" inside a text editor and take a look.

Lets assume that you placed Starcraft in your "fake_windows" directory.  After install...

```
$ cd ~/.transgaming/c_drive/Starcraft
$ cedega ./sc.exe (or StarCraft.exe)
```

Should be it.  Brood War install should be the same.  If you are running plain wine, you'll may need a no-cd crack.  Find them on the internet.  I won't link, as I think thats not "kosher" here.

Also, be sure to get the latest patch from blizzard.com.  To run the patch, its easy.

```
$ cd /path/to/starcraft_patch
$ cedega ./starcraft_patch.exe

```

Remember:

1.  Unless you patch Starcraft with a No-CD crack, you will need to mount the Starcraft CD everytime you play.
2.  Theorietically, you can play on Battle.net if you use Cedega.  I doubt it with Wine.
3.  These same instructions are practically the same to install other Blizzard games like Warcraft 3 and Diablo II.
4.  If you got Point2Play,  You can try using that to install it.  It will be easier, I think.

---

### Post by kismelts on 2005-09-22
thnx for ur speedy replies....

inyank....
i got starcraft installed frm other pc in my local newtwork...so i did copy the file to my pc where i installed ubuntu...then i lauched the .exe using cedega (cedega /pathstarcraft/starcraft.exe)....it didnt work....i did try installing gunbound with its new client and patch using cedega...but when i launched gunbound.exe via cedega, no effect..i did this on gui mode...


Mishura....
thnx for ur detailed response..i wasnt able to indicate tht starcraft is already installed on a network pc....but ur guide will be a great help for me installing fresh programs frm cd...thnx so much ur...ur fast and energetic!


now i cant figure out the problem....hoping for ur unending help....thnx

i dont have point 2 play yet..

---

### Post by Mishura on 2005-09-23
Oh, its already installed?

OK.  Lets try this:

Can you access anything from your Windows drive?  Can you see it in Natilus or Konqueror?

If not do this:

```
$ cat /etc/fstab
```

Paste that here.  This is to see if your Windows drive is already in Fstab, or your mounting configuration.

If you see something like /windows then do this:

```
$ mount /windows
```

To play a game on your Windows drive, just do:

```
$ cd /windows/path/to/starcraft/
$ cedega ./starcraft.exe
```

To make it easier, create a desktop shortcut or menu item for it, so you don't have to open up a console every time you play.  :)

---

### Post by anil_robo on 2005-10-21
Hi there! Another newbie! I switched over to Ubuntu few days back, but I still have to keep Windows because of Diablo2:LOD.

I have installed WINE and try to run Diablo2 from there, but it doesn't work, even when logged in as a root, even after putting diablo2 expansion CDROM in drive.

Can I use WINE to play diablo2? Really?

Went to Cedega website... they talk of something CVS... and I can't make a word out of that page! I really need to get rid of windows now! Please help! Help me run Diablo2 and I'll erase Windows (and a loyal customer of Bill Gates) forever!

Thanks

---

### Post by anil_robo on 2005-11-25
Anyone? I want to run Diablo 2 on Ubuntu so that I can get rid of windoze. I have the original game CD which Wine fails to recognize :(

---

