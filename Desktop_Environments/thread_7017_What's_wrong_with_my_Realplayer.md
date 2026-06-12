---
title: "What's wrong with my Realplayer?"
date: 2004-12-03
forum: Desktop Environments
---

### Post by haocheng on 2004-12-03
Hi~~~

I just downloaded RealPlayer10GOLD.bin and 
installed it by 
```

sudo ./RealPlayer10GOLD.bin.

```

There was no error messages.
But when I try to run it...

Nothing showed on my screen!!! 
I checked it: 
```

robin@ubuntu:/usr/local/src/Realplayer $ ps aux | grep realplay
robin     5631  0.0  0.1  3444 1316 ?        S    22:31   0:00 /bin/sh /usr/bin/realplay
robin     5636  0.0  0.9 56740 9992 ?        Sl   22:31   0:00 /usr/local/src/Realplayer/realplay.bin
robin     5638  0.0  0.5 21900 5804 ?        S    22:31   0:00 /usr/local/src/Realplayer/realplay.bin
robin     5639  0.0  0.5 21900 5804 ?        S    22:31   0:00 /usr/local/src/Realplayer/realplay.bin
robin     5936  0.0  0.0  2672  768 pts/2    S+   22:46   0:00 grep realplay

```

The realplayer is running but I see nothing. :sad: 

Can anyone tell me what's wrong with my Realplayer?

Any help is appreciated and many thanks in advance  : )

---

### Post by wolovids on 2004-12-07
I am running Hoary (all updated packages as of Dec 06, 2004) and I am having the same issues with Real Player 10 for Linux.  

My first guess is that there is an issue with the new development version of GTK+ and/or Gnome.  I'm glad I wasn't alone on this one.  It worked with just Warty installed.

