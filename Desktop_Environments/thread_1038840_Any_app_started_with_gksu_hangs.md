---
title: "Any app started with gksu hangs"
date: 2009-01-14
forum: Desktop Environments
---

### Post by arm-c on 2009-01-14
Ok, not sure about prefix. :) but this is a little frustrating.

Some things that I can think of that might be connected:
> Adobe Air (but don't think so except for problem with the Add/Remove apps not being populated... which was fixed by reinstalling gnome applet/program (can't remember name)
> I enabled the serial tablet features in xorg.conf
> I used xsetwacom in the xlocalrc file to set tablet buttons (note, had to remove the run system default rc file... before doing that, I would get duplicate apps in task bar, etc...

Sure, I can go back to undo what I did, but I want tablet features.

OK.  what happens:  When I launch synaptic / firestarter or some other application that requires a gksu password, it hangs.  For example, the gui comes up in Synaptic, but none of the packages populate.  Just empty windows.

I looked in my system monitor and noticed that gksu had a status of pipe_wait.  

After I kill the gksu, the application finishes its startup (ie: synaptic un-grays and loads package information.)

Any ideas?

>>> update.. went back and removed changes to .xlocalrc and my xorg.conf.  Doesn't appear to have had an effect.  I am still having the same problem.  Upon a reboot it still exists.  I may just give up and do a clean install of 8.10 (I upgraded from 8.04)... but there were a few other things.

I noticed that wine also quit working... There were a few apps I played with such as play-on-linux and wine-doors... but I have removed wine and those apps also.

So, in short, still having problem.

---

### Post by timtonys on 2009-01-24
arm-c,

I have same problem were with my notebook tabet HP TX2000. I have instaled Ubuntu intrepid 8.10 and configured driver for tablet touch screen WACOM.

When synaptic start, the GKSU ask my password and, after a put my pass, the synaptic init, stay with gray color and stop. In system monitor, the GKSU have the status pipe_wait and, when i kill gksu, the synaptic startup normaly.

I reinstall the package gksu, but i still have problem.

Can Anybody help?

P.S. - Sorry my bad english

---

### Post by x33a on 2009-01-24
try using gksudo instead.

---

### Post by arm-c on 2009-01-24
I solved my problem.  I am not sure exactly which application it was that I had installed, but I am certain that it was one of the NON STANDARD gnome applets.  I had also installed those while I was installing some other things around the same time.

If you installed a few additional applets, remove those.

In short, it was NOT the tablet features that gave me the gksu hang.

---

### Post by timtonys on 2009-01-24
> **arm-c said:**
> I solved my problem.  I am not sure exactly which application it was that I had installed, but I am certain that it was one of the NON STANDARD gnome applets.  I had also installed those while I was installing some other things around the same time.

If you installed a few additional applets, remove those.

In short, it was NOT the tablet features that gave me the gksu hang.


arm-c,

What kind of applets had can cause this problem, for example? what app you remove of your ubuntu for solve this problem? can you list the any possibles aplications?

thanks for help.

---

### Post by arm-c on 2009-01-24
TimTonys,

Before I started having problems, I had gone and installed a few additional gnome pannel applets that I could use on my GNOME bar (Pannel at top and bottom).  These are applets that adds additional utilities such as the gnome-weather-applet (note: the weather applet is NOT the problem and is a default applet)  Anyway, I found them by using synaptic and doing a quick search for 'applet'.  I don't recall all that I removed and didn't take the time to go through and install each one individually to test and find the offending applet.

The search will return many more entries than actually apply.  See if you have any applets gnome applets installed that don't have the ubuntu symbol on the line.

I can tell you that the following applets installed on my system don't cause me problems even though they have no "ubuntu" symbol on the line:

timer-applet
netspeed
libckyapplet1
glipper

I hope this helps.  Can you remember what all you may have installed before this started to happen?

---

### Post by adamlau on 2009-01-25
I would have purged gdm before reinstalling it.

---

### Post by timtonys on 2009-01-27
helo guys,

Thanks for the help, but unfortunately i have yet the problem!!!

I check all applets of Gnome instaled in my ubuntu, and verifique that all applets installed are supported by Canonical, ie have the ubuntu symbol on the line. So I reinstall all the applets, but the problem was not resolved.

I don't know if this information is relevant, but in the same period in which this problem appeared, the applet of Gnome, named fast-user-switching disappeared of my panel.
	
Maybe my problem has not relation with the Gnome applets, I dont know!!! I do not know what program installed caused this problem. Is there any way to check that aplication is in conflict with the gksu?

	
I appreciate the help!

---

### Post by arm-c on 2009-01-29
I am about at a loss to give any more suggestions.

You may try doing a complete removal of Wine, but I doubt that will work.

Here is what I would suggest: Reinstalling Ubuntu.  This isn't a bad thing if you have a separate /home partition. If you don't, it is a GOOD TIME to do that.

I'd recommend that you look at your system and see how much space your other directories are using.  I keep at least 10GB partition for the system, a swap partition (1GB for me, but at least the size of your RAM), and made everything else my home partition.  With a home partition, when you reinstall your os and bring your packages back, all of your program settings are preserved as well as your data.  I was amazed at how easy that made things for me and glad I took the time to reinstall my computer in this manner.  It is very helpful when doing a distro upgrade cause you can just download ISO and do a full install which reduces stray files on your computer and leads to a better overall function.

I hate to suggest a reinstall.  But sounds like your best option.

A thought, you may create a new profile on your computer.  Log into that and see if it has the same problems.  Might not.  I have found that sometimes issues are connected to a profile setting or something and that a new profile will function flawlessly.  A case in point:  I tried to access Ulteo, but it refuses to run under my main profile.  I tried it under a different profile and it works flawlessly!  I have yet to determine why my main profile is corrupt and won't run the program.

Good luck!  I'd like to know the outcome of your situation, if it worked fine in a new profile or not and if you ended up just reinstalling your system.

v/r
Arick

---

### Post by timtonys on 2009-02-16
Guys,

There was no need to reinstall my Ubuntu do solve the problem with GKSU, although i have a /home directorie on a separate partition. 

As suggested by arm-c, I just created a new user, with a new profile, and everything worked perfectly. Maybe my old profile was corrupted for some reason.
 	
Thanks by the help!

---

### Post by chrisspelberg on 2009-04-25
I have exactly the same problem with Ubunbu 8.10 on my MacBook 1,1.

Maybe the problem was caused by selecting a different keyboard layout when installing ubuntu.

I changed the system keyboard settings back to "Generic 105-key (Intl) PC" with layout "USA".

My current account still has the issue, when I create a new account gksu works normally.

I will check for differences in the user settings.

Chris

---

### Post by chrisspelberg on 2009-04-25
Ok, I found the problem:

open in gconf-editor:
/desktop/gnome/applications/window_manager/current (on my machine it has the value 'metacity')

set it to the same value as /desktop/gnome/applications/window_manager/default ('/usr/bin/compiz')

---

### Post by newbuntuxx on 2009-05-18
> **chrisspelberg said:**
> Ok, I found the problem:

open in gconf-editor:
/desktop/gnome/applications/window_manager/current (on my machine it has the value 'metacity')

set it to the same value as /desktop/gnome/applications/window_manager/default ('/usr/bin/compiz')

Thanks a lot. Your solution worked! In my case though, the current key didn't have any value nor did the default key! I simply added this to their value "/usr/bin/compiz" and it worked.

thanks again

oh and btw...I had the problem with 9.04!

---

