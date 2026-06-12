---
title: "Electric Sheep is crap."
date: 2009-06-24
forum: General Help
---

### Post by kd0afk on 2009-06-24
I got an email from Scott Draves one day asking me to tell him if the latest version of Electric Sheep was working. I installed it and it worked fine, then one day it just stopped working at all. Black screen. I posted on the forum and NEVER got a reply. I emailed Scott like he asked me to. He told me that he looked at the forum and it didn't help to email him. I asked him what would help. He said to stop bothering him.
If you are going to do something for free, fine. If you are going to do something for free that doesn't work, DON'T. If you are going to do something for free and you want feedback, don't complain when you get it.
I know that the people who put out free software are volunteers but if you want to do something, do it all the way, don't put out something that doesn't work and then complain when people ask you to help them get it working.
Free software that doesn't work coming from volunteers who don't care is CRAP any way you slice it. If you are going to be that way, don't bother producing the thing.

---

### Post by michy99 on 2009-06-24
Feel better now?

---

### Post by starcannon on 2009-06-24
My best guess is you have a corrupt sheep, as I have been using it for years with no trouble.

I would start by renaming the ~/.sheep folder:
```

mv ~/.sheep ~/.sheepBAK

```Then I would run electic sheep in a terminal, to get the .sheep folder repopulated, you'll know when its done downloading the first sheep, because a window will pop up displaying sheep.
```

electricsheep

```Finally, I would ask for help in a more, lets say, peaceful tone.

GLAHF

P.S. just ran it manually myself, and it appears that a new version is out, and will need updated by the end of the month, as the new client will receive no new sheep after the 30th. I'm gonna go ahead and compile it and try out the new version. I've never built a package before, but I know theres some good how-to's on the subject. If I can figure it out, I'll build a 32bit package and see about getting it up somewhere; caveat will be that if I get the packaging figured out, I will not be maintaining the package, and I will not guarantee its reliability; just so you know what your getting before you bother.

---

### Post by kd0afk on 2009-06-24
shawn@HAL:~$ mv ~/.sheep ~/.sheepBAK
mv: cannot stat `/home/shawn/.sheep': No such file or directory
shawn@HAL:~$

---

### Post by Chemical Imbalance on 2009-06-24
Another similar thread: [http://ubuntuforums.org/showthread.php?t=1184494](http://ubuntuforums.org/showthread.php?t=1184494)

---

### Post by kd0afk on 2009-06-24
> **michy99 said:**
> Feel better now?
Not really

---

### Post by surfed on 2009-06-24
> **kd0afk said:**
> I got an email from Scott Draves one day asking me to tell him if the latest version of Electric Sheep was working. I installed it and it worked fine, then one day it just stopped working at all. Black screen. I posted on the forum and NEVER got a reply. I emailed Scott like he asked me to. He told me that he looked at the forum and it didn't help to email him. I asked him what would help. He said to stop bothering him.
If you are going to do something for free, fine. If you are going to do something for free that doesn't work, DON'T. If you are going to do something for free and you want feedback, don't complain when you get it.
I know that the people who put out free software are volunteers but if you want to do something, do it all the way, don't put out something that doesn't work and then complain when people ask you to help them get it working.
Free software that doesn't work coming from volunteers who don't care is CRAP any way you slice it. If you are going to be that way, don't bother producing the thing.

electric sheep uses mplayer to display sheep, so your problem might be there.

---

### Post by kd0afk on 2009-06-24
> **surfed said:**
> electric sheep uses mplayer to display sheep, so your problem might be there.
I can play the avi files in mplayer just fine

---

### Post by Therion on 2009-06-24
Do Electric Sheep s--t photons?

---

### Post by kd0afk on 2009-06-24
Here is the debug return in terminal:

[B]shawn@HAL:~$ electricsheep --debug 1
=====================================
electric sheep v2.7b11
time start Wed Jun 24 17:29:31 2009
initial play counts: 16079:17 16081:33 16324:18 16418:19 16456:31 16457:30 16497:11
updating cache path=/home/shawn/.electricsheep/
begin delete cached 0
updating cache path=/home/shawn/.electricsheep/
time display loop Wed Jun 24 17:29:31 2009
idx=5 ncached_sheep=7 best_atime
found new anim id=16457.
play anim x=5 id=16457 iters=1 path=/home/shawn/.electricsheep/
bumped 16457 to 31, page=32
writing play counts
writing dirty page 32
set atime of 5 to 1245878971
playing /home/shawn/.electricsheep/00243=16457=16081=16366.avi
cleanup_and_exit 1
handle_sig_term display 0
cleanup.
writing play counts
handle_sig_term main 15
cleanup.
writing play counts
handle_sig_term download 15
cleanup.
writing play counts
handle_sig_term display 15
cleanup.
writing play counts
Terminated
shawn@HAL:~$ 
[/B]

---

### Post by starcannon on 2009-06-24
> **kd0afk said:**
> shawn@HAL:~$ mv ~/.sheep ~/.sheepBAK
mv: cannot stat `/home/shawn/.sheep': No such file or directory
shawn@HAL:~$

