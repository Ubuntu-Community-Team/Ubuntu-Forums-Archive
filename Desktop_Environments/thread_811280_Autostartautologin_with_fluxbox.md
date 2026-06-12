---
title: "Autostart/autologin with fluxbox"
date: 2008-05-29
forum: Desktop Environments
---

### Post by zhimsel on 2008-05-29
I've been reading a lot of threads and articles regarding autologins, autostart, etc.
But right now I'm very tired, and all this info is buzzing around in my head. I have a server install of 8.04. It had no GUI before I installed fluxbox (just the "fluxbox" package in the repos, nothing else). It works over SSH using a different session over ssh on my Desktop PC using ```
xinit -e ssh -XCT [user@host] fluxbox -- :2
```. But it doesn't work on the actual server (I want to leave a GUI session open and logged in so I can VNC into it any time). I know why it doesn't, because X isn't installed. This leads me to my 3 questions:

1. What packages do I need to get X/Fluxbox running on the server itself (not over SSH). I haven't decided on whether or not to use a login manager yet. But that depends on your answers to the next questions

2. How can my system automatically start Fluxbox at boot (not that it shuts down often, it is a server...)? This system is a basic CLI only, so its from the ground up.

3. How can Fluxbox (or whatever) automatically log into my user account (we can name it bob@server) and start a program (lets say xclock, for example)?

So basically what I want is (when it starts up), for a GUI to be logged in under "bob" with "xclock" running.

If any of these solutions have been posted already, I truly apologize, for I am very tired and I don't have the energy to search for them.

---

### Post by Mattaus on 2009-06-15
Hey dude, just wondering if you ever got this sorted out? I only ask because I am basically trying the same thing on my HTPC (switching from GNOME to Fluxbox to improve boot times) and while I know how to start a program automatically upon stating FLuxbox, I can;t figure out how to auto login yet...

IF you want the link for the starting of applications I can find it for you.

Cheers.

---

### Post by eriqjaffe on 2009-06-15
Auto-login:

[http://www.handlewithlinux.com/reconfigure-automatic-login-ubuntu](http://www.handlewithlinux.com/reconfigure-automatic-login-ubuntu)

Well, that's how to disable it, but you can enable it there as well.

---

### Post by ronocdh on 2009-12-01
> **eriqjaffe said:**
> Auto-login:

[http://www.handlewithlinux.com/reconfigure-automatic-login-ubuntu](http://www.handlewithlinux.com/reconfigure-automatic-login-ubuntu)

Well, that's how to disable it, but you can enable it there as well.
Not relevant to OP's situation.

Try [this]("http://blogs.koolwal.net/2009/03/15/howto-autologin-into-your-linux-system-without-xdm-gdm-kdm-etc/")

I use Fluxbox with no session manager (e.g. XDM, GDM, KDM) and this setup worked perfectly for me. Essentially, you just add this to /etc/rc.local:```
su - **<username>** -c startx
```Of course, replace **<username>** with your actual username! Also, it should be noted that although it looks like there is a flag missing after su (" - "), that is the correct syntax. Read the manpage for more info.

---

