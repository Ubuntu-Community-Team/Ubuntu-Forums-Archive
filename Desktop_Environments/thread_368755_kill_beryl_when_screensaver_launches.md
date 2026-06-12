---
title: "kill beryl when screensaver launches"
date: 2007-02-23
forum: Desktop Environments
---

### Post by sweensterpng on 2007-02-23
I have a few screensavers that use opengl that I really like, and I also really enjoy using beryl. While both run great on their own, running concurrently seems to be too much for my system. So I was wondering if there was a way to run a script when the screensaver launches, so I would go back to the regular metacity window manager, and maybe relaunch beryl when the screensaver closes. I have no idea if this would work or not, or what files to edit, so I would appreciate any feedback.

---

### Post by phoqueyoo on 2007-02-23
I am looking for the same thing for compiz. Anyone??

---

### Post by Nano Geek on 2007-02-23
Doing that sounds rather complex. I don't think that a simple script would do the job. :confused:

---

### Post by sweensterpng on 2007-02-24
It would be oh so useful though :)

---

### Post by MinhD on 2007-03-01
I have a similar request, but for a slightly different reason.

I recently discovered that when I run Compiz, I can't run an OpenGL screensaver.  If I try to, it crashes and brings me back to the login page.  Only lame 2d screensavers reminiscent of Win 95 work...  If I turn off the GL Desktop, then the screensaver runs fine.

I have the latest updates for all my drivers, glxinfo returns the correct info and glxgears works fine too.  Asides from this issue, Compiz works fine too.

Anyone else encounter this issue and/or know a way around it?

I have an Nvidia card, running Gnome.

---

### Post by CheShA on 2007-08-20
I got this sorted:


First you need to create a perl script at ** /usr/local/sbin/swap-wm-on-screensaver.pl**

The following would kill beryl when the screensaver activates, then start metacity when the screensaver deactivates, which basically means there is no window manager running while the screensaver is running, just basic X11:

```

#!/usr/bin/perl
my $cmd = "dbus-monitor --session \"type='signal',interface='org.gnome.ScreenSaver',member='SessionIdleChanged'\"";

open (IN, "$cmd |");

while (<IN>) {
    if (m/^\s+boolean true/) {
        #when screensaver activates, run the following commands
        system("kill `pgrep beryl`");
    } elsif (m/^\s+boolean false/) {
        #when screensaver deactivates, run the following commands
        system("metacity &");
    }
}

```

if you wish beryl to start back up again instead, replace **system("metacity &");**    with **system("beryl");**:



When you've typed this up and saved it, don't forget to:

```

sudo chmod +x /usr/local/sbin/swap-wm-on-screensaver.pl

```

You may also need to :
```

sudo apt-get install procps

```


finally, you need to add it to your session start up items:
[LIST]
[*]go System > Preferences > Sessions
[*]click "New"
[*]For "Name", enter "Swap Window Manager on Screensaver"
[*]For "Command" enter
```

perl /usr/local/sbin/swap-wm-on-screensaver.pl

```
[/LIST]

Now  log off and on again and you should be in business :)

---

### Post by shadowhywind on 2007-09-05
Do you know if this would work on KDE too?

---

### Post by pgn674 on 2007-09-17
Actually, Beryl has 2 processes running: beryl and beryl-manager. I've found that to really kill Beryl, you have to kill both processes. In terminal, this would be```
kill -15 $(pgrep beryl$)
```I don't know how it would look in Perl. Just running beryl to bring it back seems to work in what I was working on, though. I'll let you know if the Perl code needs to be modified.

---

