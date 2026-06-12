---
title: "gksudo delay"
date: 2007-11-18
forum: Desktop Environments
---

### Post by newkirk on 2007-11-18
I've had a problem for a while now in Xubuntu.  7.04 and 7.10 at least.  I've googled forever on it and found nothing useful except one post here ([http://ubuntuforums.org/showthread.php?t=545148](http://ubuntuforums.org/showthread.php?t=545148)) which never received any reply or followup, describing the same problem.

Anything that needs admin privileges asks for a password with gksudo, and it variously hangs for anywhere from 2 to 40 seconds after entry before ungrabbing/ungraying the desktop and starting synaptic or whatever.

I've reproduced this from terminal with repeated 'gksudo -p xfce4-terminal' ('-p', though meant for printing password back to console, has the side-effect of always asking for password despite having successfully received one just moments before)  Tried with '-d' debug option and the only output is "sn_launcher_context_complete called for an SnLauncherContext that hasn't been initiated".

I've timed it several times with no change in system load, and it's taken as little as two seconds one time to as long as 39 seconds.  Twice out of 12 tests the password dialog remained open the whole time (one of those the password was half-printed on the console the whole time as well) while other times the dialog disappears immediately, yet the screen remains grayed and locked for over a half-minute.

If an incorrect password is provided it returns immediately, every time.

I just can't figure out why it's doing it, while the presence of only a single post on the subject leads me to believe it's something on my system, not something about gksudo.  And it doesn't do it for another login, just my primary username.

j

---

### Post by bapoumba on 2007-11-18
Hello, i've looked around but did not find anything relevant. I'll keep looking.
I do not have this problem. May be look at the output to:
```
isabella@yeti:~ $ gksudo -S -d thunar
No ask_pass set, using default!
xauth: /tmp/libgksu-q1ilcE/.Xauthority
STARTUP_ID: gksudo/thunar/8103-0-yeti_TIME1379707764
cmd[0]: /usr/bin/sudo
cmd[1]: -H
cmd[2]: -S
cmd[3]: -p
cmd[4]: GNOME_SUDO_PASS
cmd[5]: -u
cmd[6]: root
cmd[7]: --
cmd[8]: thunar
buffer: -GNOME_SUDO_PASSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSS-
brute force GNOME_SUDO_PASS ended...
Yeah, we're in...
xauth: /tmp/libgksu-q1ilcE/.Xauthority
xauth_env: /home/isabella/.Xauthority
dir: /tmp/libgksu-q1ilcE
isabella@yeti:~ $ 

```

---

### Post by newkirk on 2007-11-18
Output below - the 'hang' occurs after "Yeah, we're in...", about 15 seconds this time.

No ask_pass set, using default!
xauth: /tmp/libgksu-jNIlGf/.Xauthority
STARTUP_ID: gksudo/thunar/9326-0-BlakBox_TIME1418326686
cmd[0]: /usr/bin/sudo
cmd[1]: -H
cmd[2]: -S
cmd[3]: -p
cmd[4]: GNOME_SUDO_PASS
cmd[5]: -u
cmd[6]: root
cmd[7]: --
cmd[8]: thunar
buffer: -GNOME_SUDO_PASSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSS-
brute force GNOME_SUDO_PASS ended...
Yeah, we're in...
xauth: /tmp/libgksu-jNIlGf/.Xauthority
xauth_env: /home/newkirk/.Xauthority
dir: /tmp/libgksu-jNIlGf


j

---

### Post by Telecaster72 on 2007-11-18
I have this bug too on a fresh install of xubuntu 7.10.

---

### Post by Telecaster72 on 2007-11-19
Here's my output, one thing was different from your outputs was "libgksu-HEiUO8" at the "xauth"-line, but i saw none of your two's were the same either..


No ask_pass set, using default!
xauth: /tmp/libgksu-HEiUO8/.Xauthority
STARTUP_ID: gksudo/thunar/5823-0-kubuntu-desktop_TIME1466362361
cmd[0]: /usr/bin/sudo
cmd[1]: -H
cmd[2]: -S
cmd[3]: -p
cmd[4]: GNOME_SUDO_PASS
cmd[5]: -u
cmd[6]: root
cmd[7]: --
cmd[8]: thunar
buffer: -GNOME_SUDO_PASSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSS-
brute force GNOME_SUDO_PASS ended...
Yeah, we're in...
xauth: /tmp/libgksu-HEiUO8/.Xauthority
xauth_env: /home/olle/.Xauthority
dir: /tmp/libgksu-HEiUO8


I found a bugreport concerning this at launchpad : [https://bugs.launchpad.net/ubuntu/+source/gksu/+bug/152855](https://bugs.launchpad.net/ubuntu/+source/gksu/+bug/152855)

---

### Post by bapoumba on 2007-11-19
Both of your outputs look normal to me. From the bug report, a clean reinstall or removing some hardware did not help, and the user experimented this problems on one computer only.
Would it have to do with some user specific configuration? Or video drivers?

Could both of you post in the bug report, may be linking to this thread, so that the bug does not get closed?

---

### Post by Telecaster72 on 2007-11-19
I must have read your mind because while you wrote your post i wrote in the bugreport :-)
Since it worked fine in GNOME in Edgy, Feisty and Gutsy it seems like it is a Xubuntu or xfce specific problem.
I am not experiencing any other problems in this setup, i am using Nvidia-glx through the restricted driver manager, i can try using the open source driver later but now i have to leave, i'll try it and check back later..
This occured from the first boot after the clean install even before i started tweaking the system, have a separate /home partition and have played around with xfce before i installed xubuntu so do you think it could be some old xfce setting that is doing something?


> **bapoumba said:**
> Both of your outputs look normal to me. From the bug report, a clean reinstall or removing some hardware did not help, and the user experimented this problems on one computer only.
Would it have to do with some user specific configuration? Or video drivers?

Could both of you post in the bug report, may be linking to this thread, so that the bug does not get closed?

---

### Post by bapoumba on 2007-11-19
> **Telecaster72 said:**
> I must have read your mind because while you wrote your post i wrote in the bugreport :-)
Thanks, a couple mods can confirm reading minds has happened a lot ^^

> **Telecaster72 said:**
> 
Since it worked fine in GNOME in Edgy, Feisty and Gutsy it seems like it is a Xubuntu or xfce specific problem.
I am not experiencing any other problems in this setup, i am using Nvidia-glx through the restricted driver manager, i can try using the open source driver later but now i have to leave, i'll try it and check back later..
This occured from the first boot after the clean install even before i started tweaking the system, have a separate /home partition and have played around with xfce before i installed xubuntu so do you think it could be some old xfce setting that is doing something?
I have no idea. I have my /home on a separate partition too, from Warty times, use the restricted nvidia drivers since Gutsy (was using the nv drivers before), and do not experiment these hangs when prompted for my password.
I'll try to check again (I rarely use GUI applications anyway) with synaptic and some of the system menus.

---

### Post by Telecaster72 on 2007-11-19
Ok so i tested with the "nv" driver and the problem dissapeared, i just cant use composite effects anymore without really sluggish performance.
I have a GeForce 3 ti 200 card.



01:00.0 VGA compatible controller: nVidia Corporation NV20 [GeForce3 Ti 200] (rev a3)

---

### Post by bapoumba on 2007-11-19
I'll enable composting to test it further. Opening Synaptic took about 3 secs, I'm not sure I would have noticed such a delay without paying attention to it..
Here is my video card:
```
$ lspci | grep nVidia
01:00.0 VGA compatible controller: nVidia Corporation NV36 [GeForce FX Go5700] (rev a1)
```

---

### Post by newkirk on 2007-11-19
For me I'm running xubuntu on a VIA C7 mini-itx board.  I can confirm that it's per-user - I posted above (last line, original post) that it does NOT do it for another username logging into the same system.

I strongly suspect something in ~/.* is the proximate cause, though whatever it's triggering in gksudo may need fixed, in the bigger picture.  But I've spent years with KDE, just a couple months with Xubuntu and still don't know my way around the config files, nor have a feel for what/how some components interact.

j

---

### Post by arrrghhh on 2007-11-19
yea i posted that bug report...

i did test multiple machines - and this only occured on my home desktop.  i couldn't use the 'nv' drivers - X wouldn't even load.  with the new 'unbreakable X' it would default back to the vesa driver just to render *something*.  

it does seem video card related - i'm running the nvidia 7600GT 256mb pci-e.  i've had quite a few issues with this card.  i would have to run the official nvidia installer from the console with no window manager running - every single reboot, which seem to have been fixed because i haven't needed to do that in a while, although this machine really never reboots!

gnome, no issues.  kde, no issues.  i've recently switched to kde as i noticed xfce was not utilizing my memory very well... i have no idea why, but on all my machines old and new kde seems to work better (although none are really old...)

---

### Post by bapoumba on 2007-11-19
> **newkirk said:**
> For me I'm running xubuntu on a VIA C7 mini-itx board.  I can confirm that it's per-user - I posted above (last line, original post) that it does NOT do it for another username logging into the same system.
Sorry I had missed this.
Do you see the lag with the first user created during the install or another one added after ? 
> **newkirk said:**
> 
I strongly suspect something in ~/.* is the proximate cause, though whatever it's triggering in gksudo may need fixed, in the bigger picture.  But I've spent years with KDE, just a couple months with Xubuntu and still don't know my way around the config files, nor have a feel for what/how some components interact.

j
Complete shot in the dark: anything in the .xsessions.errors?

---

### Post by Telecaster72 on 2007-11-19
I think it might be related to XFCE's own composite manager, this only occurs for me when i have composite enabled in the settings, Nvidia or nv driver makes no difference for me as i thought before, composite does.
I would think beryl/compiz has its own or a modified version of the one in Xubuntu, if so that would explain why it only happens in Xubuntu.

Do any of you notice a difference with composite on/off?

---

### Post by newkirk on 2007-11-19
> **bapoumba said:**
> Sorry I had missed this.
Do you see the lag with the first user created during the install or another one added after ? 
My own user account, first created when I'd installed each time.  It wasn't always there either, or maybe it just ran short (2-5 secs) more often at the time.

> Complete shot in the dark: anything in the .xsessions.errors?
Nothing.

AFA my video, the problem has existed under Vesa, Via, and Openchrome video.  I can ctrl-alt-f1 and get a vt, ctrl-alt-7 takes me back to X with a black screen and (movable) mouse cursor.  Whenever it finishes what it finishes, it repaints the desktop and proceeds.

WHILE it's hung and I'm on vt1 I glance at 'top' and see xfwm4 using 56% CPU and Xorg using 36%.  But it's not simply a resource issue (1.5ghz C7) - it will do it on my main login, and I can 'switch user' to a different user on a second X session and gksudo blows right through without hesitation.

j

---

### Post by newkirk on 2007-11-19
> **Telecaster72 said:**
> Do any of you notice a difference with composite on/off?

Yes.  I disabled Compositing in 'Window manager Tweaks' and it blew right through.  Of course that has other repercussions).  So I tested further and I find that the key is 'Display shadows under popup windows'.  So either it's not playing nice with gksudo's UI takeover, or gksudo isn't.

