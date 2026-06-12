---
title: "Arghhh Beryl"
date: 2007-03-24
forum: Desktop Effects &amp; Customization
---

### Post by CorranSW on 2007-03-24
i have posted quite a few times about installing beryl, i have followed numerous guides and hosed my partiiton numerous times.... I was suggested that i post my system specs and that might help? 
Nvidia 7900GTX
AMD 4800+
200gig HDD
2 gigs of ram
Asus A8n SLI deluxe mobo
Sounds card etc....
Well if anyone can help i am willing to follow a few more guides, also if anyone here has teamspeak or ventrilo i have my own server and i think talking to somone might be a tad easier then typing...
At this point i am open to anything.
(Also i am downloading feisty as i type i heard it auto installs Beryl maybe it will be my savior)

---

### Post by ThrobbingBrain66 on 2007-03-24
Along with your specs, it would be good to tell us about the problems you've been experiencing with Beryl.  Being able to pinpoint the issue will help to resolve it.

Feisty doesn't auto install Beryl, it comes with Compiz pre-installed, but not enabled.

---

### Post by bulldog on 2007-03-24
Well you heard wrong I'm afraid.
It has compiz preloaded and you can activate it,but Beryl you'll have to install.

But that's easy to do,I have Beryl and Emerald running with Feisty, and of course there can be a little trouble from time to time,it run's very well indeed.

---

### Post by CorranSW on 2007-03-24
well jee were do i start.... first of all the nividia drivers didnt seem to enable themselves so i edited the line "nv" like it said in the forums to "nvidia". Well i saved this came back on and the OS did'nt load so i had to hose my drive and start from scratch... I used the notepad thing to edit the nvidia text because terminal loaded a blank document when i tryed to edit the nividia script on there.

---

### Post by CorranSW on 2007-03-24
Also as i said if anyone here has voice communications a have a laptop running next to my desktop so that might hlep alot...

---

### Post by mrmonday on 2007-03-24
Which guides have you tried to follow?

I followed the official guide and it worked the first time.

---

### Post by SBFC on 2007-03-24
> **bulldog said:**
> Well you heard wrong I'm afraid.
It has compiz preloaded and you can activate it,but Beryl you'll have to install.

But that's easy to do,I have Beryl and Emerald running with Feisty, and of course there can be a little trouble from time to time,it run's very well indeed.

And you installed Beryl from the Feisty repos? I just upgraded to the feisty beta, and when I tried installing Beryl from the repos it complained about not being able to install 'beryl-plugins'. There is no package by that name.

---

### Post by Hevoos on 2007-03-24
Try to install the nvidia drivers with envy. Install the program and type 'envy' into a terminal.

---

### Post by old_geekster on 2007-03-24
> **CorranSW said:**
> i have posted quite a few times about installing beryl, i have followed numerous guides and hosed my partiiton numerous times.... I was suggested that i post my system specs and that might help? 
Nvidia 7900GTX
AMD 4800+
200gig HDD
2 gigs of ram
Asus A8n SLI deluxe mobo
Sounds card etc....
Well if anyone can help i am willing to follow a few more guides, also if anyone here has teamspeak or ventrilo i have my own server and i think talking to somone might be a tad easier then typing...
At this point i am open to anything.
(Also i am downloading feisty as i type i heard it auto installs Beryl maybe it will be my savior)
You have almost the same rig as mine.  I am running "Beryl" with no problems.  

Here is what I did.

Update your nVidia drivers to the latest version.  Use this guide:

[http://www.ubuntuforums.org/showthread.php?t=336412&highlight=Hub](http://www.ubuntuforums.org/showthread.php?t=336412&highlight=Hub)

I know there are many such guides, but this one has worked for me several times.  My idea of trouble-shooting is a "clean install".  I have done this 13 times in the past month.  Each time I have to reinstall the nVidia drivers and I use this guide.  Follow it to the "T" and it will work.

Second, use "Automatix Bleeder", not "Automatix2", to install Beryl.  I did and it worked the first time.  I had tried every other conceivalbe method --- none was successful.

Add this to "sudo gedit /etc/apt/sources.list":

#AUTOMATIX BLEEDER REPOS START
deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy main
#AUTOMATIX BLEEDER REPOS END

Then, install it from "Synaptic Package Manager".  It will install Beryl 2.0.  Once it is installed, you should run "Update Manager".  This will update Beryl so that it doesn't cause Java problems.

I know this sounds a bit newbish to some of you, but it worked for me.:) 

Good luck!

---

