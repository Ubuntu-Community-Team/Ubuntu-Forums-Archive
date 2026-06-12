---
title: "Various problems with Ubuntu custom install"
date: 2011-10-15
forum: Desktop Environments
---

### Post by abelthorne on 2011-10-15
Hello,
I'm trying to setup a custom Ubuntu install based on Openbox. I started with the alternate CD to install a minimal version (11.10), then installed the basics I needed: X.org + Openbox + video drivers. I end up with a few strange problems that doesn't appear if I use a standard Ubuntu install + Openbox.

1) LOGIN MANAGER
I can't make LightDM to work. The system takes quite a long time to start (I first thought it had hanged) and end on a black screen. LightDM doesn't seem to start at all as I couldn't "blindly" connect. I compared the installed packages with the ones on a standard Ubuntu setup and I don't find differences related to LightDM. Maybe it's a config problem or a package that isn't installed and isn't a dependency of lightdm ?
I currently use Slim (which works, despite a small graphical bug) but would like to use LightDM.

2) NETWORK MANAGER
At first, the network and internet access were fully fonctional. Then, I decided to install Network Manager so that I can use its applet. After that, local network continued to work but I had no internet access. I remembered an old problem with NM and the interfaces file (if a network adapter is declared in /etc/network/interfaces, NM can't see it) and modified the file. After that, internet is functional again but 1) I thought this issue was fixed some time ago, am I wrong? and 2) although all works, the NM applet doesn't see any network device (and is thus unusable).
What do I need to install/setup/tweak in order to use Network Manager and its applet?
**Won't work until Slim is fixed** to handle ConsoleKit correctly.

3) GKSU
I've installed Gksu to run applications as admin (e.g. Synaptic) and it doesn't work. I get an alert asking for my password (with an option to remember it; it doesn't look like the usual passwork-asking alert) and then, nothing happens. When running from a terminal, I don't get any error. I can run apps with sudo but nothing with gksu. Is there something specific to install (like the GNOME keyring or an equivalent)?
**Fixed (kind of):** I installed Evolution and it seems it installed gnome-jeyring. Gksu now works and displays the right password-alert, although I don't understand in what way Gksu is related to the GNOME keyring...

4) SOUND
I have no sound. After installing alsa-base through Quod Libet, alsamixer tells me it can't open the mixer...
**Fixed:** I added myself to the "audio" group. Also, I may have installe libasound2-plugins (not sure it was needed and/or if it was installed with ALSA)

---

### Post by mips on 2011-10-15
> **abelthorne said:**
> Hello,
I'm trying to setup a custom Ubuntu install based on Openbox. I started with the alternate CD to install a minimal version (11.10), then installed the basics I needed: X.org + Openbox + video drivers. I end up with a few strange problems that doesn't appear if I use a standard Ubuntu install + Openbox.

1) LOGIN MANAGER
I can't make LightDM to work. The system takes quite a long time to start (I first thought it had hanged) and end on a black screen. LightDM doesn't seem to start at all as I couldn't "blindly" connect. I compared the installed packages with the ones on a standard Ubuntu setup and I don't find differences related to LightDM. Maybe it's a config problem or a package that isn't installed and isn't a dependency of lightdm ?
I currently use Slim (which works, despite a small graphical bug) but would like to use LightDM.


Have exactly the same issue, cannot get it to work so using gdm for now.

I also have a custom base install with xubuntu-desktop & xubuntu-default settings but does not seem to have done much for applying the default setting to my themes, fonts, panels etc. Pretty ticked off as this should work.

My sound is also dead. Edit: 

Got my sound working by unmuting ALL the channels in alsamixer. Also got the theme issues sorted out.

---

### Post by abelthorne on 2011-10-15
Well, it seems that I don't have sound too. I have installed alsa-base and a few packages (well, I installed Quod Libet, which in turn installed alsa-base and stuff); When running alsamixer, it tells me it can't open the mixer.

(EDIT: fixed, as explained in the original post.)

---

### Post by abelthorne on 2011-10-18
Network-Manager doesn't work, as some other things (like mounting/unmounting drives as user) because Slim doesn't handle ConsoleKit as expected. There seems to be a bug report somewhere but no fix so far.

Currently, I have to use another login manager. As I can't use LightDM, I've currently switched to LXDM.

---

### Post by abelthorne on 2011-10-20
> **mips said:**
> Have exactly the same issue, cannot get it to work so using gdm for now.
I've managed to use LightDM finally. I'm not sure your problem is the same as Xubuntu 11.10 switched to LightDM too and thus should work out of the box if you installed xubuntu-desktop (unless you're still on 11.04 or older?).

Well, not sure about what fixed the problem exactly but here is what I did recently:
- installed plymouth-theme-ubuntu-logo (in case LightDM had issues with the text theme of Plymouth, although I don't think it is the case)
- installed acpi-support and its dependencies
- installed lightdm-gtk-greeter

I edited my /etc/lightdm/lightdm.conf like this:
```
[SeatDefaults]
greeter-session=lightdm-gtk-greeter
user-session=openbox
```

(If you use Xubuntu, user-session should be "xubuntu" instead of "openbox".)

Not sure if the problem came from the greeter used (although I think I tried the Gtk greeter previously), from missing software installed by acpi-support...
The Unity greeter doesn't seem to work although I don't know why.

So, points 1 and 2 are fixed as I don't need Slim anymore and LightDM manages ConsoleKit as expected (so Network manager and other permissions-related stuff works too).

---

### Post by Miscible21 on 2011-11-29
Thanks for posting this. I'm glad you resolved you're issue with lightdm. I was hoping that you could point me in the right direction. Just did a fresh minimal install of Ubuntu 11.10 virtual box. I chose to install Lightdm as my log in manager. When I power the machine up I'm presented with a strange grainy blue screen and no option to login. So now I can't actually get into the virtual machine to correct the problem. Is this similar to what you experienced? How exactly did you work around it?

---

### Post by abelthorne on 2011-11-29
Well, I did an install on my real PC and not a VM, so I could switch to ttys (ctrl + alt + F1) to log in a text session and try things. I'm not sure you can do the same with a VM.

Anyway, the problem I had with LightDM was rather a black screen with the mouse cursor but nothing else : couldn't click anywhere or log in by typing my password, it was kind of stuck.

I worked around the problem by loging in a tty, editing the LightDM config file with Nano and restarting until I it worked.

---

