---
title: "Amarok Crashes"
date: 2005-10-17
forum: Desktop Environments
---

### Post by Valeran on 2005-10-17
Just wondering if anyone else has experienced this.  I am using Amarok in Gnome with the required KDE libraries installed.  If I use it with the Xine engine I periodically get an error messsage about KMail.  If I use the gstreamer engine Amarok will just close without an error.  In either case it runs for random amounts of time before crashing.  It's not a big deal as I have started looking at other media players that are native to Gnome.  I just really liked this one in Hoary and it has been acting up ever since I installed Breezy.

Thanks in advance for any advice.

---

### Post by Dr. Nick on 2005-10-17
Crahed on me to running in gnome, though different crashes than you describe, mine froze when resizing and window inside it.

I have switched to quod Libet myself, it supports plugijns so alot of amarok functionabality can be added

Of course their is always Rhythmbox and Beep seems to be well regarded aswell

---

### Post by lost.sync on 2005-10-18
[QUOTE=Valeran]If I use the gstreamer engine Amarok will just close without an error.[/QUOTE]

same exact problem.  i hope someone knows something about this because i really like amaroK a *lot*.

---

### Post by Valeran on 2005-10-18
For me it's not so much the plugin support.  RB supports all the plugins I need.  It's the interface.  So far I have not found an application that has a similar interface to Amarok.  If anyone knows of one, I am open for suggestions.

---

### Post by Dr. Nick on 2005-10-18
[QUOTE=Valeran]For me it's not so much the plugin support.  RB supports all the plugins I need.  It's the interface.  So far I have not found an application that has a similar interface to Amarok.  If anyone knows of one, I am open for suggestions.[/QUOTE]

When I said plugins I didnt mean just format plugins though, Quod Libet has plugins to display lyrics for songs just like amaroK. 

I know alot of people like amaroK as do I, so I am currently compiling "stripped down" versions of the required kde libraries and then going to compile amarok from scratch and see if I can avoid the crashed I and others have had. This is my 1st time attempting something like this so it may take awhile, Hopefully I can get it done in the next few hours. If  I get it installed and working correctly I will post a howto and .deb files to make it easier if I can find a host. I am compiling on 64 bit though so if what I do does work I will need someone daring enough to compile on a 32bit processor :) My only 32bit would take a few days to compile this lol

---

### Post by Dr. Nick on 2005-10-18
Getting back to the OP, I had gstreamer errors aswell, they just resolved themselves and it finally ran, so I cant help you their. I just always had a crash if I moved or resized any part of the GUI. 

