---
title: "Executing commands at GNU screen startup via a bash script"
date: 2009-10-31
forum: Desktop Environments
---

### Post by rootless on 2009-10-31
Alright, I'm having trouble with a script stubbornly refusing to do what I want. I have spent a ridiculous amount of time googling this, and I'm at a loss.

Here's the script:
```
#! /bin/bash

xfce4-terminal --hide-menubar --hide-borders --hide-toolbars -x screen -X /home/abraxas/Code/loginscript

```

loginscript is designed to echo a greeting in big ASCII block letters after the user logs in. It's very slick and works very smoothly

I am trying to get xfce to launch an undecorated borderless terminal in full screen on startup. I am unsure of what format the --geometry= command takes.

Besides that, the beginning of my script works fine. I am trying to get a little more complex though. Screen invokes in that terminal just fine, but when I try to get screen to invoke my login script on startup by using the -X switch, the terminal will open for a millisecond and then close.

I am at a loss to understand this behavior. This is why I truly hate all GUIs and prefer to do everything from command line. I just want to log into xfce have it get out of the way, and automatically have screen be there, maximized, running my login script.

Any ideas?

Also, just for kicks, here's my login script, if you want to use it:
```
#! /bin/bash

clear

echo "\"From where Winston stood it was just possible to read,"
echo "picked out on its white face in elegant lettering,"
echo "the three slogans of the Party:\""

read -n 1

figlet -c -f big "WAR"
sleep .1
figlet -c -f big "IS"
sleep .1
figlet -c -f big "PEACE"

sleep .5
clear

figlet -c -f big "FREEDOM"
sleep .1
figlet -c -f big "IS"
sleep .1
figlet -c -f big "SLAVERY"

sleep .5
clear

figlet -c -f big "IGNORANCE"
sleep .1
figlet -c -f big "IS"
sleep .1
figlet -c -f big "STRENGTH"

sleep 1
clear

figlet -c -f big "WELCOME"
sleep .1
figlet -c -f big "TO"
sleep .1
figlet -c -f big "$HOSTNAME"
sleep .1
figlet -c -f big "$LOGNAME"
sleep .1

sleep .1

read -n 1

clear

echo "\"There was of course no way of knowing whether you were being watched at any given moment. How often, or on what system, the Thought Police plugged in on any individual wire was guesswork. It was even conceivable that they watched everybody all the time. But at any rate they could plug in your wire whenever they wanted to. You had to live—did live, from habit that became instinct—in the assumption that every sound you made was overheard, and, except in darkness, every movement scrutinized.\""


```

And yes, I know, I'm paranoid. Hahaha.

---

### Post by rootless on 2009-11-01
Bump

---

### Post by rootless on 2009-11-07
bump

---

### Post by Barriehie on 2009-11-07
So the terminal opens and runs the script but then closes real quick???

Barrie

---

### Post by rootless on 2009-11-07
As far as I can tell the terminal only opens long enough to start screen, and then screen attempts to execute my script, fails, and then the window gets killed.

I still have no idea what is doing this.

---

### Post by lswb on 2009-11-07
IIRC the -X switch sends a screen command to a running instance of screen. It expects a command that is valid to the screen command interpreter, not an arbitrary program or script. 

I don't know if this is the best way, but try this: Remove the "-X" from your command line; Then screen will execute that script when it starts. To keep screen from exiting immediately after it runs your script, add this line to the very end of your script:
```

exec bash

```

---

### Post by XubuRoxMySox on 2009-11-08
If you really don't like GUIs and prefer to work from the terminal or a stark but powerful window manager, have a look at [Crunchbang]("http://crunchbanglinux.org")! It has no desktop environment at all but borrows many Xfce elements for functionality, but they are never "in your way." It's super lightweight and fast! I have Crunchbang on my laptop and Xubuntu on the desktop. So far I'm completely delighted with both.

-Robin

---

### Post by falconindy on 2009-11-08
This is working as intended. The script finishes and the terminal exits because that's what the -X flag does. I'm not 100% clear on when you want this displayed, so I'll give you two alternate options:

