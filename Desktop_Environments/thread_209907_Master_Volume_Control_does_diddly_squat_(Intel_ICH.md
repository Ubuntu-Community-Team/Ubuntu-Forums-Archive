---
title: "Master Volume Control does diddly squat (Intel ICH6 Audio/Sigmatel)"
date: 2006-07-05
forum: Desktop Environments
---

### Post by Vchat20 on 2006-07-05
Just as the title states. No matter what attempt I make, the master volume control through both the Alsa Mixer and the OSS Mixer do nothing to control the volume on here. I can have an mp3 going in xmms and can slide the master volume slider up and down, mute it, etc. no change in volume. yet the PCM slider and the volume slider on xmms work.

Any ideas? I'm fairly fresh to the *nix world, but I am familiar with using the command line from plenty of experience with dos and so far ive gotten my way around ubuntu so far fairly well. Ive even managed to get my broadcom wireless card working with help from another thread on here detailing how to get ndiswrapper working.

---

### Post by evilghost on 2006-07-05
Try using alsamixer from cmdline and increase the PCM volume.

---

### Post by Vchat20 on 2006-07-05
Yeah. Adjusting the PCM volume works fine. But my problem is on my laptop ive got volume 'hotkeys' that I always prefer to use instead of manually messing with the mixer and this controls the master volume slider which SHOULD control all outgoing volume hence the name 'Master'. But it doesnt. That's the problem im trying to get sorted.

---

### Post by evilghost on 2006-07-05
Odd, what laptop?  Mine has worked fine out of the box with master volume control?

As FYI:
```

luser@zd7000:~$ lspci|grep -i audio
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
luser@zd7000:~$

```

---

### Post by Vchat20 on 2006-07-05
Im running in windows right now (dualboot xpprosp2/ubuntu with default grub bootloader) so I cant do any diagnostics that may be asked for. But here is my 'known' configuration:

Dell Inspiron 1200
1.4ghz Celeron M (1MB L2 Cache)
768MB RAM
40GB Samsung 5200rpm drive (rough partition sizes: 35GB NTFS, 5GB ext3, hda1/hda2 respectively)
Intel 9xx express chipset
Intel 915GM onboard graphics
Sigmatel C-Major Audio (Intel ICH6 based, AC97, etc.)

Almost all the drivers were default ubuntu drivers. The only one im still trying to wrap my head around is getting my broadcom bcm43xx based minipci wifi card working. Else all seems to be working great minus this minor sound problem. Oh. and my conexant modem doesnt seem to be recognized either albeit I rarely use it anyhow so thats moot for me. I can boot to windows when I do need it.

---

### Post by Vchat20 on 2006-07-06
Ok. did the command you listed above. this is what ive got:

```
vchat20@mobile:~$ lspci|grep -i audio
0000:00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
vchat20@mobile:~$
```

---

### Post by Jucato on 2006-07-06
I had an almost similar problem, where Master doesn't do anything and PCM controls everything (only difference is that I don't have a multimedia keyboard). Here's what I did: right-click on the volume control applet and choose Preferences. You will see a list which has Master, PCM, Center, etc. Master will be highlighted, so click on PCM to highlight this instead. then click close. From now on, anything that uses/changes GNOME's volume control will affect PCM as default. 

Hope that helps.

---

### Post by Vchat20 on 2006-07-06
Well, I just popped back on ubuntu this morning and the problem seems to have cleared itself up. Ive tried numerous multimedia apps from xmms to movie player to rythmbox. all the same. the PCM slider on the mixer is up all the way and the master volume does what it was supposed to do in the first place. And that now means my volume hotkeys on my laptop work too.

cheers for the help guys. :)

EDIT: Was just playing around with things a bit more and I think I may have found my original problem. While a lovely feature I wish I could get on windows, I can see it becoming a pain sometimes. And that is that the volume coming from the internal speakers on my laptop and the headphone port are completely separate. There is the Master volume slider (which appears to control the internal speakers) and a headphone slider (which controls the headphone port). And when I was trying to figure out this problem last night, I was using headphones. So that may help explain it.

---

### Post by H.E. Pennypacker on 2006-07-07
I am having this exact problem, and the problem never "clears itself."  I wish I'd be able to find a solution.  Master Control only works when headphones aren't plugged in.  Changing to PCM in the preferences dialog doesn't enable it to work with my FN keys.  I wish I could control PCM (or PCM-2) with my keyboard FN keys.
 
Dell Inspiron 2200.

---

### Post by eternalsword on 2006-07-10
I have a Sigmatel with my dell, and what I had to do was right click on the Speaker icon, go to Preferences and select the Sigmatel device (OSS Mixer).  Then the volume control worked for me.

---

### Post by stoffe on 2006-07-24
I had the same problem, and opening properties and switching from Master to PCM worked for the volume control in the tray. Still nothing happens when I press the hotkeys on my keyboard (A Logitech Media something). The floating popup appears, and the bar moves, but no change to the actual volume (on any setting). Is there someplace else I can change this one?

---

### Post by Jazzbunny on 2006-07-30
I have same problem. Tray volume control was defaulted to headphones and switching that to Internal Speaker (laptop) allowed me to control sound volume from tray icon.
However, keyboard hotkeys are still (apparently) linked with headphones so they wont do much more than bring a popup to my screen. I'd be nice if this could be changed somehow...

