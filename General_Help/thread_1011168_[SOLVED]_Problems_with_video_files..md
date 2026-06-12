---
title: "[SOLVED] Problems with video files."
date: 2008-12-14
forum: General Help
---

### Post by azmo35 on 2008-12-14
Hello people,I have this problem whenever I download or edit (convert) a Avi file my laptop freezes even the keyboard and the solution is hard reboot,has anybody any suggestions,many thanks AZMO.

---

### Post by spiderbatdad on 2008-12-14
not much information in your post. What version of ubuntu are you running? What program are you using to convert your avi files? How much ram does your system have?

---

### Post by azmo35 on 2008-12-14
Sorry,ram 512mb,Ubuntu 8.04 and for convert DeVeDe but it fail "freezes at first Utilization but this happen after i download a video file and i want to see on Movie Player,thanks for your reply AZMO.

---

### Post by spiderbatdad on 2008-12-14
have you considered ffmpeg for conversion? See here post #5 [http://ubuntuforums.org/archive/index.php/t-512417.html](http://ubuntuforums.org/archive/index.php/t-512417.html)

and here: [http://forums.gentoo.org/viewtopic.php?t=117709](http://forums.gentoo.org/viewtopic.php?t=117709)

---

### Post by azmo35 on 2008-12-15
> **spiderbatdad said:**
> have you considered ffmpeg for conversion? See here post #5 [http://ubuntuforums.org/archive/index.php/t-512417.html](http://ubuntuforums.org/archive/index.php/t-512417.html)

and here: [http://forums.gentoo.org/viewtopic.php?t=117709](http://forums.gentoo.org/viewtopic.php?t=117709)

	
I think I do not understand me,the problem I have is when i finish download a movie file and i want to see this file on MOVIE PLAYER all my laptop freezes even the keyboard so the solution is hard reboot I mentioned DeVeDe only because this is the last time it happened,thanks for any help,AZMO.

---

### Post by spiderbatdad on 2008-12-15
Sorry for the misunderstanding. After you mentioned DeVeDe, I thought you were trying to convert avi to dvd format.
What movie player are you using to watch these movies, gstreamer?

---

### Post by ajcham on 2008-12-15
Try running the memtest86 from an Ubuntu live CD.  I had the problem of complete system freezes a few weeks ago and was informed that running a memtest should be the first check to perform.  Indeed, I did have a bad module, and removing it has fixed that.

---

### Post by azmo35 on 2008-12-16
Thanks for the reply but memory is ok,I tried all sorts of players and this happen with all if i tray play movies files after download,any help would be appreciated,AZMO.

---

### Post by azmo35 on 2008-12-24
Hi again, but is here someone who can give help to my problem or any suggestion thanks,AZMO.

---

### Post by Tomatz on 2008-12-24
> **azmo35 said:**
> Hello people,I have this problem whenever I download or edit (convert) a Avi file my laptop freezes even the keyboard and the solution is hard reboot,has anybody any suggestions,many thanks AZMO.

Converting video really puts your cpu under alot of stress. Your cpu is probably overheating and the COP protection on the mainboard is disabling the processor to stop permament damage.

;)

---

### Post by azmo35 on 2008-12-24
Thanks for the reply but the problem is not about the converting but if i want see the movie files i finish downloading everything freezes so the solution is hard reboot.

---

### Post by Tomatz on 2008-12-24
Firstly, you never have to hard restart linux. First try ***ctrl alt bkspace***. If that doesn't work see the following link:

[http://ubuntuforums.org/showthread.php?t=617349](http://ubuntuforums.org/showthread.php?t=617349)

**Hard restarting is damaging to the ext3 filesystem** ;)


Secondly, can you run me through **exactly** how the freezing occurs. E.g how you open the video file.

---

### Post by azmo35 on 2008-12-24
Thanks again i try at few minutes ago play movei file that finish of downloading and bingo my keyboard freezes so ctrl alt bkspace doesn't work again solution hard reboot.
Players movie player & vcl media but i removed it.

---

### Post by Tomatz on 2008-12-24
> **azmo35 said:**
> Thanks again i try at few minutes ago play movei file that finish of downloading and bingo my keyboard freezes so ctrl alt bkspace doesn't work again solution hard reboot.
Players movie player & vcl media but i removed it.

Open a terminal and run this command:

```
totem

```

Then open the video in totem (keeping the terminal window in view). When the computer crashes write down what is displayed in the terminal window and post it here ;)

---

### Post by azmo35 on 2008-12-24
Hi but i'm being trying the commands of the link but without any success like i saied no keybord i trayed play the movei file twice but nothing i follow your advice on terminal and we played the movei ok,any suggestions thanks.

---

### Post by Tomatz on 2008-12-24
> **azmo35 said:**
> Hi but i'm being trying the commands of the link but without any success like i saied no keybord i trayed play the movei file twice but nothing i follow your advice on terminal and we played the movei ok,any suggestions thanks.

So if i am hearing correctly, the problem only occurs when you open the video by double clicking on the .avi after it has downloaded?

---

### Post by azmo35 on 2008-12-24
Hi,you are almost correct normaly i opem first totem and add the avi file but if i double click it is the same problem,i being looking on threads about karnels freezes and loking on karnel log but apparently nothing wrong,thanks again for you reply.

---

### Post by Tomatz on 2008-12-24
> **azmo35 said:**
> Hi,you are almost correct normaly i opem first totem and add the avi file but if i double click it is the same problem,i being looking on threads about karnels freezes and loking on karnel log but apparently nothing wrong,thanks again for you reply.

I assume you are running compiz?

