---
title: "Configuring keyboard layout in xorg.conf"
date: 2009-06-20
forum: General Help
---

### Post by minaev on 2009-06-20
Last week, I installed 9.04 for the first time. My first move was to change the keyboard layout. So, what do I find when I open xorg.conf? Next to nothing. I'm totally stupefied. Where do I set up the keyboard layout if I don't use Gnome or anything like this? 

I've read something about HAL being responsible for the configuration of X11 now, but isn't it totally anti-Occamic to introduce a heap of new useless packages when the others worked well? OK, let it be HAL. Why can't it take the configuration from good old xorg.conf?

I feel the growing non-Linuxness of Ubuntu somehow feels repulsive after many years of using this system :(.

---

### Post by coffeecat on 2009-06-20
> **minaev said:**
> I feel the growing non-Linuxness of Ubuntu somehow feels repulsive after many years of using this system :(.

In fact the opposite is the case. These changes are upstream ones, not Ubuntu ones. The empty xorg.conf is a feature of newer versions of the xserver which can now autodetect most hardware and for much of the time doesn't need a configuration file. Fedora has been ahead of Ubuntu in this respect.

Personally I prefer to set the keyboard layout in the GUI utilities that gnome and KDE provide, but you can still configure keyboard layout in xorg.conf if you want. If there are entries in xorg.conf they will be read as the xserver starts up.

---

### Post by minaev on 2009-06-20
> **coffeecat said:**
> In fact the opposite is the case. These changes are upstream ones, not Ubuntu ones.
Well, it may be the unUnixness of Linux as well :).
> The empty xorg.conf is a feature of newer versions of the xserver which can now autodetect most hardware and for much of the time doesn't need a configuration file.
I really doubt that the keyboard layout is something that can be autodetected ;)
> Personally I prefer to set the keyboard layout in the GUI utilities that gnome and KDE provide
I wouldn't mind doing so, but the customizations I make in Gnome work only under Gnome. So, the keyboard properties are loaded only after I run `gnome-keyboard-properties' in my mostly Gnomeless environment.
> but you can still configure keyboard layout in xorg.conf if you want. If there are entries in xorg.conf they will be read as the xserver starts up.
For some reason, they are not :(. Here's a part of my xorg.conf:

```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us,ru"
        Option          "XkbVariant"    ",winkeys"
        Option          "XkbOption"     "grp:toggle,ctrl:nocaps,grp_led:caps"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
EndSection
```

---

### Post by VCoolio on 2009-06-20
Don't know if this is what you are after, but you can use the setxkbmap command, e.g. "setxkbmap us_intl" or specify things in a config file and point setxkbmap to it. Run "man setxkbmap" to learn more.

---

### Post by minaev on 2009-06-21
VCoolio,

Thanks, I'll have a look at setxkbmap.

Anyway, I'm still disappointed by the direction taken by Ubuntu. Things that worked, are now broken, and the new features only work under certain prerequisites, of which the useless desktop environments are the most annoying.

---

### Post by coffeecat on 2009-06-21
> **minaev said:**
>  of which the useless desktop environments are the most annoying.

Useless desktop environments, eh? On the contrary, some of us find GUI desktops quite useful. :p Is it that you prefer working in the console? Or are you using one of the minimalist desktops? Please explain, because if you don't want to use gnome, KDE or Xfce then Ubuntu is not for you. That's no criticism of either Ubuntu or you, just the way it is.

There's an expression here in the English-speaking world: "horses for courses". Is there a Russian equivalent? Are you riding the wrong horse by using Ubuntu?

---

### Post by minaev on 2009-06-21
> **coffeecat said:**
> Useless desktop environments, eh? On the contrary, some of us find GUI desktops quite useful. :p Is it that you prefer working in the console? Or are you using one of the minimalist desktops?
The latter. I am deeply convinced that the WMs must be scriptable and I like tiling WMs. So, now it's StumpWM.

Desktops make certain configuration tasks easier, but how many users understand what's happening under the hood? For me, it's important.
> Please explain, because if you don't want to use gnome, KDE or Xfce then Ubuntu is not for you. That's no criticism of either Ubuntu or you, just the way it is.
There's an expression here in the English-speaking world: "horses for courses". Is there a Russian equivalent? Are you riding the wrong horse by using Ubuntu?
[/me sighs] I can't recall a Russian analog to this idiom (there must be something similar, I think), but I see what you mean. Until recently I used Hardy Heron. It took some hassle to make things work as I wanted them to, but finally I succeeded. I just hoped the things didn't get even more difficult in the new releases. But they did :). I'd rather find a distro that I could cooperate with, not fight with.

My first Linux was Slackware about 13 years ago. Then I learned about the package managers and Red Hat made my life easier. Later, Red Hat released Fedora and I found Yum. It was great, because it could track and automatically fix the dependencies, but it was too resource-heavy. Here comes Debian. It was almost perfect for the first years. Then I had more packages from backports than from the stable repo. 

Ubuntu was a great compromise between stable Debian and Sid. But only as long as it retained the conservative features of Debian. Now, I'm afraid, it's getting too avant-garde for me. Feels like I can't control my system anymore. Is it time to get real and forget that geeky habit? Or is it time to learn the new unnecessary features? Or to retire :)...

---

### Post by coffeecat on 2009-06-21
Have you thought about trying either Gentoo or Arch? Both have excellent command-line package managers and both give much more control to the user to configure the underlying OS. I used Gentoo as my primary OS for about 18 months and learnt a lot in the process.

The problem (for you) is that the issue you started the thread with - the empty or near-empty xorg.conf - is a reflection of the way development on the xserver is going, so you're going to get this in Gentoo, Slack, Arch and other distros as well.

> **minaev said:**
> Is it time to get real and forget that geeky habit? Or is it time to learn the new unnecessary features? Or to retire :)...

Well, I am retired. Yes, I am that old. :( That's partly why I've given up Gentoo and come back to Ubuntu. My brain is becoming too creaky for all that exercise. :p At my age I appreciate the simplicity of gnome.

Good luck!

---

### Post by minaev on 2009-06-23
So, the problem with the keyboard is solved. Add the following line to the ServerLayout section of xorg.conf (not the empty one, generated by Ubuntu installer, but a real one, with sections describing devices, monitor and screen):

```
Option "AutoAddDevices" "false"
```

This line turns HAL off and the things become much more simple :).

---

### Post by frederickjh on 2010-02-07
> **minaev said:**
> So, the problem with the keyboard is solved. Add the following line to the ServerLayout section of xorg.conf (not the empty one, generated by Ubuntu installer, but a real one, with sections describing devices, monitor and screen):

```
Option "AutoAddDevices" "false"
```

This line turns HAL off and the things become much more simple :).

You can actually do the same thing in the HAL configuration files that you are doing by turning HAL off and using the xorg configuration files. I figured this out when HAL did not auto detect hardware properly and I was then able to also move my custom xorg options to hal's config files.

See my post #11 in this thread for more information.

[http://ubuntuforums.org/showthread.php?t=1378715&page=2]("http://ubuntuforums.org/showthread.php?t=1378715&page=2")

I hope this helps someone that is looking for this information.

Frederick

---

