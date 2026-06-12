---
title: "Doom3"
date: 2010-07-02
forum: Gaming &amp; Leisure
---

### Post by Zirts on 2010-07-02
Hi,

I just recently installed doom3 and I'm having a ATI Radeon 9550 i think 128MB graphic card wich is using the not restricted Ubuntu drivers.

Now, the game is slow :D  It is running on about 50FPS when I'm in a place where there are no windows nearby, but once I see thoes little sub-rooms with windows and ppl moving inside of them, i get 3 FPS wich is making the most part of the game unplayable...

Also when I run the game through terminal, the game is giving some errors that my video card is 64MB  while it's actually 128MB, I changed it so that on each startup it sets it to 128 manually, but it still didn't help much.
And there are also thoes errors about some files, that the game cant open or create them, for instance a file named doomkey.
My doom is installed into the /usr/local/games/doom3 folder and the usr folder is not accessable to other users than root so, if i run doom3, the game cant create new files into there and so on...

So is the slow performance becouse of the place where the game is installed or becouse of something else, and can I fix it somehow?


Regards,
Zirts

---

### Post by rizzeh on 2010-07-02
config files for Doom3 will be in your ~/.doom3 folder. It is a hidden folder so click show hidden files. Best bet is to read up on autoexec.cfg file for doom3 , works same way as quake autoexec.cfg

---

### Post by Rustybolts on 2010-07-02
Try this page for tweaking your game.
[http://www.doom3.fre3.com/tweaks/](http://www.doom3.fre3.com/tweaks/)
Tweaking my doom install I can run doom on a gma4500m integrated graphics 18-40 fps averaging around 30fps.

---

### Post by Zirts on 2010-07-02
Well, got it to about 10fps when I turned down almoust everything, but once I got my guns and thoes demons came out, it was unplayable again...  It must be something else than the video settings of the game.

Ubuntu 10.04, with all the latest stuff.
Ram 1GB
Video card Ati Radeon 9550 128MB
Amd Sempron Processor 3000+  wich was 1,8Ghz i think.

Also nothing else big is running while I'm playing Doom3.

---

### Post by hikaricore on 2010-07-02
The slow performance is due to your video card and the fact that you're (more than likely) using the open source driver..
If your card is still supported by the latest drivers you'll need to install them.
From the looks of it that card is dated at best..

---

