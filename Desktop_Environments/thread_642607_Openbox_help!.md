---
title: "Openbox help!"
date: 2007-12-16
forum: Desktop Environments
---

### Post by Mr. Electric Wizard on 2007-12-16
I feel like a moron!
So I installed an "alternate" minimal install this afternoon.
Opted for Openbox for desktop manager and Xdm for login.
Well, after successfully logging into Openbox I realized that I do not have a terminal?
The is a right click option for Terminal Emulator but nothing happens.
Is there a way that I can get a terminal going or what?

Please help!

---

### Post by Tenken on 2007-12-16
Install xterm. I believe that is what the openbox menu item points to,

---

### Post by Mr. Electric Wizard on 2007-12-16
Yeah, I figured.
But I'm caught in kind of a catch 22.
I installed Xdm and I didn't install xterm at the time, so I can't get to a terminal and when I turn on the computer it goes straight to xdm.

---

### Post by Tenken on 2007-12-16
When you get to the Xdm login screen hit Ctrl+Alt+F1 to enter a command prompt, login and install xterm that way. Hit Ctrl+Alt+F7 to return to your Xdm screen.

---

### Post by dagnabit dang doohickey on 2007-12-16
The Openbox "Terminal" menu entry points to x-terminal-emulator, which is itself a link that points to whichever terminal its currently set to by the Debian alternatives system. You can change it if you like; check out the update-alternatives manpage. (There's also a gui front-end available: galternatives.) Besides modifying that, if needed or wanted, you can also just edit the Openbox menu. (If not already familiar with it, obmenu makes the task much easier.)
As far as what terminal to install: it's probably a good idea to have xterm installed, but don't stop there. Better terminals are available to choose from: xfce4-terminal, gnome-terminal, urxvt, etc. There's no need to get stuck with xterm as your default terminal.

---

### Post by Mr. Electric Wizard on 2007-12-17
Thanks guys

---

### Post by urukrama on 2007-12-17
Xterm is quite limited. Why don't you try another light terminal -- Sakura, urxvt or xfce4-terminal? 

Also have a look at my [Openbox guide]("http://urukrama.wordpress.com/openbox-guide/"). It might come handy if you are new to Openbox.

---

### Post by DJiNN on 2008-02-10
> **urukrama said:**
> Xterm is quite limited. Why don't you try another light terminal -- Sakura, urxvt or xfce4-terminal? 

Also have a look at my [Openbox guide]("http://urukrama.wordpress.com/openbox-guide/"). It might come handy if you are new to Openbox.

I was doing a search for Sakura & this post came up (& i'm glad that it did) :)

I've just tried to get Sakura compiled & installed onto my Xubuntu (7.10) installation, and after installing a fistful of libs & dependencies, my Xubuntu install no longer works, but boots into Busybox instead! :)  No problems there as i'll just install it again, but i was wondering if you got Sakura compiled & installed on a buntu system? and what you did to accomplish it?  It wouldn't work for me at all & borked my system! 

One more thing..... your OpenBox guide is great. I really like OpenBox but it takes some getting used to (even though i'm used to Fluxbox) and your guide is a BIG help!! +1 you & +1 to the guide. :D

---

### Post by Anzan on 2008-02-12
urukrama, I agree with DJiNN.

I've just installed Openbox and won't have time to start to configure it until next week but I've bookmarked your guide and will read through it several times before then. Thank you.

---

### Post by ejket on 2008-02-12
And coincidentally the only two openbox themes I downloaded from boxlook.org were both made by urukrama ...

---

### Post by Caraibes on 2008-02-12
I really enjoy OpenBox as well, but I must admit I use it in combination with Gnome, so I get the best of both world !

---

