---
title: "Certain programs stopped loading?"
date: 2006-06-17
forum: Desktop Environments
---

### Post by mark2741 on 2006-06-17
I have some applications that I can't run. I'm using Dapper.

Yesterday I installed, through synaptic, IDLE. It shows up fine in the Applications -- Programming menu, so I click to start. I see the "IDLE is starting..." rectangle in the bar at the bottom, but then after a few seconds it goes away and IDLE doesn't start. I chalked that up to just a bad insall so I marked IDLE for reinstallation. Still doesn't work. I figured it was limited to just IDLE until today I tried running my VMWare Server beta (to access MS Money via Win XP, which I've been doing successfully for a month now). To my horror, same thing is now happening with VMWare Server! It acts like it's trying to start but then nothing!

Only thing I can think that I've done since it last worked is I installed the 686 version of the kernel. So I rebooted into the 386 version that it worked with before many times but still no luck. IDLE wasn't installed until after I had installed the 686 kernel, so I'm pretty sure this problem isn't due to the kernel.

What could be causing this? I'll look through my other apps and see if there are any more that just won't run anymore. Any ideas on how to run these programs? VMWare server is critical for me to use : (

---

### Post by mark2741 on 2006-06-17
Update: the VMWare Server is working again. Turned out that the kernel update required me to load kernel-source packages for the 686 kernel; also there are some posts recently that said the latest Ubuntu auto upgrade did something to hose vmware and require re-configuration. Fortunately running the config script only takes a minute, and the virtual machine I had previously installed was still there unscathed.....

Still have no luck with IDLE though : (

---

### Post by mdurham on 2006-06-18
try running IDLE from the terminal and you might see some error messages.

---

### Post by Slapula on 2006-06-18
I too am having the same problem with IDLE. It just won't start at all.    

Here is what I got when I tried to run IDLE in terminal:

> Traceback (most recent call last):
  File "/usr/bin/idle-python2.4", line 5, in ?
    main()
  File "/usr/lib/python2.4/idlelib/PyShell.py", line 1350, in main
    root = Tk(className="Idle")
  File "/usr/lib/python2.4/lib-tk/Tkinter.py", line 1569, in __init__
    self.tk = _tkinter.create(screenName, baseName, className, interactive, wantobjects, useTk, sync, use)
_tkinter.TclError: this isn't a Tk applicationunknown color name "Black"


:confused:

---

### Post by mark2741 on 2006-06-18
Yep Slapula - that is what I get too. This stinks, as I was trying to learn Python via those online screencast lectures that are available on the web for free, but I can't follow along with them. 

Just typing in the code, per the screencast, into the standard python terminal interpreter doesn't work. I get errors when I type in:

root = Tk()

Tkinter is installed as far as I can tell. Oh well. I guess I'll just give Ruby a try after all.

---

### Post by Slapula on 2006-06-18
Here is the funny part: IDLE runs fine on my Ubuntu 6.06 hard drive at work.  This can only mean that we did something to our installations to cause IDLE to stop functioning.  I've even tried running the older versions of IDLE, but I still get the same error message in the terminal.

---

### Post by Slapula on 2006-06-18
Well, it seems that I *can* get IDLE to work.  The only problem is that it doesn't work for the first user logged onto the system.  It doesn't matter who the user is (I've even tried root), the first one that logs on can't use it.  Once I switch to a different user, I can run IDLE in a matter of seconds.  Ugh, this is driving me bonkers ](*,)

---

### Post by mark2741 on 2006-06-18
Wow....good catch! I just created a new user (I've been using Ubuntu now for a month and just with one user) and sure enough - Idle works fine for the other user. I'm not sure what we did to hose our regular user accounts : ) 

I did follow a tutorial a while back to install that Compiz/XGL stuff, which only worked partially and what did work I didn't like so I never run it (the tutorial I followed had me type in "thefuture" into a terminal to start Compiz/XGL). By any chance have you installed that as well? That's the only thing I can think of. I am running the 686 kernel too.

---

### Post by Slapula on 2006-06-18
Ahhhh.... :lol:   I installed xgl/compiz two days ago #-o !  And you want to know something? After I read your post, I uninstalled xgl/compiz immediately.  Once that useless app was gone my IDLE started working again! 

Oh, and when you go to uninstall xgl/compiz make sure that you fix any confs (like gdm.conf-custom) that you edited.  Upon restart, I was greeted with the blue screen of xdeath because I didn't fix it (but to be honest, all you need to do is enter the startx command to get back to the GUI).

---

### Post by mark2741 on 2006-06-19
Cool! Look at that - even though I'm clueless and a newbie, I really *can* serve  a purpose after all in these forums! : )

But now I got a question - how do I uninstall Compiz/XGL?

Actually, I am having some wierd things happen to my Ubuntu lately (the other day I lost my GDesklets for some reason and they haven't come back). I was starting to think that was due to the latest updates, but after creating and logging in as a different user to get Idle working, I'm thinking I might just be better off just copying my main user's files over to that user and just using that. But I don't know if Compiz/XGL is installed with that or not? Or is it a per user thing and only affects the user that installed it?

I also had some other applications that wouldn't run (just like Idle) with my main user account but now run fine in the new user's account: Alsamixer and Gnometab are two exampls. Wierd. I knew I shouldn't have screwed with that Compiz crap not knowing what I was doing! : (

---

### Post by Slapula on 2006-06-19
To uninstall xgl/compiz:

1. Go into synaptic and search for xgl and compiz packages.  I did a complete removal so that they won't leave any garbage behind.

2.  Go to /etc/ and look for the files gdm.conf-custom and gdm.conf-custom-backup.  The backup file should be the one without any xgl server stuff in it.  If you don't have a backup, then just delete the stuff you added to gdm.conf-custom when you installed xgl.

3. restart the xserver

Let me know if that works.  As for your other apps not working,  I have no idea what could be causing them to not work.  Could be xgl/compiz, could be something else entirely.  Just try to get rid of xgl/compiz and see if that fixes IDLE for you.  Hey, it might fix those other apps, too! :grin:

---

### Post by mark2741 on 2006-06-20
Thanks Slapula. After completely removing compiz and xgl packages I at first ran into some X problems but after a restart everything is working again. And I can confirm that compiz/xgl, at least installing it the way I did following 'thefuture' tutorial/memo, completely had my system screwed up. I even had sound problems before (lower than normal volume all the time) and now that's fixed. Some applications that weren't working, other than Idle, are now working fine as is Idle.

I should have known not to try that experimental stuff as a newb!

---