Can you run electric sheep from the command line and post what message it displays? The lack of a .sheep folder is why you have a black screen, there are no sheep to display.

```

electricsheep

```

---

### Post by kd0afk on 2009-06-24
> **starcannon said:**
> Can you run electric sheep from the command line and post what message it displays? The lack of a .sheep folder is why you have a black screen, there are no sheep to display.

```

electricsheep

```

shawn@HAL:~$ electricsheep
Terminated
shawn@HAL:~$

---

### Post by kd0afk on 2009-06-24
> **Therion said:**
> Do Electric Sheep s--t photons?

Wow, helpfull. And you wonder why I swear.

---

### Post by Leslie Viljoen on 2009-06-24
> **kd0afk said:**
> I got an email from Scott Draves one day asking me to tell him if the latest version of Electric Sheep was working. I installed it and it worked fine, then one day it just stopped working at all. Black screen. I posted on the forum and NEVER got a reply. I emailed Scott like he asked me to. He told me that he looked at the forum and it didn't help to email him. I asked him what would help. He said to stop bothering him.
If you are going to do something for free, fine. If you are going to do something for free that doesn't work, DON'T. If you are going to do something for free and you want feedback, don't complain when you get it.
I know that the people who put out free software are volunteers but if you want to do something, do it all the way, don't put out something that doesn't work and then complain when people ask you to help them get it working.
Free software that doesn't work coming from volunteers who don't care is CRAP any way you slice it. If you are going to be that way, don't bother producing the thing.

It's pretty hard to write a program that works on every system, for all time in the future, regardless of whether the program is free software or not. Have you tried emailing the developers of any other software that stopped working? I once ran Outlook, and it stopped working after some time - I don't think mailing the developers would help, even if I could get their email addresses.

For the record, I think Electric Sheep is great. Perhaps you should try reinstalling it.

---

### Post by Chemical Imbalance on 2009-06-24
> **kd0afk said:**
> Wow, helpfull. And you wonder why I swear.

Come on, it's funny.

---

### Post by kd0afk on 2009-06-24
> **Chemical Imbalance said:**
> Come on, it's funny.
I know but I am just not in the mood for funny right now.

---

### Post by kd0afk on 2009-06-24
> **Leslie Viljoen said:**
> It's pretty hard to write a program that works on every system, for all time in the future, regardless of whether the program is free software or not. Have you tried emailing the developers of any other software that stopped working? I once ran Outlook, and it stopped working after some time - I don't think mailing the developers would help, even if I could get their email addresses.

For the record, I think Electric Sheep is great. Perhaps you should try reinstalling it.
](*,)

Here is a clip of my original post, the one you quoted;

I got an email from Scott Draves one day asking me to tell him if the latest version of Electric Sheep was working. I installed it and it worked fine, then one day it just stopped working at all. Black screen. I posted on the forum and NEVER got a reply. I emailed Scott like he asked me to. He told me that he looked at the forum and it didn't help to email him. I asked him what would help. He said to stop bothering him.

---

### Post by starcannon on 2009-06-24
I found what appears to be the solution for some with a similar problem.

Follow this post:
[http://ubuntuforums.org/showpost.php?p=6092849&postcount=6](http://ubuntuforums.org/showpost.php?p=6092849&postcount=6)

Google rocks ;)

GLAHF

---

### Post by lisati on 2009-06-24
Good luck: and don't worry too much about stupid jokes (one comes to mind about men being men, and sheep being nervous; need I say more?)

---

### Post by starcannon on 2009-06-24
> **lisati said:**
> Good luck: and don't worry too much about stupid jokes (one comes to mind about men being men, and sheep being nervous; need I say more?)
It is a well known fact that sheep are grievous liars.

---

### Post by kd0afk on 2009-06-24
> **starcannon said:**
> I found what appears to be the solution for some with a similar problem.

Follow this post:
[http://ubuntuforums.org/showpost.php?p=6092849&postcount=6](http://ubuntuforums.org/showpost.php?p=6092849&postcount=6)

Google rocks ;)

