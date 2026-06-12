---
title: "VNMR help! Varian's NMR display on ubuntu"
date: 2009-04-15
forum: Education &amp; Science
---

### Post by rajan on 2009-04-15
I am trying to get remote access to a sun microsystems server running the vnmr programs that you would use to work up NMR data. I ssh in using ssh -Y [email]username@server.edu[/email], and almost everything is cool. However, I cannot see the display that I should be seeing for the middle screen. That is, if I load a spectrum, I don't see the actual spectrum very well, as you can see in the screenshot attached. 

Also, before I load a spectrum, I cannot see the contents of this window at all except for a really quick flash that occurs when you click on the screen and highlight an FID or folder (when I'm navigating to the FID file of interest). I tried changing my contrast, but that didn't work, and I think changing color depth has worked with another coworker using 8.04 (i'm using 6.06 now), but restarting X every time I want to look at NMR stuff isn't really an option. Thanks for any help,

rajan

---

### Post by 2kayak on 2009-08-12
Did you resolve this issue?  I'm have a similar problem with VNMRJ and imaging datasets.  The data loads, and I can see the histogram, but where the image should be is just black.

---

### Post by rajan on 2009-08-12
i wish i could say i fixed it, but i haven't seen anyone actually get it to work. also since i'm directly across the hall from the NMR room, there's not much of a fire under my chair to solve this. I'm not even sure where to start, but  i'd be glad to try and help you if you need it. 

my version (6.06) is most likely well behind what you're using so potentially there's something out there that will fix this for your version. I think that it should be a more common problem that just the VNMR program. I would have thought that every unix-based program probably has some required fix needed before it displays properly on ubuntu. in any case, i hope it works, and let me know if you get stuck somewhere.

---

### Post by janec on 2010-01-26
Hi, anyone found any solution for this?  I have the same issues.  We wanted to upgrade our workstations.  We got old RH9 machine that can remote to the vnmr and the screen works well.

I hope anyone who found a solution for this would share it.  Cheers!

---

### Post by Chronon on 2010-01-27
I think seeking input from Varian would be a good step to take.

---

### Post by rajan on 2010-03-02
good idea ... talked to Varian's help. they were very helpful and responsive. they suggested VNC server instead of ssh access with x windows. 

that being said, the vnc server was really easy for me to install because i didn't have to do anything, but the guy who runs the NMR lab had to install it. there was apparently a hiccup getting the login to occur correctly. this may not be a problem for your system, but if it is, you will need to "configure things to make external vnc access start up an xdm 
login, which then behaves normally." 

here is a useful web site that the installer used for VNC access:

[http://homepage.ntlworld.com/daniel.rigal/xdmvnc.html](http://homepage.ntlworld.com/daniel.rigal/xdmvnc.html)

now, i simply need to type:


```

rajan@saraswati:~$ vncviewer server.server.server.edu:1

```

and i've got good colors. 

this is solved in my view, and it seems that the future versions of VNMR will not have this color problem so a simple ssh will work.

enjoy!


rajan

---