EDIT: I just found this [thread](http://ubuntuforums.org/showthread.php?t=5923)  ... is there anyway to make Real Player use esd?

I really can't wait for GStreamer (or equivalent) to fix the sound problems in Linux.  It's just a mess.

---

### Post by randy on 2004-12-07
You need to run the installer with gksudo instead of sudo so that it can access your screen.

---

### Post by wolovids on 2004-12-07
[QUOTE=randy]You need to run the installer with gksudo instead of sudo so that it can access your screen.[/QUOTE]Real Player does not get displayed after an installation.   So, just running "realplay" will have processes running but there is no display.

---

### Post by TravisNewman on 2004-12-07
You don't have to use gksudo for apps to access the screen.

sudo nautilus brings up root's home directory
sudo glxgears brings up... well... glxgears

---

### Post by mojo on 2004-12-10
my lad, it's a known bug in all Debian distro. I've already worked on it since, the prob is of swf plugin, if u remove the swfrender.so and swfformat.so in Plugin folder, RealPlayer will run BUT won't work 100% well like expected. Be patient, and may the Ubuntu be with you.  :lol:

---

### Post by JsPr on 2004-12-10
I have Realplayer 10 installed and working just fine with Warty. I have no problems with either the player nor the plugin.

---

### Post by mojo on 2004-12-10
Some PC runs RealPlayer fine (with Warty) but with Hoary, thing turns out to be different. But I have good news, the latest build 08/12/2004 (or RealPlayer 10.2 RC1) has fixed this bug, the next 10.2 will run fine on all Hoary and Warty.

---

### Post by macewan on 2004-12-11
[QUOTE=mojo]Some PC runs RealPlayer fine (with Warty) but with Hoary, thing turns out to be different. But I have good news, the latest build 08/12/2004 (or RealPlayer 10.2 RC1) has fixed this bug, the next 10.2 will run fine on all Hoary and Warty.[/QUOTE]
 [http://ubuntuguide.org/#realplayer](http://ubuntuguide.org/#realplayer)

---

### Post by nanaban on 2005-02-14
[QUOTE=macewan][http://ubuntuguide.org/#realplayer](http://ubuntuguide.org/#realplayer)[/QUOTE]

I followed the guide and had the same problem. What should I do then?

---

### Post by Xian on 2005-02-14
[QUOTE=nanaban]I followed the guide and had the same problem. What should I do then?[/QUOTE]
Just as a quick check to see if there is another application which is conflicting with RP10, disable your sound in Gnome (Computer > Desktop Pref > Sound) by unticking both boxes listed under the "General" tab, and then try to start the application from a totally fresh launch. Also, be certain that no other programs which might try to access your sound card are running.

If the RP10 application is running but there is no interface it is generally due to some type of system sound access conflict.

---

### Post by nanaban on 2005-02-14
[QUOTE=Xian]Just as a quick check to see if there is another application which is conflicting with RP10, disable your sound in Gnome (Computer > Desktop Pref > Sound) by unticking both boxes listed under the "General" tab, and then try to start the application from a totally fresh launch. Also, be certain that no other programs which might try to access your sound card are running.

If the RP10 application is running but there is no interface it is generally due to some type of system sound access conflict.[/QUOTE]

You are right! I could start RealPlayer after I unchecked the boxes. What should I do to resolve the sound access conflict?

---

### Post by Xian on 2005-02-14
[QUOTE=nanaban]You are right! I could start RealPlayer after I unchecked the boxes. What should I do to resolve the sound access conflict?[/QUOTE]
Run the system monitor (Applications > Systems Tools > System Monitor) and click on the "Process Listing" tab. Select "All Processes" from the drop down menu. Scroll down the list of what is currently running on your system and look for anything that might be audio related which could be interfering with RealPlayer getting access to the sound system.

---

### Post by nanaban on 2005-02-14
[QUOTE=Xian]Run the system monitor (Applications > Systems Tools > System Monitor) and click on the "Process Listing" tab. Select "All Processes" from the drop down menu. Scroll down the list of what is currently running on your system and look for anything that might be audio related which could be interfering with RealPlayer getting access to the sound system.[/QUOTE]

It was "**esd**". RealPlayer pops up right away after I end the esd process.
I have also tried Desktop->Preference->Multimedia System Selector, and chose other systems for output. Same result. ](*,)

---

### Post by Xian on 2005-02-15
[QUOTE=nanaban]It was "**esd**". RealPlayer pops up right away after I end the esd process.[/QUOTE]
Check the contents of you /etc/esound/esd.conf file. Do they look like this?
```
[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 2
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=
```

The main thing you really want is that "-as 2" on the end of the spawn_options.
This tells esd to free the audio device after 2 seconds of inactivity.

---

### Post by Xian on 2005-02-15
[QUOTE=nanaban]It was "**esd**". RealPlayer pops up right away after I end the esd process.[/QUOTE]
Check the contents of you /etc/esound/esd.conf file. Do they look like this?
```
[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 2
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=
```

The main thing you really want is that "-as 2" on the end of the spawn_options.
This tells esd to free the audio device after 2 seconds of inactivity.

---

### Post by nanaban on 2005-02-15
Changed, but didn't solve the problem.

---

### Post by Xian on 2005-02-15
[QUOTE=nanaban]Changed, but didn't solve the problem.[/QUOTE]
You might have to reboot....

If that doesn't work then do this:
Use the System Monitor to make certain there are no running instances of RealPlayer.

Open a terminal and type in:
```
$ export LD_ASSUME_KERNEL=2.2.5
$ realplay
```

---

### Post by nanaban on 2005-02-15
I did all, but no difference.

---

### Post by rohandhruva on 2005-02-15
Hi, 

Thanks for the tips. If i delete the swf* files in the plugins directory it starts fine - else it doesnt even start. Then, if i disable the two ticks in Sound prefs. it works great. So, as a newbie to esd, what we are actually looking for is audio mixing - please have a look at this site - [http://fedoranews.org/contributors/andre_costa/alsa/](http://fedoranews.org/contributors/andre_costa/alsa/)

Though this is for alsa but i think it can be adapted for esd ?

Rohan.

---

### Post by Xian on 2005-02-15
If you do a "lsof /dev/dsp" command in a terminal you will most likely see something like this:
```
$ lsof /dev/dsp
COMMAND  PID USER   FD   TYPE DEVICE SIZE NODE NAME
esd     4546 xian   27w   CHR   14,3      7725 /dev/dsp
```
For some reason your sound card is not allowing multiple access to the needed path.

The best thing I can suggest is just to open the Sound Preferences 
*Computer > Desktop Preferences > Sound*

And untick the box that says "Enable Sound Server Startup"
On your next reset you should be able to run RP10.

---

### Post by mriya3 on 2005-02-27
Here's my solution (it enables Realplay to work either standalone or as mozilla plugin)

1. Enable Alsa soft-mixing as described in post [http://ubuntuforums.org/showthread.php?t=8882&highlight=hear+multiple+sound](http://ubuntuforums.org/showthread.php?t=8882&highlight=hear+multiple+sound)
(also setup esd and multimedia system settings as described in that post)

2. Install realplayer as described in [http://ubuntuguide.org/#realplayer](http://ubuntuguide.org/#realplayer)

3. Install **alsa-oss**

4. Open the launcher script **realplay** located in Realplayer's install directory (/opt/RealPlayer if you followed previous instructions)

5. Find lines
```
if [ -n "$LD_PRELOAD" ]; then
    echo "Warning: LD_PRELOAD=\"$LD_PRELOAD\""
fi

```
6. ...and after add this code:
```
LD_PRELOAD="$LDPRELOAD:/usr/lib/libaoss.so"
export LD_PRELOAD
```

7. Now you get RealPlayer working with Alsa mixing (and so combinations of Realplay, Xine, Mplayer, Frozen Bubble,...sounds work at the same time  \\:D/ )

---

### Post by Leion on 2005-06-27
[QUOTE=mriya3]Here's my solution (it enables Realplay to work either standalone or as mozilla plugin)

1. Enable Alsa soft-mixing as described in post [http://ubuntuforums.org/showthread.php?t=8882&highlight=hear+multiple+sound](http://ubuntuforums.org/showthread.php?t=8882&highlight=hear+multiple+sound)
(also setup esd and multimedia system settings as described in that post)

2. Install realplayer as described in [http://ubuntuguide.org/#realplayer](http://ubuntuguide.org/#realplayer)

3. Install **alsa-oss**

4. Open the launcher script **realplay** located in Realplayer's install directory (/opt/RealPlayer if you followed previous instructions)

5. Find lines
```
if [ -n "$LD_PRELOAD" ]; then
    echo "Warning: LD_PRELOAD=\"$LD_PRELOAD\""
fi

```
6. ...and after add this code:
```
LD_PRELOAD="$LDPRELOAD:/usr/lib/libaoss.so"
export LD_PRELOAD
```

7. Now you get RealPlayer working with Alsa mixing (and so combinations of Realplay, Xine, Mplayer, Frozen Bubble,...sounds work at the same time  \\:D/ )[/QUOTE]



i have installed realplayer but i do not have a /opt/Realplay directory

---

### Post by bier444 on 2005-06-27
>I just downloaded RealPlayer10GOLD.bin and 
>installed it by 
>```

>sudo ./RealPlayer10GOLD.bin.
>
```

>There was no error messages.
>But when I try to run it...

maybe this solves your problem:
login as root
nano /etc/esound/esd.conf
there change “auto_spawn=0” to “auto_spawn=1”
after that, restart esd:
killall esd
esd -nobeeps &

problems with rm-files from amazon:
amazon uses rm-files, which are created with old codecs.

so install w32codecs from

deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-backports main universe multiverse
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-extras main universe multiverse restricted

or your preferred backport source..

copy dnet.so.6.0 and ddnt.so.6.0 from /usr/lib/win32 to the codec-directory from realplayer (e.g. /usr/local/RealPlayer/codecs). 

now,

cd /usr/local/RealPlayer/codecs
ln -s dnet.so.6.0 dnet.so

hopefully now all works correctly. 

bier444

---

### Post by wo.anderer on 2005-07-22
[QUOTE=mriya3]Here's my solution....

4. Open the launcher script **realplay** located in Realplayer's install directory (/opt/RealPlayer if you followed previous instructions)
.....
[/QUOTE]

Thanks works like a charm...so far ;) However I found my realplay script mentioned in point 4 at: /usr/lib/realplay-10.0.4/realplay

---

### Post by Grimmy on 2005-07-24
[QUOTE=wo.anderer]Thanks works like a charm...so far ;) However I found my realplay script mentioned in point 4 at: /usr/lib/realplay-10.0.4/realplay[/QUOTE]

Me too.

This seems to be because the instructions on Ubuntu Guide have changed... They used to involve installing Realplayer manually, but now it is obtained using apt-get.

---

### Post by FX on 2005-07-24
I've been trying to get realplayer working but haven't be successful. After reading about all the hoops to jump through to get it working right, for me, it would be just easier to reboot into windows.

Just one more of the reason's why I personally don't think that Linux is ready for the desktop yet.

<note> Kind of in a bad mood so don't take that last line to hear too much.

---

### Post by nickname on 2005-07-25
I've just followed the steps to getting real player working, however it works but it's abit choppy, compared to real player in windows or real player in other distros like mandrake. Is there any way of increasing the quality???

---

### Post by sainter54 on 2006-04-24
I have searched heaps of threads but am still having trouble with my sound, and I particularly want RealPlayer to work.
I had heaps of trouble just getting sound to work for little things like start-up tunes in Ubuntu, and other tiny things like that.
Now they work, but I'm still having trouble, but I've hardly got any error messages, so I can't see where I'm going wrong.
I'm using Hoary 5.04. Alsa is installed, and I think it's working (that's what got my system sounds happening, and I haven't had any error messages). All the steps on this thread are done, without any error messages.
Here are some querks:
When I go to System->Preferences->Multimedia Systems Selector and I chose to make the output ALSA, I test the device and get a message saying 
"Failed to construct test pipeline for 'ALSA - Advanced Linux Sound Architecture'"
The same happens for OSS, but not for ESD - it works.
And same again for the Audio Input.
Now from what I understand, Ubuntu would then be playing sounds through ESD, and Realplayer is trying to play sound through ALSA (now that I edited the launcher script).
But it's not working, which would make sense if ALSA isn't working...But I can change the volume settings for my device HDA Intel (ALSA Mixer) or the device Realtek ALC260 (OSS Mixer), and for both the volume of my system sounds will alter, which makes me think ALSA (and OSS) is working.
And to top it off, when I go to RealPlayer to play my file, no error message....but the url successfully streams, without any sound whatsoever....
I'm completely lost....can someone please help me, or atleast point me in the right direction? I swear I must've tried just about everything.
Thanks in advance


CANCEL THAT!

Well, now I have RealPlayer working...Just had to kill ESD and change my System->Preferences->Multimedia Systems Selector Audio Output to ALSA....but now my system sounds don't work. Was my system using ESD to play audio? How might I be able to channel that to ALSA?

---