1) To display this every time a user opens a terminal (or logs in from the console), invoke your script from $HOME/.bashrc.

2) To display this only on login, add the contents of your script to the file /etc/motd.tail.

---

### Post by lswb on 2009-11-08
> 
2) To display this only on login, add the contents of your script to the file /etc/motd.tail.

This will display the contents of the script, not run it.

---

### Post by Barriehie on 2009-11-08
Try this, put a myscript.desktop file in ~/.config/autostart/myscript.desktop and then logout.  When presented with the login/username screen hit F10 for new session, (GNOME) and login as usual.  I tried this with a test to run my firefox clean script and it worked.

Here's a sample .desktop file.  Of course substitute the appropiate path to the script and Naming, comments, etc.  The definition for .desktop files can be found [here](http://standards.freedesktop.org/desktop-entry-spec/latest/index.html).

```


[Desktop Entry]
Type=Application
Encoding=UTF-8
Version=1.0
Name=No Name
Name[en_US]=FFclean
Exec=bash -c /home/barrie/bin/ffclean.sh
X-GNOME-Autostart-enabled=true
Comment[en_US]=FirefoxCleanUp
Comment=FireFoxCleanUp
GenericName=

```

---

### Post by rootless on 2009-11-08
Heey, thanks for the help all! You have no idea how long this minor flaw has been bothering me.

Yeah Dixie, I used to use something similar to Crunchbang, a distro I mixed myself, but I used Fluxbox instead. Actually, this was before Crunchbang was around- it's relatively new... or at least I hadn't heard of it... anyway, I fit every piece of this distro together from scratch- even the kernel, and then heard of Crunchbang just a few months later.

Hey, it's ok, I learned a lot. I loooved my Fluxbuntu netbook. I've used almost every Window Manager out there, and Fluxbox was my old standby for a very long time. I heavily modded Flux to behave like a tiling WM. It was really fast and beautiful but it just didn't want to grab certain windows for some reason. 

This gradually started to annoy me until one day I got sick of reconfiguring all the time and chucked both Fluxbox and my custom distro altogether.

By this time, I had learned enough about linux to do most of what I wanted in terminal- it was the only fast way to do things on my ancient netbook. I was telling a friend about how I loved GNU screen, and he told me to try Ratpoison- a WM based on screen-like commands.

At first, I was skeptical of another full-on tiling WM. I had tried xmonad for a while and had been disappointed at the lack of scriptability, but Ratpoison totally blew my mind. Unlike Flux, it does ONLY what you tell it to do, predictably, time after time. It is fully scriptable with about a hundred commands and hooks. It's my new favorite WM (although Fluxbox Openbox, etc. still hold a place in my heart.)

Anyway, so, now I use Backtrack 4 with Ratpoison on my netbook to pentest my Xubuntu home server/desktop. As far as Desktop Environments go, Xubuntu is the one I hate the least, being the most logical, integrated, and least crufty. 

At some point, I may switch my Desktop over to Ratpoison, but right now, I'm experimenting with Xubuntu, seeing if I can utilize the advantages of it's tightly integrated desktop while increasing efficiency.

This little GNU screen hack is part of that process... of course, ASCII art is cruft, but it's acceptable cruft ^___^

Barriehie- I'll try that, log out, and get back to you.

---

### Post by rootless on 2009-11-09
OK, now for some reason it's spawning two terminals. I commented out the script, and no terminals spawn, so I know that it is the script that spawns both. Any ideas? You guys have been great so far. Keep it up!

---

### Post by Barriehie on 2009-11-09
> **rootless said:**
> OK, now for some reason it's spawning two terminals. I commented out the script, and no terminals spawn, so I know that it is the script that spawns both. Any ideas? You guys have been great so far. Keep it up!

So now it's working as desired except for spawning 2 terminals???  How about copy/paste/post the script again please?

Thank You,
Barrie

---

### Post by rootless on 2009-11-09
```
#! /bin/bash

xfce4-terminal --fullscreen -x screen /home/abraxas/Code/loginscript
```

---