If so run the following command in a terminal ([COLOR="Red"]leave the terminal open after[/COLOR]) to disable compiz until the next boot\session:
```

metacity --replace

```
If the problem seems to have gone, post back and we can try to fix the issue ;)

---

### Post by azmo35 on 2008-12-24
Yes,you are correct i'm running compiz but my problem sortoff are solve i can play my 190gb off avi files without any problem only when i finish of downloading one of them the laptop freezes all my open windows and keybord so i can run the command but i think at this moment not will make any difference stop compiz,sure i will writting down the command and try,thanks for the reply.

---

### Post by Tomatz on 2008-12-24
> **azmo35 said:**
> Yes,you are correct i'm running compiz but my problem sortoff are solve i can play my 190gb off avi files without any problem only when i finish of downloading one of them the laptop freezes all my open windows and keybord so i can run the command but i think at this moment not will make any difference stop compiz,sure i will writting down the command and try,thanks for the reply.

Are you using bittorrent to download them (i assume they are all legit downloads as its against forum rules to talk about piracy)? If so, what client do you use?

---

### Post by azmo35 on 2008-12-25
Hi again but i use a little software called Utorrent through wine and no problems with that,about torrents and piracy this is not my thread,my thread is about everything on my laptop that freezes after i download one movie file and if i check is content them my problem begins all windows stop no keyboard and no mouse only power key works "HARD BOOT" thanks again for your reply.
Ps:After the hard boot if i play the same movie no problems.

---

### Post by Tomatz on 2008-12-25
> **azmo35 said:**
> Hi again but i use a little software called Utorrent through wine and no problems with that,about torrents and piracy this is not my thread,my thread is about everything on my laptop that freezes after i download one movie file and if i check is content them my problem begins all windows stop no keyboard and no mouse only power key works "HARD BOOT" thanks again for your reply.
Ps:After the hard boot if i play the same movie no problems.

Try using **azureus **;)

Install it via synaptic. Its probably a problem with utorrent and wine. My guess, its the utorrent data verification stage causing problems ;)

P.s

Merry crimbo fellow Cambridgeshireian lol. Im just down the road in cambridge ;)

---

### Post by azmo35 on 2008-12-25
Hi maybe that is the problem but **azureus** for me is not good **utorrent** is far beter for me.i will try your suggestions and see what will happen for now thanks for the reply.

---

### Post by azmo35 on 2008-12-26
Well i'm back again about **wine/utorrent** that is not the problem i made a direct donwload through firefox and boom everything again freezes so now only maybe is the compiz the problematic i will try again and see the result.

---

### Post by azmo35 on 2009-01-01
Thanks to **Tomatz** that point me to the right problem and now i need a solution. The problem as caused by compiz, i used the code **metacity --replace** to desable compiz that **Tomatz** give me and my movie files worked fine without any freez so now the quistion is what i need change in compiz to correct my problem,any sugestions are appreciate,thanks AZMO.

---

### Post by jocheem67 on 2009-01-01
If you're into watching avi's, you could disable all fancy stuff by navigating to preferences ---- appearance ---- visual effects and disable compiz there. This will give you the plain old normal desktop with no effects. 
Is usually better for stability regarding video's...

I recommend these players:

smplayer ( has the mplayer as backend, most powerful )
vlc ( very versatile )
totem-xine ( slightly netter imho than totem-gsteamer )

Furthermore you should enable the medibuntu reps. for the win32 codecs and libdvdcss2 ( if you're not on ubuntu64 that is )

Did you install "ubuntu-restricted-extra's" ??

---

### Post by Tomatz on 2009-01-01
> **azmo35 said:**
> Thanks to **Tomatz** that point me to the right problem and now i need a solution. The problem as caused by compiz, i used the code **metacity --replace** to desable compiz that **Tomatz** give me and my movie files worked fine without any freez so now the quistion is what i need change in compiz to correct my problem,any sugestions are appreciate,thanks AZMO.

The following should work. You need to switch to X11 video output. Videos will be slightly pixallated but the freezing problem shouldn't occur again.
[B]
To do this for the 3 main media players[/B] (only do what is appropriate)**:**

> GSTREAMER:
For Totem with the gstreamer backend (totem-gstreamer) open a terminal and type gstreamer-properties
Then click the Video tab and under Default Output select X Window System (No Xv) for the plugin. Then restart Totem. This will work for any video application that uses gstreamer as it's video backend.

MPLAYER:
If you use MPlayer (GMplayer) right-click on the screen and select Preferences then select the Video tab and under Available Drivers select X11 (XImage/Shm)
then restart MPlayer. The issue here is that it won't go fullscreen with the video. I suggest using VLC or totem-gstreamer.

XINE:
If you use Xine then go to File -> Configure -> Preferences.
(make sure under experience_level you select Master Of The Known Universe)
You will get a tab at the top for Video. Under driver select xshm. Then restart Xine. This also works if you are using the totem-xine backend. Just run gxine at the terminal and follow the steps.

VLC:
For VLC select Settings -> Preferences then in the bottom-right of the window check the Advanced Options box. Then expand the Video item on the left and select Output modules. Then in the list on the right for Video output module change it to X11 video output. Then restart VLC

---

### Post by azmo35 on 2009-01-05
Thanks **Tomatz** your introctions solve my problem.

---

### Post by RealG187 on 2009-01-06
For my thread:

I said VLC and Rhythm box worked for audio, but not totem. But my theory is that totem uses visualizations, which are videos in a way, so the visualizations caused it.

I upgraded to 8.10 and it appears to work just fine. Totem works with visualizations. I have not tried Rhythmbox or VLC (VLC is installing now as we speak)

EDIT: Rhythmbox works

---