---

### Post by joypunk on 2006-07-30
Same problems here. Dell Inspiron 9100 laptop. The volume control keys are only affecting the "Master" volume. I can control the volume from Terminal by using the PCM controls in alsamixer.

Right clicking on my volume icon and selecting PCM will still only change the "Master" volume.

---

### Post by H.E. Pennypacker on 2006-09-11
double-post.

---

### Post by H.E. Pennypacker on 2006-09-11
Do we know of a solution months after this thread has been posted?  The problem "clearing itself up" is not a solution.

---

### Post by ampop on 2006-09-13
> **Jazzbunny said:**
> I have same problem. Tray volume control was defaulted to headphones and switching that to Internal Speaker (laptop) allowed me to control sound volume from tray icon.
However, keyboard hotkeys are still (apparently) linked with headphones so they wont do much more than bring a popup to my screen. I'd be nice if this could be changed somehow...

Yes that's it, and preferences (right-click on sound icon) must be OSS Mixer.
What about Hotkeys? Any solution? Thank you.

---

### Post by ampop on 2006-09-14
Any help in this issue? Thank you.

---

### Post by pocketman on 2007-12-29
Hello all,

This is my first post as a new Ubuntu user.  I solved the keyboard volume control keys for myself, and since I've gotten help here, figured I better register and share this solution for other owners of Dell Inspirons (maybe others with the same sound card as well).  Simply go to System > Sound and under Default Mixer tracks CTRL click on both Master and PCM.  Did the trick for me.  Hope it helps you too. I am currently running Gutsy, so I can't tell you if this will work in other releases.

Good luck,


Ben

---

### Post by ksmiff on 2007-12-29
here is my problem...hda intel..no sound from internal speakers but ok through headphones...alsamixer shows NO MASTER...why is that? how do i fix that? shouldn't there BE a master? and if the answer is yes..how do i get one.

---

### Post by pocketman on 2007-12-30
Have you tried double clicking on the volume icon in the tray, then clicking on Edit > Preferences?  There are a host of checkboxes there that allow you to select what is available on the mixer.

---

### Post by MarimaX on 2008-01-11
Ok...running Gutsy on I9300....subwoofer stays on through master volume ctrl....face buttons will raise/lower volume on the PC Speakers (your tweeters) and subwoofer....have tried the various settings with ctrl/click etc...not working...the best I can do is leave it where it is and ctrl vol via the face buttons.  any ideas i'd appreciate.

---

### Post by project4 on 2008-01-12
this helped! thanks!

> **Jucato said:**
> I had an almost similar problem, where Master doesn't do anything and PCM controls everything (only difference is that I don't have a multimedia keyboard). Here's what I did: right-click on the volume control applet and choose Preferences. You will see a list which has Master, PCM, Center, etc. Master will be highlighted, so click on PCM to highlight this instead. then click close. From now on, anything that uses/changes GNOME's volume control will affect PCM as default. 

Hope that helps.

---

### Post by InspirationDate on 2008-01-15
I was having the same problem.  I could double select Master and PCM in the Volume Control applet preferences and the Volume Control applet would work, but my keyboard shortcuts still weren't working.

I fixed it by going into System > Preferences > Sound and then double selecting Master and PCM there (hold CTRL while selecting).  This changes the default mixer, doing it in the applet just changes the applet mixer.  Keyboard shortcuts are attached to the default mixer.

---

### Post by aaronkarp on 2008-02-29
I've read through all the posts here, but my copy of Gutsy isn't showing the same settings that you guys are seeing.

I right click on the volume tray icon, click preferences, and see the following options:

[ CA0106 (Alsa mixer) ]
Line in, Microphone, Phone, IEC958 Center/LFE, IEC958 Front, IEC958 Read, IEC958 Unknown, Aux, Analog Center/LFE, Analog Front, Analog Rear, Analog Slide, CAPTURE feedback

[ mixer00 (OSS Mixer) ]
Microphone, Line-1, Digital-1, Phone-in, Phone-out

I don't see anything about Master or PCM.

Here's what I get for my audio controller:
aaron@aaron-desktop:~$ lspci|grep -i audio
04:01.0 Multimedia audio controller: Creative Labs SB Audigy LS

Any suggestions?

Thanks!
-Aaron

---

### Post by InspirationDate on 2008-02-29
Try the System menu up beside Applications and Places.

System > Preferences > Sound

Then just follow the rest of my message.

---

### Post by phicloray on 2008-06-18
Hey folks,

Can't find a way as yet to implement this on KDE with KMix - am looking as we speak and will post a solution if I find one!

---

### Post by Kamikaze117 on 2008-07-18
> **pocketman said:**
> Hello all,

This is my first post as a new Ubuntu user.  I solved the keyboard volume control keys for myself, and since I've gotten help here, figured I better register and share this solution for other owners of Dell Inspirons (maybe others with the same sound card as well).  Simply go to System > Sound and under Default Mixer tracks CTRL click on both Master and PCM.  Did the trick for me.  Hope it helps you too. I am currently running Gutsy, so I can't tell you if this will work in other releases.

Good luck,


Ben

Thanks! It works Great.

---

