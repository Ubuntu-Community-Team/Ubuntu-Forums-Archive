---
title: "accidentally deleted something"
date: 2009-06-12
forum: Desktop Environments
---

### Post by benjamindlevin on 2009-06-12
i have been unsuccessful with finding an acceptable solution to my current problem.  i have checked the f.orums and wiki first.  i have tried multiple searches, changing my wording each time so as to fully understand what it is that has happened.  

i am running Easy Peasy 
Release 8.10 (intrepid)
Kernel Linux 2.6.27-8-eeepc
GNOME 2.24.1

i have been using it with the netbook view, and somehow i have managed to remove my entire system tray, including Easy Peasy icon.  I cannot minimize anything, and my notification area containing my  bluetooth icon, internet connection icon and volume control is gone.  

right clicking does nothing for me, except give me the option to Change Desktop Background. 

i was trying to uninstall some things that i didnt need, and i may have inadvertently deleted something.  i deleted Evolution Mail thingy... K-torrent, and some games... it should not have affected anything, but then again... i am new to Ubuntu, so who knows.  

any help is appreciated

---

### Post by jerrrys on 2009-06-12
Evolution is tied in to your desktop...

[http://ubuntuforums.org/showthread.php?t=1158042](http://ubuntuforums.org/showthread.php?t=1158042)

---

### Post by labinnsw on 2009-06-12
You can install a gnome or xfce panel from Synaptic
System >> Administration >> Synaptic

If you have no panel then, you probably have no menu.

Click Alt+F2 to launch gnome do.
In the window type synaptic

Once you have a panel, right click on the panel and select Add to Panel
Scroll to: Notification area, select it and click Add.

---

### Post by benjamindlevin on 2009-06-13
thank you both, however i am unable to install anything to remedy this.  i tried re-installing evolution and upgrading GNOME ... installing gnome-do... not sure why i cannot get this back.  is there a way to roll back my software config?  i dont know.  very frustrated by this.  

my cynical windows buddy told me that this is what happens with too much freedom... f* that, now if only to show this guy that i'm not a moron... i need to get this re-installed.

i went to the evolution site and they have it for download, if i want to compile from source... how exactly do i do that?  i will be looking into this, in the meantime... if anyone has any ideas please throw em here.

---

### Post by labinnsw on 2009-06-13
Seems to me that you are able to use the terminal. If so, you can try to restart gnome panel. In a terminal type:
```
killall gnome-panel
```

On the matter of rolling back. You could if you have a back-up of the system when it worked properly. Failing that, you can now back-up your home directory, Re-install the system, perform the updates, overwite the new home directory with the backed up one, then open a terminal and type:
```
chmod 644 .dmrc
chmod 700 ~
```

You may also want to reinstall any hardware and software that were installed so make a list first.

---

### Post by jerrrys on 2009-06-13
dont do this yet, but im thinking that you need to do an "apt get install evolution". can anyone verify that?  i am pretty sure thats the command, may need a sudo in front of it. ill google, but maybe someone can just tell us...be back...

---

### Post by jerrrys on 2009-06-13
no one came along with an answer hu.  no matter

[http://www.google.com/search?q=reinstall+evolution&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=reinstall+evolution&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by benjamindlevin on 2009-06-13
yes, well its re-installed... but the problem persists.  here is an image, if you do not use this version, so you know what i am talking about specifically. 

[IMG]http://i732.photobucket.com/albums/ww322/nagel69/desktop.png[/IMG]

in the upper left is where the Easy Peasy icon should be.  on the right, my notification area, clock, network connection icon, etc.  and, in the middle where i can minimize and manage my open windows and apps.  

i have now re-installed evolution.  jerrrys, as per your first post... i checked that thread and it was suggested not to delete 3 files... well, re-installing i have been successful in getting 2 of the 3 back.  the one i cannot find is *evolution-documentation.  *reason is unknown.  i have now re-installed evolution with synaptic, then again by source... thoroughly confused and wish i had looked into this before trying anything... lesson learned, just wish i could fix this.  i mean, i can still  use my ubuntu... its just lost some of the ease of use... and has become a real headache.

oh, and labinnsw... tried the killall, and got the message *"gnome-panel:no process killed". *
also, i did not manually backup anything before, so i guess that was a moot question.

---

### Post by jerrrys on 2009-06-13
this worked for me

[ATTACH]117537[/ATTACH]

good luck

---

### Post by benjamindlevin on 2009-06-13
with fingers crossed i checked my installed packages in the hopes that one of those was not installed... they were, so i marked them for re-install and restarted the system (twice) well... no dice... problem persists.  not sure what i did to this thing, i must have pissed off one of the computer gods and am being punished.

another key point is that my internet connection is not always nice to me here.  i am in Iraq, and the internet is slow to the point of, if i try to upgrade to the latest distro... it will take more than 24 hours of constant connectivity.  and, having constant connectivity is an even bigger issue... arg

---

### Post by benjamindlevin on 2009-06-14
thank you very much. 

it wouldnt work for me, so i switched from "Ubuntu Netbook View" to "Classic Desktop View" and i could *add panel*.  so, i added the panel there and then switched back to the netbook view, voila... 

so, thank you both for the pointers it did help.

---

