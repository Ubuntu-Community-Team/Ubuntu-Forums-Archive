---
title: "hung up login screen:is that a graphics problem ?"
date: 2009-04-17
forum: Desktop Environments
---

### Post by get2shashank on 2009-04-17
I installed ubuntu 7.10 on my machine. It installed all the way fine. When i was prompted to reboot the system (after removing the disc from the system) i did so which booted the new install.

I then type in my username and password and then it is. It accepts my details [i.e. no incorrect username/password message] and then it just sits there on the light orange blank screen. It proceeds to nowhere even after waiting for long periods of time [neither can i see the hard drive read LED on. the system seems to be doing no working on my login attempt]. I just cannot login to my GUI desktop [although i can login at the terminals==>Ctrl+Alt+F2 to F6].

What do i do.I think it is due to some graphics issue.
**One thing...I have a higher screen resolution at the login screen than what i set at the ubuntu desktop during live disk session.
**Also the screen refresh frequency seems to be lower than 85Hz which is recommended for my CRT monitor.
**the recommended primary mode for my CRT monitor is 1024x768 (85Hz). This is what i set during the live disk session before initiating the install. i should get that thereafter, but i dont.
**When i booted from the CD for the first time, then before the GUI of ubuntu took up the screen, i was prompted with messgaes like...
load boot time graphics [y/n] and a few more like this. [i answered with Y everytime]
My buddy tells me these things are not experienced in his machine. So is some thing wrong here.

I have an integrated graphics on my motherboard. Its Intel 845GL (64 MB).

---

### Post by aaronp on 2009-04-18
> **get2shashank said:**
> I installed ubuntu 7.10 on my machine. It installed all the way fine. When i was prompted to reboot the system (after removing the disc from the system) i did so which booted the new install.

I then type in my username and password and then it is. It accepts my details [i.e. no incorrect username/password message] and then it just sits there on the light orange blank screen. It proceeds to nowhere even after waiting for long periods of time [neither can i see the hard drive read LED on. the system seems to be doing no working on my login attempt]. I just cannot login to my GUI desktop [although i can login at the terminals==>Ctrl+Alt+F2 to F6].

What do i do.I think it is due to some graphics issue.
**One thing...I have a higher screen resolution at the login screen than what i set at the ubuntu desktop during live disk session.
**Also the screen refresh frequency seems to be lower than 85Hz which is recommended for my CRT monitor.
**the recommended primary mode for my CRT monitor is 1024x768 (85Hz). This is what i set during the live disk session before initiating the install. i should get that thereafter, but i dont.
**When i booted from the CD for the first time, then before the GUI of ubuntu took up the screen, i was prompted with messgaes like...
load boot time graphics [y/n] and a few more like this. [i answered with Y everytime]
My buddy tells me these things are not experienced in his machine. So is some thing wrong here.

I have an integrated graphics on my motherboard. Its Intel 845GL (64 MB).

This happened to me when I first installed Gutsy a couple of years ago, after I'd done a bit of tweaking with my xorg.conf...

It would still allow me to go into a failsafe gnome session - can you try selecting that from the session chooser before logging in?
If that works, then you can start fresh by going to a terminal and running through the xorg reconfigure process:

```
sudo dpkg-reconfigure xserver-xorg
```

If you can't even get into failsafe, reboot, choose recovery mode and it should take you to a shell prompt. login there and run the above command.

hth
Aaron

---

### Post by get2shashank on 2009-04-18
at terminals i get this...
"cant open display"
also now the system is prompting me with a new dialogue message [thank God..it said to me something at last] saying that ubuntu is running on low graphics mode. When i configure it, it detects my monitor as generic monitor and my card (which is Intel82845GL) as Intel i8x [x, i dont remember].
Continuing with these default options, i get either a blank screen which hangs up or a deformed login screen which takes in my details and then doesn't go further...

---

