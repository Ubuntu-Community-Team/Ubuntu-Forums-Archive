---
title: "Kubuntu Disappointment"
date: 2009-11-18
forum: Desktop Environments
---

### Post by mvalviar on 2009-11-18
I wanted to give Kubuntu a try after a year of using ubuntu. I installed kubuntu-desktop. Kubuntu has a nice presentation but I've experienced poor performance though. 

I've seen blank entries in the task bar. Even if I run a kill all on an application (one is suspect to be the blank entry) I doesn't go away.

I've seen glitches in drag and drop operations.

KDE is fairly heavy on resources as well.

Dolphin leaves .directory which is annoying. I often reach for the terminal and it's distracting seeing these files.

Am I the only one experiencing these glitches? Will it go away if I install kubuntu from scratch?

---

### Post by viralmeme on 2009-11-18
> **mvalviar said:**
> I wanted to give Kubuntu a try after a year of using ubuntu. I installed kubuntu-desktop. Kubuntu has a nice presentation but I've experienced poor performance though ..

I'm happy with Xubuntu  ...

---

### Post by lovinglinux on 2009-11-18
Works great for me.

---

### Post by Zorael on 2009-11-18
I've had the empty task manager entry bug once during the Karmic beta, and a subsequent update fixed it. I haven't had it since, certainly not after release.

No glitches in drag/drop operations for me, though admittedly I mostly copy/paste.

