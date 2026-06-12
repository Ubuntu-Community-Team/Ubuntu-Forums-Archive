---
title: "Minimal Ubuntu"
date: 2009-06-24
forum: Desktop Environments
---

### Post by atomicpookavirus on 2009-06-24
Greeting Ubuntuers!
I've just installed minimal ubuntu with IceWm on an old notebook and it's real snappy, now I'm wondering what other programs to use with it. First of all, how do I connect to my wifi?

---

### Post by kerry_s on 2009-06-24
> First of all, how do I connect to my wifi? 

how do you want to connect? cli, manager, script, ?

most people will use a manager> **sudo apt-get install wicd**

but i don't want the bloat of a slow manager so
on mine i use /etc/network/interfaces for the main connection & i also have a gui for when i switch or use an open connection.

---

### Post by atomicpookavirus on 2009-06-24
interesting
can you link to any guides on configuring the /etc/network/interfaces file?

Edit:
I just discovered man interfaces! :shock:

---

### Post by kerry_s on 2009-06-24
this is what i use:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
allow-hotplug eth0
iface eth0 inet dhcp

# The wireless network
allow-hotplug wlan0
iface wlan0 inet dhcp
wireless-mode managed
wireless-essid newday
wireless-rate 54M
wireless-key open

```

the gui i use is called "network-config" its in the repo> **sudo apt-get install network-config**

you have to create a launcher for it> **gksudo network-config**

i use just 2, 1 for wired & 1 for wireless, cause i may use 1 or the other, but you can set as many profiles as you want.
looks like this:

---

### Post by atomicpookavirus on 2009-06-24
It works now. I have WPA2 network all set up from /etc/network/interfaces file.
Only snag was copy the hexadecimal key (converted from plain text) off the command line and into leafpad by hand.

Is there a way to enable copy/paste with the terminal?

---

### Post by philcamlin on 2009-06-24
right click copy paste cut...

---

### Post by kerry_s on 2009-06-24
> **atomicpookavirus said:**
> It works now. I have WPA2 network all set up from /etc/network/interfaces file.
Only snag was copy the hexadecimal key (converted from plain text) off the command line and into leafpad by hand.

Is there a way to enable copy/paste with the terminal?

since your minimal i'm going to assume you mean xterm.
left click hold & drag to highlight, paste is middle click.
works the same way in the terminal it self.

---

### Post by kerry_s on 2009-06-24
> **philcamlin said:**
> right click copy paste cut...

only works if your using a heavy terminal.

---

### Post by atomicpookavirus on 2009-06-24
I can copy/paste from xterm to xterm and copy/paste from leafpad to xterm but I can't copy text out of xterm to leafpad or firefox.

---

### Post by kerry_s on 2009-06-25
> **atomicpookavirus said:**
> I can copy/paste from xterm to xterm and copy/paste from leafpad to xterm but I can't copy text out of xterm to leafpad or firefox.

thats weird, works just fine for me.
is the stuff in the xterm still highlighted when you trying to paste?

---

### Post by Henrike Corinna on 2009-06-25
I'm using Ubuntu as an alternative operating system on my laptop, part of a dual boot, but it won't look at the wireless card inbuilt into my computer. Could anyone recommend a usb wireless adapter that will work out of the box with minimal or no extra configuration? Any help is much appreciated, thanks.

---

### Post by atomicpookavirus on 2009-06-25
:popcorn: I was getting ready to take a screencap showing that the xterm clipboard wouldn't over write to leafpad when it sudden;y started working. Very bizarre.

Now to figure out how to customize xterm...

---

### Post by kerry_s on 2009-06-25
> **atomicpookavirus said:**
> :popcorn: I was getting ready to take a screencap showing that the xterm clipboard wouldn't over write to leafpad when it sudden;y started working. Very bizarre.

Now to figure out how to customize xterm...

what is it you want to customize?

i'm helping another with fonts and colors here:
[http://ubuntuforums.org/showthread.php?p=7513724#post7513724](http://ubuntuforums.org/showthread.php?p=7513724#post7513724)

---

### Post by atomicpookavirus on 2009-06-25
Excellent. The text is now a readable size and the colors are spiffy.

My next project is compiling awsome 3.3.1.
I'm trying to hunt down all the dependencies.
I've gotten the errors in make down to
[COLOR=Red]
-- package 'libstartup-notification-1.0>=0.10' not found[/COLOR]
Edit: it's just down to libstartup now.

-- package 'xproto>=7.0.15' not found
-- package 'libdxdg-basedir>=1.0.0' not found

also, copying from the terminal no longer works :o

---

### Post by kerry_s on 2009-06-25
> **atomicpookavirus said:**
> Excellent. The text is now a readable size and the colors are spiffy.

My next project is compiling awsome 3.3.1.
I'm trying to hunt down all the dependencies.
I've gotten the errors in make down to
[COLOR=Red]
-- package 'libstartup-notification-1.0>=0.10' not found[/COLOR]
Edit: it's just down to libstartup now.

-- package 'xproto>=7.0.15' not found
-- package 'libdxdg-basedir>=1.0.0' not found

also, copying from the terminal no longer works :o

yeah, why are you compiling when its in the repos.(**sudo apt-get install awesome**)
going outside the repos can cause problems, so i'm not surprised stuff is breaking.

---

### Post by atomicpookavirus on 2009-06-25
I just discovered that there are two separate clipboards. One is accessed by ctrl+v and the other is accessed by middle click.

I had wanted to compile awesome so that I could use the latest version. I suppose I will to use the one in the repos for now though, seeing as I can't find [COLOR=Black]libstartup-notification-1.0 anywhere. What allows you to type s awesome to search for the package? That looks extremely useful.

Edit:
I found this blog post -- [link]("http://www.tychoish.com/2009/05/new-awesome/")
[/COLOR]> I've been (slowly) upgrading to the latest version of the [Awesome Window Manager]("http://awesome.naquadah.org/"). Since Awesome is a pretty new program, and there was a debian code freeze during development for a huge chunk of the awesome3-series code... it's been hard to install on ubuntu. Lots of dithering about, and then compiling by hand. For the uninitiated, ususally installing new software on a Debain-based system (like ubuntu; and many GNU/Linux systems are this way) is as simple as typing a single command. This hasn't really been the case for awesome.
  In any case, with the latest release candidates for awesome 3.3 in sid (debian unstable) I added a sid repository to my ubuntu system, updated, installed awesome, removed the sid repository. Breathed a huge sigh of relief, and then got to getting things setup again. I have the following responses to the new awesome:
  
[LIST]
[*]I really like the fact that if you change something in your config file and it doesn't parse, awesome loads the default config (at /etc/xdg/awesome/rc.lua) so that you don't have to kill X11 manually and fix your config file from a virtual terminal.
[*]If you're considering awesome, and all this talk of unstable repositories scares you, the truth is that awesome is--at this point--not exactly adding new features to the core code base. There are some new features and reorganizations of the code, but the software is generally getting more and more stable. Also, the config file has been (and is becoming less of) a moving target, so given that it's pretty stable and usable, it makes sense to "buy in" with the most current version of the configuration so you'll have less tweaking in general.
[*]The new (default) config file is so much better than the old ones. I basically reimplemented my old config into the new default config and have been really happy with that. It's short(er) and just yummy.
[*]I did have some sort of perverse problems with xmodmap which I can't really explain but they're solved.
[*]If you're use a display manager (like gdm) to manage your x sessions, I know you *can* just choose awesome from the default sessions list, but I'd still recommend triggering awesome from an .xinit/.Xsessions file so that you can load network managers and xmodmap before awesome loads. Which seems to work best for me.
[*]I'd never used naughty, which is a [growl]("http://www.growl.info/")-like notification system before, and now that it's included by default I am using it, and I quite adore it.
[/LIST]


The same procedure worked well for me too.

---

### Post by kerry_s on 2009-06-26
>  What allows you to type s awesome to search for the package? 

it's a alias. you can set them in ~/.bashrc, i use:

```

alias !='sudo'
alias u='sudo apt-get update;sudo apt-get upgrade'
alias s='apt-cache search'
alias i='sudo apt-get install' 
alias r='sudo apt-get remove --purge'
alias ?='dpkg -l | grep'
alias c='sudo apt-get clean'
alias ch='clear;rm ~/.bash_history;history -c'
alias grep='grep --color'

```

---

