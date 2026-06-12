---
title: "How to install/start DOOM3 demo?"
date: 2005-04-29
forum: Gaming &amp; Leisure
---

### Post by Turin Turambar on 2005-04-29
I can't install this game.
I tried to run doom3-linux-1.1.1282-demo.x86.run and got this message:

bash: ./doom3-linux-1.1.1282-demo.x86.run: /bin/sh: bad interpreter: Permission denied

With "sudo" prefix:

sudo: unable to execute ./doom3-linux-1.1.1282-demo.x86.run: Permission denied

---

### Post by bored2k on 2005-04-29
[QUOTE=Turin Turambar]I can't install this game.
I tried to run doom3-linux-1.1.1282-demo.x86.run and got this message:

bash: ./doom3-linux-1.1.1282-demo.x86.run: /bin/sh: bad interpreter: Permission denied

With "sudo" prefix:

sudo: unable to execute ./doom3-linux-1.1.1282-demo.x86.run: Permission denied[/QUOTE]
 Try 
chmod 755 doom3-linux-1.1.1282-demo.x86.run && sh doom3-linux-1.1.1282-demo.x86.run
  or
chmod 755 doom3-linux-1.1.1282-demo.x86.run && ./doom3-linux-1.1.1282-demo.x86.run

---

### Post by wbeck85 on 2005-04-29
Oh, shoot, I completely missed the word "demo" in your post, so I went on and on about how to install the game.... Sorry about that. Here's the thing anyway....

I just installed Doom3 yesterday, in fact. I downloaded the .run file. moved it to my /usr/local/games/doom3
folder (which I made), then manually copied the .pk4 files from the 3 CDs to the /doom/base directory
(which I also created) then I ran the .run file and that ran the setup. This worked well, however, after running
the game as a user (by typing in doom3 in to a console, or i suppose you could add it to your menu), you will
realize that you cannot save anything. I dont know if this happens to everyone, but I had to change the
permissions on the ~/.doom3 folder and all it's contents to allow myself to read and write to the directory.
Here's what I did:
     Open a console window:```
# sudo mkdir /usr/local/games/doom3
# sudo mkdir /usr/local/games/doom3/base
# sudo mv ~/Desktop/doom3-linux-1.1.1286.x86.run /usr/local/games/doom3/doom3-linux.run
```Now, to copy the .pk4 files from the CDs:```
# sudo nautilus
```(here, i just navigated to the /doom3/base directory, opened up another window in nautilus and dragged&dropped the .pk4 files from CD to /base directory, i suppose it could be done with # sudo cp ... but I like to see the nautilus status bar when moving big files)
     Once the files are copied:```
# sudo sh /usr/local/games/doom3/doom3-linux.run
```
     This brought me to the installer thing, in which I just used all the default options. Once that's over, try the game:```
# doom3
```
     You will probably initialize the game and then get booted out. I think. if that happens, or you can't save anything, you may need to change the permissions of your ~/.doom3 directory, and I also changed the permissions of my /usr/local/games/doom3 directory just for kicks:```
# sudo chmod -R 777 ~/.doom3
# sudo chmod -R 777 /usr/local/games/doom3
```
     Now, make sure that in your xorg.conf you have resolutions set that will enable decent play in Doom3. to do that:```
# sudo gedit /etc/X11/xorg.conf
```     Now scroll down to 'Section "Screen"' make sure there is a subsection that looks something like this ```
Subsection "Display"
        Depth       24
        Modes       "1680x1050" "1280x800" "1024x768" "800x600" "640x480"
        ViewPort    0 0  # initial origin if mode is smaller than desktop
    EndSubsection
``` but make sure that the resolutions listed are suitable for your monitor. If not already present, enter your desired resolution for Doom3. Save it and close gedidit. Alrighty, try out doom3 again by typing "# doom3 " in the console window. Hopefully it works for you.

I found that my audio was really screwed up. I do not know if that is from following the asound.conf alsa mixer howto or if it's something else, as I did not install Doom3 until after that. Does anyone else have really garbled audio in doom3?

Hope this helps. I didnt want to sound condencending to you, as i do not know your linux abilities, but i figured that some noobs may want to try out doom3 as well, and this is mostly for them :)

Good luck.

---

### Post by Turin Turambar on 2005-04-29
:) Hey Wbeck, you are very kind! :) Thanks!
That happened to me few times as well - I wrote the whole step-by-step guide and when I finished, I noticed that he/she wanted to know the first step only.  :grin: 

Anyway, I got it working, but I had to transfer the whole file from a DVD to HDD... and then I started it without any problems or permission changes.
I just wanted to see how my OpenGL drivers work. They are functioning good, but I deleted the game as soon as I could. I don't want to have nightmares. ;)

---

### Post by wbeck85 on 2005-04-30
[QUOTE=Turin Turambar]:) Hey Wbeck, you are very kind! :) Thanks!
That happened to me few times as well - I wrote the whole step-by-step guide and when I finished, I noticed that he/she wanted to know the first step only.  :grin: 

Anyway, I got it working, but I had to transfer the whole file from a DVD to HDD... and then I started it without any problems or permission changes.
I just wanted to see how my OpenGL drivers work. They are functioning good, but I deleted the game as soon as I could. I don't want to have nightmares. ;)[/QUOTE]
 LOL, that makes sense. I assume that the file was probably trying to write to the DVD. no wonder you didnt have permission!

Yeah, that game is creapy. After many months of dabbling in the first few levels of the game, I finally buckled down, turned the gamma up and plowed my way through the levels, ignoring as much as i could. Less scary that way. Expansion pack just recently came out. Don't think ill get it. I'm not one for horror. I usually am the one sitting my girlfriend's lap by the end of a horror flick.... But anyway....

I found that with the latest fglrx driver (8.12.10) my Mobile Radeon 9700 is so-so in linux. I probably get about 30 or so fps with high settings at 800x600. Could be worse. But could be alot better. It is alot better in Windows, sadly. However, I did find that levels seemed to load about twice as quicky inlinux as they did in Windows, and the game exits very quickly and cleanly, was well as starts quickly. In windows, it would take forever to start, and once it closed, Windows would run sort of bogged down for a while. Very annoying. But my audio problem! that is a bother. Since I installed it, the audio is garbled. I can make out what people say, but it is as though they are speaking through a very weird synthesizer or something. Weird. And annoying. But nice to know that you got the program working. :)

---

### Post by Turin Turambar on 2005-04-30
I have a Radeon 9000 PRO and it runs pretty ok in 640x480 resolution. I didn't even dare to try 800 or 1024... I knew my card couldn't handle that. :)
Linux ATI drivers are still new, I guess as the time goes by, they will get better and better. Please correct me if I'm wrong, but I think that mobile versions are newest addition to fglrx drivers? If so, that explains a little why you had some glitches.

As far as DOOM3 goes, I'll stick to Super Tux. ;)

---

### Post by copilot on 2005-05-02
I got it working thanks to your guide. My sound is also garbled, If I figure it out I'll be sure to post.

---

### Post by DanVarga on 2005-05-06
I am having similar problems with Doom3 except that mine launches the game and then stops with a black screen.  I have to restart X to get out of it.  Anyone have any ideas what could be causing this problem?

Edit:  Nevermind got it to work.

---

### Post by DutchLau on 2005-05-06
Where can I download the Doom 3 demo for Linux? I'm browsing the website and the mirrors but I can only find demos for windoze. Someone please post a link for linux! Thanks :razz:

EDIT: I found a website that has the Linux demo. 3D Gamers.com

---

