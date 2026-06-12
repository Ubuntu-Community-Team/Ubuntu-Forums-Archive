---
title: "Simple file/print KIOSK"
date: 2009-01-21
forum: General Help
---

### Post by melbs on 2009-01-21
I have tried doing some research and search threads before I asked and I have found some info but not exactly what I'm looking for.

**What I want to do:** a simple workstation running Linux, where people can simply look for the form they want and select it and it will automatically print. There will be less than 15 forms.

A simple web page could work but I want it full screen and work like a KIOSK. (I am a newbie at Linux/KIOSK).

I have looked into Open Kiosk but a lot of this software is really overkill for the simple thing I want to accomplish! Also, can I run Open Kiosk on Ubuntu-do I need to install KDE? 

Thanks in advance for any comments.

---

### Post by melbs on 2009-01-21
Another quick question - I installed "KIOSK Admin Tool" on Ubuntu Hardy Heron. I tried going to Help/Kiosk Handbook and it could not open it because it could not find the service kdhcenter.

Do all KIOSKs have to be on KDE? So I have to install KDE?

---

### Post by lykwydchykyn on 2009-01-21
I have done web-browser kiosks for years, many different ways.  The best approach is to forget about using KDE or GNOME and just override the GUI session with a script.

Basically, you can do this by putting commands in the ~/.xsession script.

Here's a sample .xsession script from one of my kiosks:
```

flwm &
xset s off
xset -dpms

while true; do
        rsync -qr --delete --exclude '*.Xauthority' /etc/profiles.d/thinclient/ $HOME/
        firefox -fullscreen
        done

```

That script basically runs a minimal window manager (flwm), disables screen blanking/powersave, then runs an infinite loop that refreshes the user's home directory and runs firefox fullscreen (had to add a firefox extension to make the -fullscreen switch work).  

I'm not sure what a good software front-end would be for your application, it might be best just to use a local web-page and have an embedded PDF reader from which the user can print.

I blogged about this here: [http://www.alandmoore.com/geekpage/index.php?content=33](http://www.alandmoore.com/geekpage/index.php?content=33)
though that's a bit outdated.

---

### Post by lykwydchykyn on 2009-01-21
> **melbs said:**
> Another quick question - I installed "KIOSK Admin Tool" on Ubuntu Hardy Heron. I tried going to Help/Kiosk Handbook and it could not open it because it could not find the service kdhcenter.

Do all KIOSKs have to be on KDE? So I have to install KDE?

kiosk admin is a tool to configure KDE for kiosk use.  That isn't to say you have to use KDE to do a kiosk, just that tool won't do anything unless you are.

I think you'll find it's a lot easier to build the kiosk environment from the ground up rather than installing a massive environment like KDE or GNOME and trying to lock everything down.

---

### Post by melbs on 2009-01-21
I think you are right about building from the ground up. However, I'm not quite sure as to where to start or if I want to do a web page or what.

Does anyone have any info on basic, simple kiosks?

Thanks for the information I will take a look at that page.

---

### Post by lykwydchykyn on 2009-01-21
Once you understand how to work with the .xsession file, from there it's just a matter of finding a program that accomplishes what you want with a minimum of other functions.  I suggested a web page because it's the simplest way I know of having a barebones interface where you can open files.  There are other ways to approach it, I suppose.

---

### Post by melbs on 2009-01-21
What will be needed to make the screen only show that one web page, no toolbars, menus or any other options and "loop" back to a welcome screen. It seems if I make a simple web page it will not work as much like a kiosk-like screen like I want. (Thanks, I'm investigating ideas for work and I am new to this type of thing.)

---

### Post by lykwydchykyn on 2009-01-21
> **melbs said:**
> What will be needed to make the screen only show that one web page, no toolbars, menus or any other options and "loop" back to a welcome screen. It seems if I make a simple web page it will not work as much like a kiosk-like screen like I want. (Thanks, I'm investigating ideas for work and I am new to this type of thing.)

There are some kiosk-type plugins for firefox that will do this, or you can use prism, which is a stripped-down firefox for kiosk/webapp type situations.

Opera also has a kiosk mode.  I've been through a lot of these, and they're all a little different, so you may just want to check out various options and see what works for you.

If a web page isn't going to do it, something like idesk or rox-pinboard might be configured to do what you need. They basically provide desktop icons (and only desktop icons).

---

### Post by melbs on 2009-01-22
Thanks for all of your information! I will look into it some more (and may be back : ) )

---