GLAHF

That didn't work. Thanks anyway.

---

### Post by kd0afk on 2009-06-24
I just ran electricsheep - preferences in terminal and I got the preferences, clicked on the "online help" button and it took me to this page.
[http://img514.imageshack.us/img514/3...eenshotxzl.png]("http://img514.imageshack.us/img514/3590/screenshotxzl.png")

I think it speaks volumes.

---

### Post by starcannon on 2009-06-24
Never did hear what glxinfo | grep direct reported.

As it goes, I guess suit yourself. Mines working flawlessly, and I'm willing to help, but if your just not into it today then thats cool to.

GL

---

### Post by kd0afk on 2009-06-24
> **starcannon said:**
> Never did hear what glxinfo | grep direct reported.

As it goes, I guess suit yourself. Mines working flawlessly, and I'm willing to help, but if your just not into it today then thats cool to.

GL
I think tomorrow. I will be back online at around 2pm eastern time USA

---

### Post by cariboo on 2009-06-24
@kd0afk

If your were a little more lucid than it doesn't work, like at least pasting the output you get when trying a command someone gives you we may be able to resolve your problem. A little better attitude would also help.

---

### Post by Therion on 2009-06-24
> **Chemical Imbalance said:**
> Come on, it's funny.
I'm glad someone got a **charge* out of that.

[Rimshot]


See, the sheep are ELECTRIC, right, so...  An *elecrical* charge, get it?  
Gah!  It's a pun, people...

---

### Post by kd0afk on 2009-06-24
> **cariboo907 said:**
> @kd0afk

If your were a little more lucid than it doesn't work, like at least pasting the output you get when trying a command someone gives you we may be able to resolve your problem. A little better attitude would also help.

Did you not see page one of this thread?

---

### Post by cariboo on 2009-06-24
Yes I did, and if this thread is an example of the email you sent the developer, it's no wonder he told you to go away and stop bothering him.

From the Forum Code of Conduct:
> Be respectful of all users at all times. This means please use etiquette and politeness. Treat people with kindness and gentleness. If you do this the rest of the code of conduct won't need more than a cursory mention. 


---

### Post by kd0afk on 2009-06-24
> **cariboo907 said:**
> Yes I did, and if this thread is an example of the email you sent the developer, it's no wonder he told you to go away and stop bothering him.

From the Forum Code of Conduct:
So, if you saw the first page, knowing that I posted the return of the debug and you also saw that I posted the return of the other code that was suggested, why did you say that I didn't?
Just curious. Oh, by the way, what is your solution to my question?

---

### Post by surfed on 2009-06-24
When i updated to the lates e-sheep none of my old sheep worked, also mplayer syntax has changed, make sure mplayer gets called without the --zoom option.

---

### Post by kd0afk on 2009-06-24
> **surfed said:**
> When i updated to the lates e-sheep none of my old sheep worked, also mplayer syntax has changed, make sure mplayer gets called without the --zoom option.
How do I do that? I don't even know where the electric sheep files are. Do you know where the configuration file is?
I did a file search for electric sheep and electricsheep and it returned nothing

---

### Post by fooman on 2009-06-24
don't see how this will help,  but i'll post it anyways.

when i first setup my electricsheep (years ago),  i installed it through synaptic.    i then downloaded a "mega-pack" of electricsheep .mpg's that i found on a website which i can no longer locate (sorry).... they came in a huge zip file that when unzipped,  contained hundreds of these mpgs.  i took the mpgs and moved them into the .sheep file that is in my /home folder.  it worked flawlessly.

like i said,  that was years ago and many versions of ubuntu ago.  i have carried over that same /home folder in all of my upgrades and electricsheep has worked without issues throughout...as it continues to now.

electricsheep rocks!  :D

---

### Post by kd0afk on 2009-06-24
> **surfed said:**
> When i updated to the lates e-sheep none of my old sheep worked, also mplayer syntax has changed, make sure mplayer gets called without the --zoom option.
Found the preferences.xml file. Here is what it looks like:

<preferences
 nick="kd0afk"
 url=""
 password=""
 cache="2000"
 nrepeats="2"
 frame_rate="23"
 uid="494BFE1802FD642C"
 zoom="1"
 video_driver=""
 no_animation="0"
 standalone="0"
 hide_errors="0"
/>


There is nothing here that calls the mplayer. I tried adding mplayer to video driver and taking away the 1 in zoom or replacing the 1 with a 0 and even deleting the zoom line altogether and combinations of these things but nothing changes. I still get the "terminated" error.

---

### Post by starcannon on 2009-06-24
If you used that script, then you have a new version of electric sheep, and the sheep are located at:
~/.electricsheep

You can see them in Nautilus by opening your /home/username directory and pressing CTRL+H (they are hidden files)

I would rename or empty the directory entirely, and try again. I used that script to upgrade, and did not need to change any settings, though as pointed out, mileage may vary from hardware configuration to hardware configuration.

What GPU are you using; please post the output of:
```

sudo lshw -C display

```Is the driver for your card installed; please post the output of (put this one in a code box):
```

lsmod

```Is direct rendering working correctly; please post the output of:
```

glxinfo | grep direct

```Just trying to determine if its a driver issue, before we go looking for other problems, as my electric sheep install is right off that script (I tried it before recommending it) and it works as intended. Anyway lets see what those commands tell us.

---

### Post by starcannon on 2009-06-24
> **kd0afk said:**
> Found the preferences.xml file. Here is what it looks like:

<preferences
 nick="*********"
 url=""
 password="********"
 cache="2000"
 nrepeats="2"
 frame_rate="23"
 uid="494BFE1802FD642C"
 zoom="1"
 video_driver=""
 no_animation="0"
 standalone="0"
 hide_errors="0"
/>


There is nothing here that calls the mplayer. I tried adding mplayer to video driver and taking away the 1 in zoom or replacing the 1 with a 0 and even deleting the zoom line altogether and combinations of these things but nothing changes. I still get the "terminated" error.

Edit out your username and password from your output. I put asteriks in there when I quoted you, go edit that post and change your pword right away.

---

### Post by kd0afk on 2009-06-24
> **starcannon said:**
> Edit out your username and password from your output. I put asteriks in there when I quoted you, go edit that post and change your pword right away.
Thanks.

---

### Post by kd0afk on 2009-06-24
> **starcannon said:**
> If you used that script, then you have a new version of electric sheep, and the sheep are located at:
~/.electricsheep

You can see them in Nautilus by opening your /home/username directory and pressing CTRL+H (they are hidden files)

I would rename or empty the directory entirely, and try again. I used that script to upgrade, and did not need to change any settings, though as pointed out, mileage may vary from hardware configuration to hardware configuration.

What GPU are you using; please post the output of:
```

sudo lswh -C display

```Is the driver for your card installed; please post the output of (put this one in a code box):
```

lsmod

```Is direct rendering working correctly; please post the output of:
```

glxinfo | grep direct

```Just trying to determine if its a driver issue, before we go looking for other problems, as my electric sheep install is right off that script (I tried it before recommending it) and it works as intended. Anyway lets see what those commands tell us.

[B]shawn@HAL:~$ sudo lswh -C display
sudo: lswh: command not found
shawn@HAL:~$ 

[/B]```
shawn@HAL:~$ lsmod
Module                  Size  Used by
binfmt_misc            16776  1 
ppdev                  15620  0 
i915                   65668  1 
drm                    96296  2 i915
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
lp                     17156  0 
parport                42220  2 ppdev,lp
joydev                 18368  0 
snd_intel8x0           37532  4 
snd_ac97_codec        112292  1 snd_intel8x0
arc4                    9856  2 
ac97_bus                9856  1 snd_ac97_codec
ecb                    10752  2 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
pcmcia                 44748  0 
snd_seq_dummy          10756  0 
ath5k                 107008  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
mac80211              217464  1 ath5k
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
led_class              12036  1 ath5k
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           32396  1 
rsrc_nonstatic         19328  1 yenta_socket
psmouse                61972  0 
pcmcia_core            43540  3 pcmcia,yenta_socket,rsrc_nonstatic
pcspkr                 10496  0 
cfg80211               38288  2 ath5k,mac80211
serio_raw              13316  0 
snd                    62628  17 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
snd_page_alloc         16904  2 snd_intel8x0,snd_pcm
shpchp                 40212  0 
toshiba_acpi           18624  0 
input_polldev          11912  1 toshiba_acpi
intel_agp              34108  1 
video                  25360  0 
output                 11008  1 video
agpgart                42696  3 drm,intel_agp
e100                   41740  0 
mii                    13312  1 e100
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
shawn@HAL:~$ 
```


[B]shawn@HAL:~$ glxinfo | grep direct
direct rendering: Yes
shawn@HAL:~$ 

[/B]

---

### Post by kd0afk on 2009-06-24
I have to sign off in a few minutes. I will take this back up tomorrow at 2pm

---

### Post by Therion on 2009-06-24
> **kd0afk said:**
> So, if you saw the first page, knowing that I posted the return of the debug and you also saw that I posted the return of the other code that was suggested, why did you say that I didn't?  Just curious. Oh, by the way, what is your solution to my question?

Editing my post to show how I've turned over a new leaf.  I'm a calmer, cooler, geeentler forums-user.  

I am at peace, not ONLY with myself, but also with jerks who... Wait... <deep breath>

Now.  Where was I?  Oh yes... I am at peace with myself.  Peeeeeeeeeeace...

[COLOR="White"].[/COLOR]

---

### Post by starcannon on 2009-06-24
Sorry for the typo, I will fix it; the command should have been:
```

sudo lshw -C display

```Feel free to run it, but at this point its probably superfluous, as it appears that things are fine on the driver end of the deal. I will search around, it looks like your running an i915, so I'll start googling to see if there are any special parameters needed for things to work correctly with that.

I'm out googling, not ignoring.

Wondering if this is a 9.04 issue, I run 8.04 LTS, so I'm not sure if what is working here, would be working there.

Note that script was defaulted to 8.04, but can be modified for 9.04.
Open the script with a text editor and modify it to look like this; the echo lines are the ones that need modified. So try following [http://ubuntuforums.org/showpost.php?p=6092849&postcount=6](http://ubuntuforums.org/showpost.php?p=6092849&postcount=6) and use your modified script instead. You'll likely need to open System>Administration>Software Sources and remove the incorrect entry that the default script made.
```

#!/bin/bash

apt-key adv --recv-keys --keyserver keyserver.ubuntu.com f191582f22b943d1029b2d5a91dae98f32ffb679

list=/etc/apt/sources.list.d/electricsheep.list

echo 'deb http://ppa.launchpad.net/flam3/ubuntu intrepid main' > $list
echo 'deb-src http://ppa.launchpad.net/flam3/ubuntu intrepid main' >> $list

apt-get update
apt-get install electricsheep

```

---

### Post by cariboo on 2009-06-24
Thanks the script worked perfectly. I'm running Karmic, so it should run in Juanty.

---

### Post by kd0afk on 2009-06-25
> **starcannon said:**
> Sorry for the typo, I will fix it; the command should have been:
```

sudo lshw -C display

```Feel free to run it, but at this point its probably superfluous, as it appears that things are fine on the driver end of the deal. I will search around, it looks like your running an i915, so I'll start googling to see if there are any special parameters needed for things to work correctly with that.
 
I'm out googling, not ignoring.
 
Wondering if this is a 9.04 issue, I run 8.04 LTS, so I'm not sure if what is working here, would be working there.
 
Note that script was defaulted to 8.04, but can be modified for 9.04.
Open the script with a text editor and modify it to look like this; the echo lines are the ones that need modified. So try following [http://ubuntuforums.org/showpost.php?p=6092849&postcount=6](http://ubuntuforums.org/showpost.php?p=6092849&postcount=6) and use your modified script instead. You'll likely need to open System>Administration>Software Sources and remove the incorrect entry that the default script made.
```

#!/bin/bash
 
apt-key adv --recv-keys --keyserver keyserver.ubuntu.com f191582f22b943d1029b2d5a91dae98f32ffb679
 
list=/etc/apt/sources.list.d/electricsheep.list
 
echo 'deb http://ppa.launchpad.net/flam3/ubuntu intrepid main' > $list
echo 'deb-src http://ppa.launchpad.net/flam3/ubuntu intrepid main' >> $list
 
apt-get update
apt-get install electricsheep

```
 
Thanks, I will run it as soon as I am at my computer.

---

### Post by kd0afk on 2009-06-25
I don't know what happened but the only thing I have been doing with my computer is trying to get ES up and running again but when I restarted it this morning, I got all kinds of errors and now it starts up in low-graphics mode. 800x600.

---

### Post by kd0afk on 2009-06-25
I am getting all kinds of errors. My trouble started when I did the bleeding-edge intel upgrade. I am doing a complete reinstall.
Thanks for the help you gave me. This thread may get continued in the near future.

---

### Post by spotspot on 2009-07-08
Electric Sheep works great for many thousands of people.  Like any software, there are bugs and incompatibilities, and we do our best to fix them as fast as possible.  kd0afk ommitted important information from his bug report, and it wasn't until some time later with the help of other users were we able to figure out the problem (incompatibility with a new version of mplayer).  This particular problem should be fixed now.  kd0afk's attitude, however, is apparently still broken.  patch, anyone? ;)

---

