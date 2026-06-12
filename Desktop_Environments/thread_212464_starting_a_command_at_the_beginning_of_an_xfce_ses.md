---
title: "starting a command at the beginning of an xfce session"
date: 2006-07-09
forum: Desktop Environments
---

### Post by DAaaMan64 on 2006-07-09
Alright I have been looking around for awhile now trying to figure out how to run this command on startup:

```

x11vnc -logfile $HOME/.x11vnc.log -rfbauth $HOME/.vnc/passwd -forever -bg

```

I have tried gediting $HOME/.xsession and .xprofile but both have nothing in them.  I have search for this for awhile and I was hoping for a simple solution.  Anyways, I need to learn how to do this regardless of whether it's simple or not.  So, may I have some help?  Remeber this is xfce so I can't to my knowledge just use the session start manager that gnome has.  

Thanks :)

---

### Post by 5-HT on 2006-07-10
You should be able to just put that command in a script, and place it in a directory called "Autostart" in ~/Desktop. 

I'm not currently running XFCE so I'm not sure if you even need an executable script in the Autostart directory - putting that command in a file within the directory may be enough.

XFCE will source ~/Desktop/Autostart  on boot and execute anything it finds in there.

Hope that helps.

---

### Post by DAaaMan64 on 2006-07-10
Thanks 5-HT, that was very helpful, I will try to summarize what I did.

**Running a command at startup of a Xfce Session**

I wanted to run this command on startup:

```

x11vnc -logfile $HOME/.x11vnc.log -rfbauth $HOME/.vnc/passwd -forever -bg

```

Normally it would be a command I would run in a terminal window, but I don't want to do that every time I restart my machine.

So in xfce do the following...

1.  Go to the "/home/your_username/Desktop/" directory.

2.  Look for a folder called "Autostart", if it doesn't exist, create it.

3.  Go into the "Autostart" folder.

4.  Create a basic text document, with nothing in it except the command you want to run.

5.  Save it, log out and log back in, make sure it worked, and your golden.

More specifically I used these steps to get x11vnc to run on startup of xfce, so that I could just connect to it any anytime.

---

