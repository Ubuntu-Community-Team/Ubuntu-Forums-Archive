---
title: "Erratic behaviour of laptop when closing the lid"
date: 2016-07-18
forum: Desktop Environments
---

### Post by tschill on 2016-07-18
I installed Ubuntu 16.04 on a HP spectre X360. Most things worked right out of the box, except for some minor annoyances. 
Lately I noticed a major problem, when closing the lid. I did set the parameter, what to do when closing the lid, to SUSPEND. Usually this is what happens - I open the lid, type my password and everything is back to normal. But several times now it happened that in between several programs have been opened for no apparent reason. Once I was logged into my guest account (that doesn't have a password). Several programs and/or system settings are open sometimes. Today I counted 28 (sic!) different programs that were running simultaneously additionally to the ones that I used before closing the lid. This nearly created a meltdown of my processor, with all these programs open at the same time. 

Anybody else who experienced something similar? Any hint, why this happens is much appreciated. My main concern is that system settings or documents are changed during this suspend time without me realising that.

P.S.: SUSPEND is also the option what to do when on battery power an inactive for 30 minutes - but though this is also a SUSPEND option, such a strange behaviour never happened, when the lid stays open.

---

### Post by jonjon2 on 2016-07-22
I'm in no way an expert, so I'm sure I won't be much help. But did you try changing the settings again just to see if it is the SUSPEND setting or not? And if it is, then the problem can be narrowed down further. But that is very strange. I have never heard of that before. If you haven't already, I would say switch up the settings first and see what is going on after you close the lid once setting have been changed. Then try SUSPEND settings again and evaluate.

---

### Post by mc4man on 2016-07-23
This has been going on since 15.04, I finally got tired of it & filed a bug several months ago. Pretty much ignored. 
Likely from some sort of 'crosstalk' between the screen & touchpad. All sorts of things can happen..
[https://bugs.launchpad.net/ubuntu/+source/unity-settings-daemon/+bug/1565031](https://bugs.launchpad.net/ubuntu/+source/unity-settings-daemon/+bug/1565031)
2 threads in this forum
[https://ubuntuforums.org/showthread.php?t=2318967](https://ubuntuforums.org/showthread.php?t=2318967)
[https://ubuntuforums.org/showthread.php?t=2290458](https://ubuntuforums.org/showthread.php?t=2290458)

It generally was worse on my laptop with a touch screen though a fresh 16.04 install on a non touch screen laptop shows this now.
Not much to be done, on my touchscreen laptop the hinges are very 'tight' so I can actually close the lid but leave it about an inch up which seems to alleviate

---

### Post by tschill on 2016-07-31
Thanks, I was quite puzzled, what is going on. Strange that they attributed this bug a low priority. It can change system settings, modify essential documents, forward emails to undesired recipients. Imho this is quite dangerous. The worst part is that Ubuntu doesn't even support very well the touchscreen! So you can't use the touchscreen in Ubuntu, but it produces this bug. Brilliant.

Seems indeed that there is not much one can do. :/ Meh.

Are mainly HP laptops affected by this bug?

---

### Post by tschill on 2016-10-30
I still haven't found a solution to this problem. But I can prevent that the computer has a life of his own, when the lid is closed. I just click SUSPEND before closing the lid. Though closing the lid should do exactly trigger the same event like clicking the Suspend command, the behaviour is afterwards different. Not the best way. But we always adapt to computers, rarely the other way round.

---

### Post by DJonsson2008 on 2017-01-02
My HP Elitebook 8440W also has crazy making suspend and lid close problems with Ubuntu 16. There is no shortage of chatter on this and other forums regarding Nvidia and suspend issues with a variety of brandname laptops.  I'm using driver 340.98 which according to Nvidia is the latest drive for use with my Quadro FX 380.

I've attempted to disable power management altogether but it makes no difference.

Problems encountered.

* Ubuntu goes into suspend multiple times after boot up and desktop is displayed.
* Shutdown or restart only goes into suspend.
* Opening the cover of the laptop relieves some of the problems once the desktop stabilizes, when using external monitor/s.

My preference would be to disable suspend altogether, as I don't use suspend or hibernate either one on this workstation,
I thought disabling power management might fix that, but it seems to make no difference. 

No sure solution can be found on the internet after hours of searching -- while it appears many other users are confronted with the similar issues.

Any insights or speculations as to why this is happening appreciated. 
Any suggestions for troubleshooting this appreciated.

Much of what I listed in the above post is related to nvidia-settings being called in start up.

Why loading nvidia-settings --load-only or doing an nvidia-settings assign call in start up causes 
ubuntu to go into suspend multiple times in startup I can't figure out. For now I've made a launcher
so I can make those calls manually after start up.

This all though leaves me with having to keep the lid open, when the laptop is docked or using external monitors.
Disabling the suspend with lid closed still appears an issue.

Finally my solution included hacks to tell the power switch to do nothing when lid was shut.

Settings in power manager gui were useless for controlling any of this, 
edits had to be made to conf files...

```
sudo gedit /etc/UPower/UPower.conf
```
and 
```
sudo -H gedit /etc/systemd/logind.conf
```

Per instructions found in this link.

[http://askubuntu.com/questions/15520/how-can-i-tell-ubuntu-to-do-nothing-when-i-close-my-laptop-lid](http://askubuntu.com/questions/15520/how-can-i-tell-ubuntu-to-do-nothing-when-i-close-my-laptop-lid)

I then also wrote a batch file to be triggered manually after boot up to control the monitor/s setup via xrandr and load some nvidia-settings ie.

```
**************************************************************************
#!/bin/sh
xrandr --output VGA-0 --primary --mode 1920x1080 --pos 5000x0 --rotate normal --output DP-4 --off --output DP-3 --off --output DP-2 --mode 1920x1200 --pos 3800x0 --rotate left --output DP-1 --off --output DP-0 --off
nvidia-settings --assign="SyncToVBlank=0" 
****************************************************************************
```

The xrandr gui arandr was priceless in getting the external monitors set up, as from there once it was right could save the params via backup settings and then paste them into the above batch file.

```
$ aptitude install arandr
```

Not sure if can marked this solved or not. As...

* ACPI in 16.04 with the power manager front end does not represent accurately what happens when the lid is shut. 
* Hacking into the conf files is needed to get a work-around. 
*  Nvidia drivers do not inspire confidence regarding suspend
    _something as simple as loading nividia settings during start up
    throws suspend into the erratic behaviour that started this discussion.
* There are those of us who would like to be able to easily ABSOLUTELY disable 'suspend'    
   & 'hibernate' temporarily (if not completely) 
   if for no other reason to be able to troubleshoot display issues like those listed above.

---

### Post by khamamet13 on 2017-01-07
Lenovo X1 + Intel onboard GPU. same problem

---

### Post by mc4man on 2017-01-12
> **DJonsson2008 said:**
> Finally my solution included hacks to tell the power switch to do nothing when lid was shut.


Not sure if can marked this solved or not. As...

Considering that what you've posted has absolutely nothing to do with this thread I'd say not..

---

### Post by Taemojitsu on 2017-01-17
This is an old thread, but if someone still has this problem, they should try to see if they can record the screen using ffmpeg while the lid is closed.

A command like this might work:

ffmpeg -hide_banner -thread_queue_size 500 -f x11grab -framerate 30 -video_size 1280x800 -avoid_negative_ts 2 -i :0.0 -thread_queue_size 500 -f pulse -i 0 -vsync vfr -r 30 -threads 1 -preset veryfast -aq-strength 0.5 -rc-lookahead 3 -bf 0 -crf 20 -vf mpdecimate=29 output.mp4

Could also maybe add '-movflags frag_keyframe', or maybe specify '-c:v libx264' and use .mkv as the output extension, or maybe use mpegts as the output format, so that the output file is still playable if the encoding is interrupted. (But all of these options might not be viewable on all media players.) In this case, there's no time limit specified with '-t value' and I hope the other options are right, but if you interrupt by pressing ctrl-C once, it should finish up and give a usable file.

---

### Post by blackmagic09 on 2017-12-14
Hi there,
I am a newbie to Linux and still got the problem on my HP Spectre. But there is a workaround for Xubuntu user (tested with Xubuntu 16.04.).
Before closing the lid press crtl+alt+del to get into XScreenSaver. In there random behavior can hardly done any harm to your system because in there you have to type in your password and click on login. Therefore chances are very slim that this occurs by random chance.
ByTheWay: Your apps will continue to work. I tested this method by playing a music file when entering XScreenSaver.
Greetings BlackMagic09

---

### Post by QIII on 2017-12-14
Rest In Peace, dear old thread.

---