Good call.

j

---

### Post by arrrghhh on 2007-11-20
good call indeed.  the source of this problem is definitely display compositing, i can confirm with this feature disabled there are no more issues.

---

### Post by tristan on 2007-11-20
I have experienced the same issue with xfce. It is definitely related to compositing, and does not occur if compositing is switched off. I like my xfce composite effect so...

The other way to prevent the problem is to make sure that gksudo is called with the -g option (ie gksudo -g) so that it does not steal focus and grey the screen. I did a global search and replace of gksudo with gksudo -g and don't experience the problem any more. Probably not the most elegant way of dealing with the problem but c'est la vie!

---

### Post by Telecaster72 on 2007-11-20
Excellent!!

---

### Post by bapoumba on 2007-11-20
Interesting.
This should be the same for gksu, then.

So it is not a gksu/gksudo problem, as I understand it.

---

### Post by newkirk on 2007-11-20
> **bapoumba said:**
> Interesting.
This should be the same for gksu, then.

So it is not a gksu/gksudo problem, as I understand it.

It looks like the xfwm4 dropshadow support doesn't play nice with XGrabServer().

j

---

### Post by bapoumba on 2007-11-20
[http://bugzilla.xfce.org/](http://bugzilla.xfce.org/)
I spent some time looking for existing bugs in Xfce bugzilla but did not find any related to this one.
Could someone please have a look, and may be file a new one?

---

### Post by Telecaster72 on 2007-11-20
I didn find any there either, so i posted one.
[http://bugzilla.xfce.org/show_bug.cgi?id=3681](http://bugzilla.xfce.org/show_bug.cgi?id=3681)
...this is kinda fun..

---

### Post by tw1ggy.ramir3z on 2007-11-23
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/gksu/+bug/152855](https://bugs.launchpad.net/ubuntu/+source/gksu/+bug/152855) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				There's another elegant way to solve this problem! ;)

Just run ```
gksu-properties
``` and change "Capture mode" from enable to disable! So you can keep enable your composite as you like! Enjoy! :)

---

### Post by Telecaster72 on 2007-11-23
Beautiful!
Works like a charm...thank you!!

Really the most elegantest way ;-)

---

### Post by arrrghhh on 2007-11-23
now i'm curious, what is 'capture mode' and why does it cause so much headache?  what are the pros/cons of this mode?

thanks!

---

### Post by tw1ggy.ramir3z on 2007-11-24
It make the gksu window like a floating window. When you enable capture mode, it take a shoot of your desktop and place a gksu window on it... It really annoing me. I want to see what appens on my desktop in every moment. I disable capture mode also when I was on Gnome. I prefer gksu floating window than the "freezing desktop window". Hope I was clear. I'm Italian, and sorry for my bad english! :lolflag:

---

### Post by bapoumba on 2007-11-24
[https://bugs.launchpad.net/ubuntu/+source/kdegraphics/+bug/108673](https://bugs.launchpad.net/ubuntu/+source/kdegraphics/+bug/108673)
This is the only bug I found regarding capture-mode, and it's not related to gksu or gksudo.
So is this related to video drivers ?

---

