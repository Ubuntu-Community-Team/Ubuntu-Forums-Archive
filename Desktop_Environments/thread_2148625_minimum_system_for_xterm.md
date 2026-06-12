---
title: "minimum system for xterm"
date: 2013-05-26
forum: Desktop Environments
---

### Post by David Butland on 2013-05-26
I am trying to test some Java software on a minimal Ubuntu system - no gui - just a bare terminal linux system in Ubuntu 13.04 on an old computer.
The software uses Swing, and so I need an x-terminal (apparently). I have  installed xterm, xorg and openbox
After *** export DISPLAY=0:0***
and ***xterm*** the message "Can't open display 0:0" appears

1. Am I missing some software?
2. Is there some technical information someone could point me to, suitable for a non-specialist?

David Butland

---

### Post by 2F4U on 2013-05-26
Did you install the appropriate graphics drivers? Is Openbox working? Whats in /var/log/Xorg.0.log?

---

### Post by sanderj on 2013-05-26
> **David Butland said:**
> I am trying to test some Java software on a minimal Ubuntu system - no gui - just a bare terminal linux system in Ubuntu 13.04 on an old computer.
The software uses Swing, and so I need an x-terminal (apparently). I have  installed xterm, xorg and openbox
After *** export DISPLAY=0:0***
and ***xterm*** the message "Can't open display 0:0" appears

1. Am I missing some software?
2. Is there some technical information someone could point me to, suitable for a non-specialist?

David Butland

So apparantly the Java software wants to open a GUI. The export DISPLAY is exporting to the local, so non-GUI system. That's not going to work.

So: where do you want to show the GUI of the Java software?

---

### Post by David Butland on 2013-05-29
Thanks for your prompt replies. I missed them, expecting to get an email notification that anyone had offered to help.
You must understand that my expectations of what can be achieved are as high as my ignorance of what else has to happen.
 
2F4U asked whether I had installed the appropriate graphics drivers. Not explicitly. I apparently successfully entered:
sudo apt-get install openbox
and
sudo apt-get install xorg
I have not tested whether these commands have set up an appropriate environment.
There is no [COLOR=#000000]/var/log/Xorg.0.log file.
And yes, sanderj, I am blissfully expecting to be able to generate some graphics output without a gui. I reason that a gui can create windows, so why not me? That may be unrealistic. I just want the minimum environment in which to test so0me graphics output.
I will keep looking for replies to this post, but is there an option to be notified if someone has offered to help?

David Butland[/COLOR]

---

### Post by Irihapeti on 2013-05-29
Have you actually started the X server? To do that, enter the command "startx" after logging in. The Xorg.0.conf file should be created automatically. It shouldn't be necessary to set special environment variables.

---

### Post by steeldriver on 2013-05-29
I think you actually need to start an X server for your xterm to connect to, usually that would be done via the 'startx' command, which starts an X server based on a bunch of default stuff in /etc/X11 and then executes the user's session as defined via .xinitrc and/or .Xsession

So maybe try creating a minimal ~/.xinitrc file, something like

```

# Load X resources (if any)
if [ -e "$HOME/.Xresources" ]
then
        xrdb "$HOME/.Xresources"
fi

xsetroot -solid "#DAB082"
x-terminal-emulator -geometry "80x24+10+10" -ls -title " Desktop" &
x-window-manager &

```

or try openbox and fall back to a plain default WM if unavailable

```

# Load X resources (if any)
if [ -e "$HOME/.Xresources" ]
then
        xrdb "$HOME/.Xresources"
fi

if which openbox-session >/dev/null
then
        openbox-session & 
else
        xsetroot -solid "#DAB082"
        x-terminal-emulator -geometry "80x24+10+10" -ls -title " Desktop" &
        x-window-manager &
fi

```

and then executing 'startx' from the command line?

See --> [https://help.ubuntu.com/community/CustomXSession](https://help.ubuntu.com/community/CustomXSession)

---

### Post by David Butland on 2013-05-29
Thanks for your prompt replies. I missed them, expecting to get an email notification that anyone had offered to help.
You must understand that my expectations of what can be achieved are as high as my ignorance of what else has to happen.
 
2F4U asked whether I had installed the appropriate graphics drivers. Not explicitly. I apparently successfully entered:
sudo apt-get install openbox
and
sudo apt-get install xorg
I have not tested whether these commands have set up an appropriate environment.
There is no [COLOR=#000000]/var/log/Xorg.0.log file.
And yes, sanderj, I am blissfully expecting to be able to generate some graphics output without a gui. I reason that a gui can create windows, so why not me? That may be unrealistic. I just want the minimum environment in which to test so0me graphics output.
I will keep looking for replies to this post, but is there an option to be notified if someone has offered to help?

David Butland[/COLOR]

---

### Post by David Butland on 2013-05-29
You are all terrific guys.
I tried "startx" after logging in. A lot of things scrolled past, and I now have a lighter coloured full screen which does not appear to accept input. I will wait for a bit to see whether anything develops.
If all else fails I'll try the magic suggested by steeldriver. Will post  a report later.

David

---

### Post by Irihapeti on 2013-05-29
Right-click on that lighter screen and you'll get a menu.

---

### Post by David Butland on 2013-05-29
Yippee!!
Are  you really only 2 years old?
That is amazing. You and I would make a wonderful team.
All problems solved.
Well, apart from world peace and brotherhood.
David

---

### Post by Irihapeti on 2013-05-29
> **David Butland said:**
> 
Are  you really only 2 years old?


Let's say that it's a very old photo. Several decades have passed since that was taken. :)

I'm glad my playing around with Openbox is proving useful.

---

### Post by David Butland on 2013-05-29
How do I flag this problem as having been solved? I've only just discovered how to be notified of replies by email.

It's years since I had anything to do with X - I hadn't even realised that it's still in use. The fonts are quite adequate for my purposes, and a lot better than systems I was using 10 years ago. It may be time to dust some old software.
Oooh I am pleased

---

### Post by Irihapeti on 2013-05-29
To mark a post "solved", see [http://ubuntuforums.org/showthread.php?t=2121377&p=12536730#post12536730](http://ubuntuforums.org/showthread.php?t=2121377&p=12536730#post12536730)

---