As for resources, I found it to be pretty much on par with GNOME, while Xfce was noticeably below them both. 'free -m' on my netbook currently says it's using 264mb buffers/cache, though it only has an hour's uptime. This is with a decent Plasma desktop (folder view, show desktop, analogue clock widgets) with a standad panel (menu, task manager, pager, system tray, power manager, digital clock), and while running Kopete, Konversation and Yakuake. In [this thread](http://ubuntuforums.org/showthread.php?p=8256900&postcount=30) I had 306mb used at an uptime of 5 days. You may want to check if you're getting autostarted applications from both environments, like glipper and klipper, kmix and GNOME's/Pulse's mixer applet, etc.

I don't think there is a way to disable Dolphin from creating .directory files. It is very much by design, I'm afraid.

The only KDE app I'm truly disappointed with is Krfb. It is garbage, unusable. 30% cpu usage when not doing anything, allegedly due to the code not making use of interrupts. I have learned to love x11vnc.

---

### Post by Dullstar on 2009-11-18
> **mvalviar said:**
> I wanted to give Kubuntu a try after a year of using ubuntu. I installed kubuntu-desktop. Kubuntu has a nice presentation but I've experienced poor performance though. 

I've seen blank entries in the task bar. Even if I run a kill all on an application (one is suspect to be the blank entry) I doesn't go away.

I've seen glitches in drag and drop operations.

KDE is fairly heavy on resources as well.

Dolphin leaves .directory which is annoying. I often reach for the terminal and it's distracting seeing these files.

Am I the only one experiencing these glitches? Will it go away if I install kubuntu from scratch?

From what I hear, (K)Ubuntu ain't the best KDE distro out there.  I haven't noticed any major problems with KDE though, once I figured out that the issue I had was due to sudo apt-get install kde instead of sudo apt-get install kubuntu-desktop.

---

### Post by Zorael on 2009-11-18
> **Dullstar said:**
> I haven't noticed any major problems with KDE though, once I figured out that the issue I had was due to sudo apt-get install kde instead of sudo apt-get install kubuntu-desktop.
Yeah, even with a core KDE installation you *will* want at least kubuntu-default-settings, or GTK apps (including Firefox) will make your eyes bleed.

---

### Post by Melcar on 2009-11-18
Kubuntu will just leave you a bad impression of KDE.  Use OpenSuse or even Fedora if you want KDE done right.  Kubuntu isn't that bad, but it does have the odd "wtf" quirk here and there.

---

### Post by mvalviar on 2009-11-18
Honestly I find most that most kde apps are better that their gnome counterpart. Amarok vs RB, k3b vs brasero. Sure you can run kde apps in gnome but its buggy and I hate having to install extra packages. Amarok's classic 'Launching http cache cleaner' on gnome is still alive and kicking. 

Maybe I'll wait till Kubuntu LL. I've heard the kubuntu devs want make that lts release a perfect one. But then again GNOME 3 will be out...

---

### Post by Clamwacker on 2009-11-18
I've had some issues as well with just installing the kubuntu-desktop package.  

For starters I can't shutdown or restart my machine.  The options just aren't there in the "Leave" section in Kickoff.   I have to log out of kde and go itno gnome, or run shutdown from a terminal.  

I also had a blank spot in the task bar like you did.  It turned out to be some gnome based power management deal, I'm assuming for laptops with batteries to monitor.  

I also have an issue with Amarok hoarding the sound card whenever it is running.  With Rhythmbox I can hit pause and then watch a video, or even hear the little beeps and bongs and flash animations and stuff in firefox, but not with Amarok running. 

It's really kind of a bummer because I *want* to like KDE.  The apps look so much better, such as KTorrent vs Transmission.  The way it handles desktop wallpaper on multiple monitors seems better (even though I have to open the "Desktop settings" from whichever monitor I actually want to change).  I've heard great things about them making a comeback with 4.3 but it still seems glitchy. 

I came back to ubuntu from OpenSuSE 11.2 because it was even worse for me.  The install for it is nice and slick.  After that though I had numerous problems, apps would crash all the time and I got really sick of the KDE Crash Handler window popping up.  It's not bad ram, memtest clears it in every test (which takes a long time with 8Gb or RAM!)  and my gnome based Ubuntu installation works great.  The biggest thing bringing me back to Ubuntu though was these forums.  Opensuse's  is hardly as well organised and doesn't seem to have the membership/activity as this one.

---

### Post by lovinglinux on 2009-11-18
> **Zorael said:**
> Yeah, even with a core KDE installation you *will* want at least kubuntu-default-settings, or GTK apps (including Firefox) will make your eyes bleed.

I don't have **kubuntu-default-settings** installed and everything works great, including GTK applications.

---

### Post by Melcar on 2009-11-18
You really need to either install a KDE DE or a GNOME DE.  Having both running on the same install is fine and all, but you will eventually run into weird glitches.

---

### Post by Zorael on 2009-11-19
> **lovinglinux said:**
> I don't have **kubuntu-default-settings** installed and everything works great, including GTK applications.
Really? Perhaps QtCurve sets itself up by itself nowadays. Else kubuntu-default-settings exports the gtkrc file (via ~/.kde/env/gtk2-engines-qtcurve.sh from /usr/share/kubuntu-default-settings/gtk2-engines-qtcurve.sh) to tweak GTK app theming.

---

### Post by lovinglinux on 2009-11-19
> **Zorael said:**
> Really? Perhaps QtCurve sets itself up by itself nowadays. Else kubuntu-default-settings exports the gtkrc file (via ~/.kde/env/gtk2-engines-qtcurve.sh from /usr/share/kubuntu-default-settings/gtk2-engines-qtcurve.sh) to tweak GTK app theming.

Well, I could be missing something, since this is the first time I use KDE. Anyway, I had to rename **.gtkrc-2.0-kde4**, which is the file created by "System Settings >> Look & Feel >> Appearance >> GTK+ Appearance", to **.gtkrc-2.0** to make the theme work.

---

### Post by clipgangbloodgang on 2009-11-19
> **lovinglinux said:**
> Well, I could be missing something, since this is the first time I use KDE. Anyway, I had to rename **.gtkrc-2.0-kde4**, which is the file created by "System Settings >> Look & Feel >> Appearance >> GTK+ Appearance", to **.gtkrc-2.0** to make the theme work.

Thanks a lot for this. It works.

---

### Post by dvhart on 2009-11-23
I don't see the GTK+ Appearance panel in my KDE4 system settings. Is there a package I should be installing? I also don't have a .gtkrc-2.0-kde4 file in my home directory.

---

### Post by Zorael on 2009-11-23
> **dvhart said:**
> I don't see the GTK+ Appearance panel in my KDE4 system settings. Is there a package I should be installing? I also don't have a .gtkrc-2.0-kde4 file in my home directory.
I think the main package is **qtcurve**, which should pull its dependencies (gtk2-engines-qtcurve, kwin-style-qtcurve, kde-style-qtcurve). You will also want **kcm-gtk** for the actual System Settings module.

I'm not sure if installing **kubuntu-default-settings** makes it pull more dependencies and, for instance, replace your usplash. If you want to avoid installing it, you'll have to make sure you have a **.gtkrc-2.0** file in your home that imports Qtcurve's. (I'll update this post in a bit with example content.)

