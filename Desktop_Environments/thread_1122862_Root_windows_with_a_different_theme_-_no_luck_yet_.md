---
title: "Root windows with a different theme - no luck yet :("
date: 2009-04-11
forum: Desktop Environments
---

### Post by cfogelberg on 2009-04-11
[aka "Why doesn't root read /root/.themes for its theme??]

Hello all,

I've been configuring the Jaunty beta on my Dell XPS M1330, and I've been trying to get windows that have root privileges (e.g. "gksudo gedit ..." to have a different theme.

I haven't been successful so far. There's quite a lot of material already on the internet, but it seems to be dated and does not work with GDM 2.20.10 (what I currently have installed).

This and related material includes:
* [http://lifehacker.com/software/linux-tip/re+theme-your-sudo-applications-263153.php#viewcomments]("http://lifehacker.com/software/linux-tip/re+theme-your-sudo-applications-263153.php#viewcomments")
* [http://www.linuxquestions.org/questions/ubuntu-63/where-does-ubuntu-store-user-set-theme-555478/]("http://www.linuxquestions.org/questions/ubuntu-63/where-does-ubuntu-store-user-set-theme-555478/")

Potentially incredibly useful, and linked to by the second link, above:
* [http://developer.gnome.org/doc/whitepapers/SystemConfig/index.html]("http://developer.gnome.org/doc/whitepapers/SystemConfig/index.html")
Unfortunately the Theme Configuration page hasn't been written yet :( :( :(

Now things take an exploratory turn. I've discovered that custom themes are saved to ~/.themes. So:
* I created a modified theme "Human-RootForRed" with a red window background (#ff332f) using gnome-appearance-properties (#ff332f).
* This appeared in ~/.themes. I also copied it to /root/.themes.
* I edited the file in ~/.theme so that it's window background was #efebe6 (one bit different from Human, #efebe7).

Unfortunately, when I do gksudo gedit I don't get the bright red background I see when the theme folder that is now in /root/.themes. Instead I see the Human-like tone #efebe6, and I guess it's being read from ~/.themes. Huh? It seems like root isn't reading its theme information from /root/.themes?

If anyone knows what's going on or has any ideas please let me know! I'm keen to crack this one and feel like I'm getting close...

Thanks,
Christo

---

### Post by djbushido on 2009-04-11
Root doesn't have a .themes because you don't run gdm, X, or anything else as root. You would have to make a root account, possible only in another distro. Look up Ubuntu's su philosophy for a more detailed account, but as far as I know, this isn't possible. Could be wrong, but I doubt it.
Also, root probably is reading ~/.themes because that's where X/GDM/GNOME is pointing to because there is no "root" user.
If you absolutely have to have this, try out Debian.

---

### Post by cfogelberg on 2009-04-11
Hello,

Yes, I may have been led astray because root already had a .themes directory before I did anything. Unfortunately the output of "sudo env" makes me thing you're right:

```
[2129][christo@christo-lt2 ~/bin]
$ sudo env
[sudo] password for christo: 
TERM=xterm
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin
LANG=en_GB.UTF-8
HOME=/home/christo
DISPLAY=:0.0
XAUTHORITY=/home/christo/.Xauthority
COLORTERM=gnome-terminal
SHELL=/bin/bash
LOGNAME=root
USER=root
USERNAME=root
SUDO_COMMAND=/usr/bin/env
SUDO_USER=christo
SUDO_UID=1000
```

For a while there I was hoping I could write some sort of wrapper script around gksudo, but then I realised that would probably change the theme of every window. Changing the theme of just one window could be a lot more difficult and I'm not sure how to start. Unless anyone else has a genius idea up their sleeve I might have to shelve this project for the time being...

Christo

---

### Post by djbushido on 2009-04-11
Sorry to put a damper on your plans, but since there is no "root" account in Ubuntu, I'm pretty sure it is not possible.

---

### Post by Darkshade on 2009-04-11
Move your themes to /usr/share/themes/ and icons to /usr/share/icons/. You'll still be able to change them trough the appearance settings menu but they'll also apply to root windows as synaptic.

---

### Post by Zoowey on 2009-04-11
Use the instructions from this website [http://tombuntu.com/index.php/2007/09/18/theme-applications-running-as-root-in-ubuntu/](http://tombuntu.com/index.php/2007/09/18/theme-applications-running-as-root-in-ubuntu/) to make all root applications use your normal theme. The thing with Ubuntu is it does in fact have a root account but it is hidden.

---

### Post by cfogelberg on 2009-04-12
> **Darkshade said:**
> Move your themes to /usr/share/themes/ and icons to /usr/share/icons/. You'll still be able to change them trough the appearance settings menu but they'll also apply to root windows as synaptic.

Hi there,

Yes. I can modify how the theme displays for root, or set root to use any theme I like, but then my non-root user also uses that theme, and that's not quite what I'm trying to do :)

What I'm trying to do is theme windows with root privileges differently than windows without. I.e. if I have a gedit window with root privileges open I want it to have a red background, but I want the firefox window I have open at the same time to have a normal (and different) window background colour.

Best,
Christo

---

### Post by cfogelberg on 2009-04-12
> **Zoowey said:**
> Use the instructions from this website [http://tombuntu.com/index.php/2007/09/18/theme-applications-running-as-root-in-ubuntu/](http://tombuntu.com/index.php/2007/09/18/theme-applications-running-as-root-in-ubuntu/) to make all root applications use your normal theme. The thing with Ubuntu is it does in fact have a root account but it is hidden.

Hi there,

The problem I have is that root seems to ignore the information in /root/.themes - e.g. if I have Human-RootWithRed in ~/.themes and /root/.themes, but the files describing them are different then it makes no difference: root still seems to use the theme described in ~/.themes and ignores what's in /root/.themes.

EDIT FOR CLARITY: I mean that there is a theme with the same name in /root/.themes and ~/.themes, but that the files which describe this theme in the respective directories are different (e.g. specify a different window background colour). The themes have to have the same name as there doesn't seem to be a way to pick the theme based on uid, at least not an easy or obvious way to a newbie like me!

If you know how to customise this kind of thing (where gdm looks, on a per-window basis, based on uid or something) please let me know! :)

Best,
Christo

---

### Post by Zoowey on 2009-04-13
> **cfogelberg said:**
> Hi there,

Yes. I can modify how the theme displays for root, or set root to use any theme I like, but then my non-root user also uses that theme, and that's not quite what I'm trying to do :)

What I'm trying to do is theme windows with root privileges differently than windows without. I.e. if I have a gedit window with root privileges open I want it to have a red background, but I want the firefox window I have open at the same time to have a normal (and different) window background colour.

Best,
Christo

Oh, I see. So basically you want a SEPARATE theme for root. For example you use the Human theme for your normal non-root windows then some red alert theme for your root windows. I've been trying some things with no luck, I'll update this post when and if I figure something out. Best of luck.

---

### Post by cfogelberg on 2009-04-14
> **Zoowey said:**
> Oh, I see. So basically you want a SEPARATE theme for root. For example you use the Human theme for your normal non-root windows then some red alert theme for your root windows. I've been trying some things with no luck, I'll update this post when and if I figure something out. Best of luck.

Exactly! I want a nice red background or even just a different titlebar, to warn me for when I can really screw my system up :P

I was surprised to learn that GNOME doesn't seem to use $HOME or logname or similar to work out which theme information to use. Now I'm trying to figure out how it does it and hope it is a per-window parameter that can be tweaked by using uid-type information. This is very exploratory for me though as I don't really know what I'm doing in this area!

Best,
Christo

---

### Post by cfogelberg on 2009-04-15
I haven't experimented with this at all yet, but maybe it could be adapted to this problem? (it's in the Jaunty repositories, I just saw it in a "sudo apt-get upgrade" I ran)

[http://ignore-your.tv/fusa/]("http://ignore-your.tv/fusa/")

Christo

---

### Post by thilina on 2011-01-22
Things have become really easy in ubuntu these days. All you have to do is to install Ubuntu tweak and change the roots theme using that. If you need more help, visit this link.

[http://alldtechstuff.blogspot.com/2011/01/change-theme-of-root-user-easily-in.html](http://alldtechstuff.blogspot.com/2011/01/change-theme-of-root-user-easily-in.html)

---