I have since complied from scratch disabling all other output engines except for gstreamer, it ran fine without any errors but I still get the same crash on resizing, though the interface does seem abit snapier. If I can get my crashes to stop I will post how but I am not holding ot much hope :( If you scan the amaorK forum you will see we're not alone, also their have been several threads on these forums recently about crashes. I hope a new version is released soon but I will play with this one for a few more days, but untill amaroK seems more stable im going to still use quod Libet

Sorry I couldnt be of more help :(

---

### Post by mlomker on 2005-10-18
I've always had problems with amaroK from the repositories, so I build my own from cvs.  What you do is remove the Ubuntu version of amaroK, install the various development files that you need to build it, and then use a script [that they provide]("http://amarok.kde.org/amarokwiki/index.php/Get-amarok-svn.sh") to automagically download and compile the new amaroK every few days...or however often you want.  You'll always have the very latest version.

If there's a strong interest then I could write a how-to on what -dev packages need to be installed for the script to run.

---

### Post by Dr. Nick on 2005-10-18
Thanks I may give that a try.
What I did was remove the repository version of amarok, kdelibs, kdebase. Downloaded kdelibs and compiled it without supprt for arts as described here [http://amarok.kde.org/amarokwiki/index.php/KDElibs_without_aRts](http://amarok.kde.org/amarokwiki/index.php/KDElibs_without_aRts)
I then made debian packaes and instaled them, then compiled amaroK without arts support and only had gstreamer, made a deb of it and installed it. It ran just would freeze up like before. I may clean up what i've done and give cvs a whirl, unfortunately i'm short on time right now. If its not to hard a guide may help me or anyone else who hits a roadblock.

Thanks

---

### Post by souled on 2005-10-19
I would like a HOWTO on how to install amaroK from cvs :)

---

### Post by Dr. Nick on 2005-10-19
I dont think they really do CVS anymore , correct me if im wrong. What I see now is a svn build wgich is similar to cvs. Install "subversion" in synaptic and follow these instructions, also need kdelibs and kdelibs-dev, I also had to update automake to contnue it.

[http://amarok.kde.org/amarokwiki/index.php/Installation_HowTo](http://amarok.kde.org/amarokwiki/index.php/Installation_HowTo)
under Building SVN amaroK

This should work But I was un-sucessfull, I would use checkinstall instead instead of make install so you can uninstall the deb easier.

I will try again but just dont have the time now, If anyone gets it please update us, If you have problems post and I may be able to help, you need to build taglib as well, if you dont the ./configure will fail and tell you how. Sorry  I could help alot more :(

---

### Post by mlomker on 2005-10-20
[QUOTE=Dr. Nick]I dont think they really do CVS anymore , correct me if im wrong.[/QUOTE]

You are correct.  I'm not a programmer, so I don't appreciate the differences.  ;)

I'll work on a how-to for this.  You're right--Taglib is the only one that has to be compiled/installed...the rest are just Ubuntu -dev packages.

---

### Post by crispingatiesa on 2005-10-20
I'm having problems with amarok after installing the nvidia drivers. It was working ok and now when trying to start it just quits. Telling me 

amaroK: [Loader] Starting amarokapp..
amaroK: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
amaroK: [Loader] amarokapp probably crashed!

When calling amarokapp I got:
Segmentation fault

funny if I try to run glxgears I have the same segmentation fault.

The nvida driver works (no problems) and everything was working previously.

Any ideas anybody?

Thanks

---

### Post by fanoodlehey on 2005-10-22
I have the same problem as crispingatiesa.

I couldn't get X to start with nvidia as the driver since I upgraded to Breezy, so I just reinstalled the latest nvidia driver. Unfortunately I still can't get nvidia to start so have to start with vesa.

But since the reinstall of the nvidia driver amarok won't start and crashes with
amaroK: [Loader] Starting amarokapp..
amaroK: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
amaroK: [Loader] amarokapp probably crashed!

Seems like a really strange problem.

---

### Post by mlomker on 2005-10-22
> Seems like a really strange problem.

You've already tried a 'complete removal' and reinstall?

---

### Post by fanoodlehey on 2005-10-22
Don't know about the "complete removal". Do you mean amarok or nvidia? I followed the Howto for installation of the latest nvidia drivers. Would this have done a complete removal. I don't want to do a removal or reinstall of amarok since I don't feel that it is at the root of the problem.

Any suggestions for how to continue?

---

### Post by mlomker on 2005-10-22
> Any suggestions for how to continue?

Well, I offered some and you didn't take it.  ;)  I'd try removing amaroK completely and reinstalling it.

I'm going to work on a how-to for compiling amaroK from SVN this morning but that won't solve any problem that reinstalling amaroK won't fix.  I've spent over a week working on the ATI drivers and how-to's on them.  There's **no way** I'm buying an Nvidia!  One brand is headache enough.  :)

---

### Post by fanoodlehey on 2005-10-22
OK. Just tried complete removal and reinstallation of amarok. No joy. Still have the same problem.

---

### Post by fanoodlehey on 2005-10-22
Ah ha. Fixed. My own fault really. When reinstalling the nvidia driver I mistakenly downloaded the 7676 driver from the nvidia website instead of the 7667 driver. Installation of the 7667 driver solved all my problems.

---

### Post by mlomker on 2005-10-22
[Here is my how-to]("http://www.ubuntuforums.org/showthread.php?p=434718") for building amaroK through SVN.

---

### Post by adrian.oneclick on 2008-05-01
figured it out ... sorry

edit: i noticed d' thread is old sorry for reviving it, had same probs.

Peace*

---

