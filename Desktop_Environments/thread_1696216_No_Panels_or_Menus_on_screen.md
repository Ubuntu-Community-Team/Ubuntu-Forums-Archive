---
title: "No Panels or Menus on screen"
date: 2011-02-27
forum: Desktop Environments
---

### Post by gazza_roberts on 2011-02-27
Hello there

I have a problem with Ubuntu 10.04. I was using update manager this morning and when I restarted (as required by the system) there are no longer any panels or icons on the desktop.

I can open a terminal and other apps with ALT-F2 but I''m not sure what to run to get my desktop back

Thanks 

Gary

---

### Post by Frogs Hair on 2011-02-27
Hi and Welcome 

Try Alt + F2 and run nautilus.

---

### Post by Krytarik on 2011-02-27
What video card/chip do you have, what drivers are you running?

Background: I have a Nvidia card and need to have the following option in the "Screen" section of my "/etc/X11/xorg.conf", otherwise I also have either no panels, no desktop, or both:
```
Option         "AddARGBGLXVisuals" "True"
```

---

### Post by gazza_roberts on 2011-02-27
> **Frogs Hair said:**
> Hi and Welcome 

Try Alt + F2 and run nautilus.

Thanks Frogs Hair

I'll try this when I get home later

---

### Post by IWantFroyo on 2011-02-27
<Ctrl><Alt><T>
```
gconftool-2 – -shutdown
gconftool – -recursive-unset /apps/panel
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```
Good luck!

---

### Post by gazza_roberts on 2011-02-28
> **IWantFroyo said:**
> <Ctrl><Alt><T>
```
gconftool-2 – -shutdown
gconftool – -recursive-unset /apps/panel
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```Good luck!

IWantFroyo you are a GENIUS!!! 
If I had Froyo you could have it...:popcorn:
Your advice worked PERFECTLY.  

If anyone else is reading this thread and they're as new as me to Linux then perhaps this will help you enter the commands from IWantFroyo

<Ctrl><Alt><T> opens a terminal window. 
You can type the long dashes with --
You may need to logon as root to execute ps kill gnome-panel
Do this by typing su then the root password for the system.

Thanks again guys for all your help. I have had a similar problem with PCLinuxOS and spent so long messing with X11 config files that I gave up in the end and just reinstalled.

---

### Post by coljohnhannibalsmith on 2011-02-28
Hello,

I had a similar problem and came-up with a different solution:

See Below:

