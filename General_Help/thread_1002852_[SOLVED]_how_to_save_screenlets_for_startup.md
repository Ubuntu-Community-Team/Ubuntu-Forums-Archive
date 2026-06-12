---
title: "[SOLVED] how to save screenlets for startup?"
date: 2008-12-05
forum: General Help
---

### Post by rixtr66 on 2008-12-05
I have some screenlets i use,but i cant seem to get them to be there at startup?I tried saving them in sessions but that didnt work.
so how do i save them for startup?????
any help would be appreciated!!
Peace
Rick](*,)

---

### Post by Wartender on 2008-12-05
in the screenlets manager, just highlight the screenlets you have open and check the auto start on login box.

---

### Post by rixtr66 on 2008-12-05
I did that,but they still arent there at startup?
Rick

---

### Post by rixtr66 on 2008-12-06
I have tryed everything to get my screenlets to start,session mngr.is setup,
the startup boxes on the screenlets are checked.????????
they still arent there at startup!!
is this a compiz thing?
:-k ](*,)]
Rick

---

### Post by Brain-free on 2008-12-06
First of all, the screenlets project is dead. Universal Applets is the one that is active and you can find more about it [here]("http://forum.compiz-fusion.org/showthread.php?t=8522").

You should know however that they are a bit unstable.

Secondly - and most probably a long shot - check if at startup, the screenlets process runs in the background. If this is the case, you probably have widget layer enabled in compiz and it treats screenlets as widgets.

And finally, which is the version of screenlets you have installed? If it's different than [this one]("http://www.gnome-look.org/content/show.php/Screenlets+0.1.2?content=82586"), then your problem may be justified.

---

### Post by rixtr66 on 2008-12-06
ok ill check out universal-applets,i uninstalled screenlets and tried an older version still a no go.
Peace
Rick

---

### Post by kabeza on 2010-04-14
Hi guys
Sorry for bumping but I'm having the same problem

I've set everything, tried some things I found on google, but I'm still having problems trying to make screenlets to load in the same position I left in last session

---

### Post by mcurran on 2011-02-07
add a symlink to your Autostart folder for each screenlet you want opened at startup, for instance in KDE3, I use the following for my pidginscreenlet:

sudo ln -s /usr/share/screenlets/Pidgin/PidginScreenlet.py /root/.kde3/Autostart/PidginScreenlet.py

I also created a startup script for wicd-client and also pidgin itself, in order for this one to work, but that's besides the point...

---

### Post by nigeldodd on 2011-05-21
On upgrade to Ubuntu 11 my clock screenlet ceased to start when I logged in. I could get it to work from the Screenlet daemon icon on the top task bar.

I found that the path was wrong in the Startup Applications' Preferences. For the ClockScreenlet it was 

python -u /usr/share/screenlets/Clock/ClockScreenlet.py

whereas it should have been

python -u /usr/share/screenlets/screenlets-pack-basic/Clock/ClockScreenlet.py

When I changed it to that, it worked on startup. (not surprisingly).

---

### Post by torlud on 2012-01-20
Thank you nigeldodd! That saved me alot of time.

A tip for finding adresses to non-basic screenlets is to look at the directory

~/.screenlets/

Just in case someone out there is as forgetful as myself... ;)

---

