---
title: "[Lubuntu] Kega Fusion"
date: 2014-05-02
forum: Emulators
---

### Post by SoulStreamBurst on 2014-05-02
Hi! New to the Linux and Ubuntu world user here! 

I was just wondering how to setup Fusion to get it up and running on my laptop, I'm using Lubuntu 14.04 64-bit on a Dell Studio 1558 with built-in Intel HD Graphics.

I tried searching other threads similar to my question, but the methods stated didn't work for me, so I hope someone would fill me in...

Thanks!

---

### Post by adec2 on 2014-05-02
Hi,

Firstly you need to get hold of the various bios files which i cant give you due to copyright for the sega cd/32x(Google is your friend) Then put them in your Fusion Directory where the Fusion executable file is.
If you just want to run Megadrive/Genesis stuff I dont think you will need a bios file.
Normally you run fusion and select all your bios files under the menu>options>set config
Or select all your preferred options which will save a config.ini (After first run of Fusion and exiting) file in your home folder under .Kega Fusion (You may have to press CTRL+H to unhide this folder)
The Fusion executable you should have downloaded from the Fusion website and it should be around 697kb in size, this is your executable to double click to run.
It *should* run Megadrive/Genesis roms without bios but when you want to run 32x Genesis/Megadrive roms they require their own special bios (Again Google is your friend here) Same with SegaCD/MegaCD images.
Then just Press File>Run whatever system you need and browse to the rom/image of your game

Hope this helps a little!

---

### Post by SoulStreamBurst on 2014-05-02
Hey there! Thanks for the reply, I already tried downloading Fusion from the website, extracted it then I did try double-clicking the executable, unfortunately nothing comes up. What am I doing wrong? :(

---

### Post by adec2 on 2014-05-03
is the file marked as executable?
Right click it and select properties, there should be an option to mark it as executable
Either that or open a terminal in the folder you have the Fusion binary and type "./Fusion" without the quotes and paste what the output is in the terminal (make sure you type fusion exactly as it is spelt, capital letters and all if it has them) If you binary is called "fusion" type "./fusion" or if its called Fusion, with a capital make sure you type "./Fusion"

---

### Post by SoulStreamBurst on 2014-05-04
Yup, I can confirm that it is an executable. I tried running it with the terminal, I have to locate the directory where Fusion is kept before typing the command "./Fusion" yes? Nothing comes up after that. 

When I tried right-clicking and "run the executable in the terminal" nothing comes up either.

---

### Post by adec2 on 2014-05-04
You are correct in that you have locate the folder with the Fusion exe in it before typing. After typing ./Fusion what is written in the terminal window even if it does not run?
 Anything about missing dependencies?

---

### Post by SoulStreamBurst on 2014-05-05
Nothing it's just blank, nothing about missing dependencies either.

---

### Post by adec2 on 2014-05-05
Try folowing this site..if it works for you i will write it here for completeness sake and for anyone else that needs the help

[http://digitalstudio7.blogspot.co.uk/2014/03/kega-fusion-ubuntu-no-sound-fix.html](http://digitalstudio7.blogspot.co.uk/2014/03/kega-fusion-ubuntu-no-sound-fix.html)

Try to re download it from [http://segaretro.org/Kega_Fusion#Downloads](http://segaretro.org/Kega_Fusion#Downloads)

I have attached my Fusion.ini to this post and it needs to be extracted as is into your home folder (with the dot in front too as it is a hidden folder)

Worth a try it may be simply because there is no .ini file, :)

---

### Post by SoulStreamBurst on 2014-05-05
Holy!

I tried re-downloading Kega from that website, somehow I tried double-clicking the executable, it... worked... just like that... :shock: 

I'm having no trouble with sound or anything... it just works now! Woah, hey thanks for the links, I think this already solves my problem. :)

---

### Post by adec2 on 2014-05-05
You're quite welcome SoulStreamBurst :)
I love emulators myself and believe me some have had me scratching my head too. Dont forget the other systems it emulates (32x, SegaCD etc) may need extra bios files!
Enjoy!

---