I *imagine* that the .gtkrc-2.0**_-kde4_** naming theme is to stop GNOME from using the file. Do correct me if I'm wrong, but I wager a .gtkrc-2.0 file is automatically imported, much like a .fonts.conf file is. Appending **-kde4** to the file would thus stop it from being imported, *unless* there's a startup script in **~/.kde/env/** explicitly refering to it - which there is on a default Kubuntu installation.



**edit:** Right, so I completely forgot about updating this post. By default, **~/.gtkrc-2.0-kde4** has the following content, obviously pointing to QtCurve.
```
include "/usr/share/themes/QtCurve/gtk-2.0/gtkrc"
```
And on a standard Kubuntu installation, you have a script in **~/.kde/env/** that exports it, as it would probably only be otherwise read by GTK apps _*if*_ it had not had **-kde4** appended to it.
```
$ cat ~/.kde/env/gtk2-engines-qtcurve.rc.sh
#!/bin/bash

[B]# Make sure our customised gtkrc file is loaded.
export GTK2_RC_FILES=$HOME/.gtkrc-2.0-kde4[/B]
```
This way, you won't get a KDE-y GTK theme when in non-KDE environments like GNOME, as then the startup script wouldn't be run. Again and as lovinglinux mentioned above, renaming it to **.gtkrc-2.0** makes GTK apps read it automatically, but then it won't be a KDE4-specific theming per se, as it will be read in all environments instead of those that just read the **~/.kde/env/** script file (ergo, KDE4).

The same **gtk2-engines-qtcurve.rc.sh** script can be found in **/usr/share/kubuntu-default-settings/**, along with the base copy of **.gtkrc-2.0-kde4** (there named **dot-gtkrc-2.0-kde4**).

Hence why I advocate installing **kubuntu-default-settings**. apt-cache tells me it only depends on python, too. I am, however, unsure at what point the .gtkrc-2.0-kde4 file and the gtk2-engines-qtcurve.rc.sh script gets copied into users' home directories.

---

### Post by sccolbert on 2009-11-23
I haven't like the last two releases of Kubuntu (8.10 & 9.04), but this version is really good. 
It has a few minor bugs, but none of the show stoppers previously mentioned. (those are user errors). 

You will find that KDE is infinitely more configurable than gnome, and thus the default config might not be suitable for everyone. 

For example:

"Amarok hogs my audio hardware!"
Solution: Tell Amarok to use PulseAudio instead of HDA Intel (or whatever your default it) (under the Amarok settings -> playback -> config)

"Dolphin leaves .directories!"
Solution: So does Nautilus! Use alt + . in dolphin to toggle the hidden directory display. 


This version of Kubuntu is solid. And given that Suse/YAST couldnt install the nvidia driver without borking my system, I would say it's even more reliable than most of the other "well known" kde distros....

---

### Post by mvalviar on 2009-11-24
> **sccolbert said:**
> I haven't like the last two releases of Kubuntu 
"Dolphin leaves .directories!"
Solution: So does Nautilus! Use alt + . in dolphin to toggle the hidden directory display. 


I don't remember nautilus ever leaving .directory files.

---