[http://ubuntuforums.org/showthread.php?t=1664899](http://ubuntuforums.org/showthread.php?t=1664899)

---

### Post by gazza_roberts on 2011-02-28
Thanks Hannibal

I''ll print out your thread and this one as I have a feeling I may need them. 

You're definitely right with:
*"It's unfortunate and strange that the file that holds this setting  somehow gets corrupted.  This feature needs some kind of 'failsafe,' as  this bug will render your system unusable!"*

Display issues have been the only problem that I've had with Linux too. I guess the geniuses who develop the system will fix this over time.

Cheers

---

### Post by Krytarik on 2011-02-28
I hope it is really fixed, because I could always get my panels/desktop back by simply restarting them, but after the next login they were gone again. And your initial post indicated no corruption of your panels/desktop config.

---

### Post by gazza_roberts on 2011-03-01
> **Krytarik said:**
> I hope it is really fixed, because I could always get my panels/desktop back by simply restarting them, but after the next login they were gone again. And your initial post indicated no corruption of your panels/desktop config.

Hi Krytarik

You are right - the panels disappear when I shutdown. Still, at least I can get them back now. I don't want to mess with X11 as this has broken my system altogether a few time sin the past. I think I'll re-install when I get time. Thanks for your help

Gazza

---

### Post by Krytarik on 2011-03-01
> **gazza_roberts said:**
> I think I'll re-install when I get time.
That doesn't necessarily fix the issue also. ;-)

---

### Post by worksofcraft on 2011-03-01
Like the OP here, without any apparent cause suddenly my computer also stopped displaying the main panel that by default is at the top of the screen and it has happened before too.

I followed the instructions below and they seem to have set up the original default panel settings again.

> **IWantFroyo said:**
> <Ctrl><Alt><T>
```
gconftool-2 &#8211; -shutdown
gconftool &#8211; -recursive-unset /apps/panel
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```
Good luck!


However I'm **not happy** with this solution at all: I can't remember how to recreate all my settings. For instance how to put Google Chrome back on the menu and countless other things. The use of "rm -rf" there I assume has **irrevokably anihilated** any files I might have been able to use to restore them.

Can anyone suggest what I can do to get my application menus back?

Note: As these disappearing panels is evidently quite a common problem with gnome desktop IMO they should consider creating backups. Even simply identifying the files involved would be preferable to hiding them in hidden folders IMO :P


p.s. and I know a lot of people think it isn't very important, but I happen to be in emergency and potentially life threatening post Earth quake conditions here with many essential services cut off. I wanted to use my computer to find the nearest operational medical center.

Dependable internet access is essential and the bad timing and unreliability of something stupid like this is enough to make me consider ditching the whole Ubuntu thing for good.

---

### Post by Krytarik on 2011-03-01
Those posted method is indeed a real brute-force one, even doublicatly removal, and shouldn't be used unless simply restarting the panel doesn't work.

To just restart gnome-panel:
- press Cltr+Alt+t to get a terminal
- enter "killall gnome-panel"

To restart nautilus, just to be said:
- press Cltr+Alt+t to get a terminal
- enter "killall nautilus"

EDIT: To identify potential issues related to the failure to start gnome-panel take a look into "~/.xsession-errors".

---

### Post by worksofcraft on 2011-03-01
> **Krytarik said:**
> 
EDIT: To identify potential issues related to the failure to start gnome-panel take a look into "~/.xsession-errors".


IDK if the following means anything to anyone but this is what it says in there:

```

** (<unknown>:1289): DEBUG: Client registered with session manager: /org/gnome/SessionManager/Client2

(polkit-gnome-authentication-agent-1:1331): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:1331): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
Starting gtk-window-decorator
Initializing nautilus-gdu extension
Initializing nautilus-open-terminal extension
I/O warning : failed to load external entity "/home/cjs/.compiz/session/10dd3a6e1fc2f670c129900225454965700000012010031"

(gnome-settings-daemon:1298): GLib-GObject-WARNING **: IA__g_object_notify: object class `GkbdStatus' has no property named `name'
Unable to find a synaptics device.
** (update-notifier:1686): DEBUG: Skipping reboot required

```

---

### Post by Krytarik on 2011-03-01
> **worksofcraft said:**
> IDK if the following means anything to anyone but this is what it says in there:

No, not really.

---

### Post by worksofcraft on 2011-03-01
> **Krytarik said:**
> No, not really.

lol you know once I have my computer working the way I want it again I'm going to permanently disable all updates and remove write access from all configuration files.

here is the latest one:
```

$ google-chrome
[1837:1837:334273923:ERROR:base/native_library_linux.cc(32)] dlopen failed when trying to open libGLESv2.so: libGLESv2.so: cannot open shared object file: No such file or directory

```

If it doesn't work with those settings I will be buying windows 7

---

### Post by Krytarik on 2011-03-01
> **worksofcraft said:**
> lol you know once I have my computer working the way I want it again I'm going to permanently disable all updates and remove write access from all configuration files.LOL, Yeah, may help sometimes.:P
> **worksofcraft said:**
> 
here is the latest one:
```

$ google-chrome
[1837:1837:334273923:ERROR:base/native_library_linux.cc(32)] dlopen failed when trying to open libGLESv2.so: libGLESv2.so: cannot open shared object file: No such file or directory

```If it doesn't work with those settings I will be buying windows 7
Yeah, buy, sure.;)

Does Chrome not start because of this error? You may try Chromium instead, though some people say, it is more unstable.

---

### Post by The Linux Cynic on 2011-03-02
@worksofcraft

I suggest you learn how to use the commandline instead of throwing the whole thing out just because a single gnome bug may happen. There are lots of things that can go wrong with Windows7 as well, and I think you'll find there are fewer recourses should something get cocked up.

If you really want to be prepared, you need to know more than one way to do things. Start here: [http://linuxcommand.org/]("http://linuxcommand.org/")

---

### Post by worksofcraft on 2011-03-02
> **The Linux Cynic said:**
> @worksofcraft

I suggest you learn how to use the commandline instead of throwing the whole thing out just because a single gnome bug may happen. There are lots of things that can go wrong with Windows7 as well, and I think you'll find there are fewer recourses should something get cocked up.

If you really want to be prepared, you need to know more than one way to do things. Start here: [http://linuxcommand.org/]("http://linuxcommand.org/")

I know how to use the command line. It is not the type of user interface that is appropriate for computers in the 21st century.

It is unacceptable to be dependent on a system which loses it's settings in such a way that it actually became a potentially life threatening situation in an emergency.

When I make **no** changes to these settings, there is no excuse for a machine not to start up the same way every time.
Hidden folders of unidentified files that are being written to and corrupted for no apparent reason doesn't seem to me like a particularly desirable design.

---

### Post by Copper Bezel on 2011-03-02
No, there really isn't. Krytarik, since you've experienced this before, do you have any idea what caused it? It can't be normal.

worksofcraft, since you obviously don't have the time to dink with these settings and need a dependable interface, I'd recommend switching to Unity (which doesn't depend on Gnome Panel or, as I understand it, x-nautilus-desktop.)

---

### Post by Krytarik on 2011-03-02
There are a number of things which can cause the panels to not come at startup:

- Anything faulty in the panels itself: This is usually logged into .xsession-errors, we did check that, that's not the case.

- It can be video driver/options related, like in my case: Therefore we need more information about the video card and the running driver. But I don't think it's wise to even start tinkering with the video driver in this very situation.

- It could be a faulty session configuration, check that: [http://ubuntuforums.org/showthread.php?t=1682949](http://ubuntuforums.org/showthread.php?t=1682949)

What I really like to know is if the panels come up when restarting gnome-panel in the way I described.

And, honestly, I don't recommend installing another DE in this very situation either. If the panels can be brought up in the described way, I would simply add a launcher to "Startup Applications" temporarily.

---

### Post by Copper Bezel on 2011-03-03
If the simpler, non-nuclear command will bring the panel back, sure, that would be an easy fix.

And yes, recommending another DE would be very silly. = ) That's why I suggested Unity, which is a Compiz plugin that runs Gnome with a slightly different set of services and, relevant to this case, a panel that depends on a different set of config files. = )

---

### Post by NykO18 on 2011-03-03
> **gazza_roberts said:**
> I have a problem with Ubuntu 10.04. I was using update manager this morning and when I restarted (as required by the system) there are no longer any panels or icons on the desktop.

The keyword here is 'restarted'. I had the same problem this morning after rebooting and started blaming Linux for doing stupid stuff behind my back. Then I realized it was the first time I rebooted since two weeks or so and I remembered uninstalling the evolution mail panel indicator a few days ago (not using evolution, this is quite useless).

Next thing you know, The Ubuntu Software Center sure uninstalled the evolution mail panel indicator and with it, the whole Ubuntu Desktop package. Nice move Ubuntu, didn't even told me that it would delete this whole package as a dependency. So yeah, a simple aptitude install ubuntu-desktop solved it for me. Do not remove all your preferences like IWantFroyo is suggesting.

---

### Post by Krytarik on 2011-03-03
> **Copper Bezel said:**
> 
And yes, recommending another DE would be very silly. = ) That's why I suggested Unity, which is a Compiz plugin that runs Gnome with a slightly different set of services and, relevant to this case, a panel that depends on a different set of config files. = )
So, may be my fault then. If so, sorry! I thought Unity goes hand-in-hand with the Netbook Edition. I have to do some research on it, and a trial, when I have the time.

Btw., "non-nuclear", adequate term. LOL

---

### Post by Copper Bezel on 2011-03-03
Yeah, let's just hope that that command works. = )

And yeah, on Unity, it's getting a lot of press because of the unusual (but useful) layout and its relative lack of configurability, and it's getting branded as a DE because of Canonical's marketing and because it shows as a separate DE in Session (which it has to because of the difference in services) but it's very much a simple panel alternative. In retrospect, I guess it would have been simpler to suggest using Unity-2D, which is just the panel and can be called in a normal Gnome session, and even that would be a third option in terms of long-term workability, after working with the panel to simply fix the problem or trying a straight panel alternative like Cairo or Avant. The OP's last post just conveyed a sense of urgency about getting things working *now *with little or no configuration, yes?

---

### Post by Krytarik on 2011-03-04
Thanks for the info about Unity, and sorry for answering that late, I was working on a theme since yesterday night and I always look straight then. ;-)
> **Copper Bezel said:**
> The OP's last post just conveyed a sense of urgency about getting things working *now *with little or no configuration, yes?
Aside from the fact that *worksofcraft* isn't the OP, I can really understand that mood. It's really unfortunate to have the panels disappear while you are in a earth quake desaster zone. But it would also be great if one tries a given possible at least temporary solution, instead of keeping to say that it is unacceptable that the system has an error/misconfiguration without any order. ;-)

---

### Post by Copper Bezel on 2011-03-04
Oh, they totally aren't the same guy. I feel very silly. Sorry!

[QUOTE=krytarik]But it would also be great if one tries a given possible at least temporary solution, instead of keeping to say that it is unacceptable that the system has an error/misconfiguration without any order.[/QUOTE]

Yes, I agree, productive discussion is more productive. = )

---

