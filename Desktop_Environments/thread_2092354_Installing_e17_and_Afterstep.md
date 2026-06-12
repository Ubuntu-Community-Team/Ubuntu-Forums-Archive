---
title: "Installing e17 and Afterstep"
date: 2012-12-07
forum: Desktop Environments
---

### Post by Iggy64 on 2012-12-07
I'm relatively new to Linux, and I have an old laptop I am using for experimentation.  I gravitated to Ubuntu, and eventually to the LXDE environment.  I currently am running LXDE on Ubuntu 12.04. 

While I am in the experimenting mode, I thought I'd try out the Enlightenment window system (or DE?).  I tried installing from this repository
ppa:hannes-janetzek/enlightenment-svn
but received a lot of error messages during the terminal session.  Later, when I opened the Ubuntu Software Center, I received error messages telling me I had broken dependencies somewhere.  It didn't tell me WHERE, nor did it fix them when it offered to try.  Eventually, I used Synaptic to completely remove e17, and everything seems OK.  However, I'm left wondering why the install didn't work.  Are there some foolproof instructions for installing e17?

Moving along, I installed Afterstep by means of the Software Center.  I looked in Synaptic to see if it showed up, and it is there.  However, I get no option in my Sessions Manager to choose an Afterstep session.  I'm probably totally misunderstanding how Afterstep substitutes for Openbox.  Perhaps someone can explain, and tell me how to try out Afterstep?

Thanks!

---

### Post by TenPlus1 on 2012-12-07
Being relitively new to Ubuntu/Linux and in the mood for experimenting with desktop environments I'd google the one you wish to use and try to find an installation guide for Ubuntu that could help you install and configure it properly...

This link should help with the AfterStep problem:

[http://ubuntuforums.org/showthread.php?t=906990](http://ubuntuforums.org/showthread.php?t=906990)

---

### Post by Frogs Hair on 2012-12-07
I have used the PPA but not with Lubuntu. The PPA worked with 11.10 and 12.04. There are E17 core packages in the _Ubuntu_ repository but they will be older and have limited function compared to the PPA. 

The core packages should work if available; however if they are installed along with the PPA the package system will break.      

Light Ubuntu based E17 distro:[http://www.bodhilinux.com/](http://www.bodhilinux.com/)

---

### Post by Iggy64 on 2012-12-07
Thank you, TenPlus1.  Yes, I had already done a fair amount of research, and had seen the forum thread (on menuizing Afterstep) you mentioned.  But I was too timid to try those instructions.  After your post, I tried to give it a go --- and it worked!  Plus, a learned a little bit more about where Linux (Ubuntu) stores various things.  I really appreciate your help.

And, to Frogs Hair:
Nice of you to take time to comment on e17 installation.  I did already read a little bit about Bodhi, and it sounded interesting.  Maybe I will create a Live CD and check it out.  I really like LXDE on top of Ubuntu, and could be very satisfied with it.  However, I want to do some exploring of other light options before I really settle down into a favorite.

As far as installing e17 goes, I'm not bright/knowledgeable enough (yet) to completely follow your instructions.  It sounds like I definitely want to install it from the ppa.

"The core packages should work if they are available."  I'm not sure what "core packages" means.  Sorry, I need to learn the terminology.  Do you mean the packages that come from the Software Center?

---

### Post by Frogs Hair on 2012-12-08
The basic E17 packages included in the Ubuntu repository. The are listed in synaptic if available for Lubuntu . Make sure you have removed the source for the ppa and run the update manager so the PPA packages are no longer available in synaptic.

---

### Post by konas on 2012-12-08
You can also try this ppa:  [https://launchpad.net/~efl/+archive/trunk](https://launchpad.net/~efl/+archive/trunk)
which is listed on the download page on englightenment.org .

I use it on my ubuntu install, and have no problems with it.

---

### Post by Iggy64 on 2012-12-08
Thanks to Frogs Hair for the additional explanation.  Much appreciated and very helpful.

And I am grateful to konas for pointing out a better ppa.  This install went without any listed errors.  Now it's time to log out and give it a try.

Many thanks!

---

### Post by Iggy64 on 2012-12-09
Well, I THOUGHT the installation from the Enlightenment ppa went OK, because Terminal did not give me any error messages.  However, when I opened an Enlightenment session, I was greeted with a litany of error messages about missing modules.

I went back into Terminal to see what it actually told me during the install:

john@Laptop-61SXY91:~$ sudo apt-get install e17
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  e17
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/2,565 kB of archives.
After this operation, 6,669 kB of additional disk space will be used.
Selecting previously unselected package e17.
(Reading database ... 416957 files and directories currently installed.)
Unpacking e17 (from .../e17_201210091318-14115~precise1_i386.deb) ...
Setting up e17 (201210091318-14115~precise1) ...
john@Laptop-61SXY91:~$ 

It says "Unpacking" and Setting up," but I'm expecting to see something more than just those simple statements.  (Yes, I am really a newb.)

I have no clue what to try next.

---

### Post by Frogs Hair on 2012-12-09
Did you remove the software source from the previous PPA as I wrote ? . I tested the PPA linked by konas last night and it worked fine in Ubuntu.

---

### Post by Iggy64 on 2012-12-09
Thanks for continuing to help me with this, Frogs Hair.

I tried removing e17 using Synaptic, as you suggested.  I also tried it from Terminal, using 

sudo apt-get purge e17
Perhaps neither method was effective.

I think I'm not sure how to do it with Synaptic.  When mark e17 for Complete Removal, Synaptic seems to remove only e17, but not of the other packages that are listed in the window beneath it.  Do I need to mark all those packages, too?  If so, is there any trick for marking them all at once, instead of having to mark them one at at time?  

THanks!

---

### Post by Frogs Hair on 2012-12-09
Open Software Sources > Other Software and make sure that the first E17 PPA source has been removed. This is how they appear in Ubuntu and I think LXDE has a similar application. 

There may be two lines as in Ubuntu. Run the update manager and attempt it install E17 again if you still want to. The first PPA source will cause broken packages if you install E17 from another source.

---

### Post by Iggy64 on 2012-12-09
It is very kind of you to keep trying to help me, even though I am obviously in over my head and probably wasting your time.

I took your advice and checked the Software Sources in Synaptic.  Indeed, the original ppa was still listed (twice); so I deleted these entries.  Now I went back and tried to install e17 again (in Terminal).  This must have been the wrong approach, since I received:

john@Laptop-61SXY91:~$ sudo apt-get install e17
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 e17 : Depends: e17-data (= 0.17.0-beta-1ppa1~precise) but 201210091318-14115~precise1 is to be installed
E: Unable to correct problems, you have held broken packages.

I apologize for stumbling around so much.

---

### Post by Frogs Hair on 2012-12-10
Did you reload synaptic after removing the source and prior to the installation attempt.

---

### Post by Iggy64 on 2012-12-13
I'm feeling more and more foolish, as I probably don't know enough to properly use your instructions.

You said I should "reload synaptic after removing the source."  I'm supposing you mean removing the ppa I used originally, and I did remove that.  I'm really unsure what you mean by "reload synaptic."  

Bottom line is:
I removed the original ppa.
I used Synaptic to clean out all e17 packages.
I used the newer (Enlightenment web site) ppa to re-install e17 in the Terminal.
Still no luck.  Got messages about broken packages and inability to open a locked file.
Used Synaptic to clean up broken packages.  Tried again.  Still no luck.

Now I know I am wasting your time.  I need to make time to study up on Linux in general, on repositories and packages, on Synaptic and more.  I shouldn't keep messing with things that are beyond my current reach.

As an interim solution, I created a Live USB of Bodhi Linux and ran it.  It gives me some idea of what the Enlightenment WM does, since Bodhi uses e17.  I rather like a lot of its features.

Many thanks for all your help and for your patience.

---

### Post by konas on 2012-12-13
> **Iggy64 said:**
> I'm feeling more and more foolish, as I probably don't know enough to properly use your instructions.

You said I should "reload synaptic after removing the source."  I'm supposing you mean removing the ppa I used originally, and I did remove that.  I'm really unsure what you mean by "reload synaptic."  

Bottom line is:
I removed the original ppa.
I used Synaptic to clean out all e17 packages.
I used the newer (Enlightenment web site) ppa to re-install e17 in the Terminal.
Still no luck.  Got messages about broken packages and inability to open a locked file.
Used Synaptic to clean up broken packages.  Tried again.  Still no luck.



I believe there are some leftover packages from the previous ppa. So type "enlightenment" in the search box in synaptic. You should see, besides e17, and e17-data, many lib_something packages (for ex. libedje1, libecore1 etc...), remove all of them, then press the RELOAD button, on the upper left corner, and then install again the e17 package, and the other packages should install automatically.

---

### Post by Frogs Hair on 2012-12-13
> As an interim solution, I created a Live USB of Bodhi Linux and ran it. It gives me some idea of what the Enlightenment WM does, since Bodhi uses e17. I rather like a lot of its features.


_That is the best solution for trying E17_. The reload button in synaptic is on the top left and is the same as running the update manager or the following command. ```
sudo apt-get update
```

---

### Post by Iggy64 on 2012-12-13
Thanks for the added clarification.

After experimenting with Bodhi (and liking it a great deal), I went through the whole sequence of purging e17 packages from my Ubuntu 12.04 machine and having a fresh go at installing it from the official ppa, using the Terminal.  I still ran into a locked file/folder issue at the end, but finally figured out this was due to having left Synaptic open.  Apparently I should only have one package handler open at a time (Synaptic, Installer, Terminal).  Once I got past that, the install (in Terminal) looked OK.

When I logged on in Enlightenment, I still got error messages, telling me I had a host of modules that had something wrong with them (can't remember what).  I was given a choice of removing them or keeping them.  I learned that removing them all (seemed like about 12 to 15 modules) allowed me to proceed.  Now it's up and running, and looking and behaving pretty much like it does in Bodhi.

Can't help but wonder what all those unruly modules were all about.  I guess I should have written down all their names.

Thanks again for all the help.  Now I'll spend some time comparing the relative convenience of LXDE with Enlightenment.

---

### Post by konas on 2012-12-14
I am glad you got it finally working. It's strange though about the modules. I only had this once, when I installed the Bodhi version of e17, and it was only one module (comp-scale or something like that) that needed to be removed.

You can have a look at [http://e17-stuff.org/](http://e17-stuff.org/), there are some nice themes.

---

### Post by Iggy64 on 2012-12-14
Yes, strange about the modules.  I wish I had written down some of the names.  Hopefully, if it turns out I need some of them, I will have an opportunity to add them.

And yes, I did visit the e17-stuff site to grab a couple of nice themes.  Thanks for the tip.

So far, I find e17 just a bit more convenient to navigate (from a GUI standpoint) than LXDE.  I like them both, though.

Next, I need to figure out how to get Nautilus to run in e17, without having Nautilus drag in its own desktop.  (So far, Nautilus is the only file manager I have found that lets me drag and drop, show a tree in the left pane, search for files, and show file details.)  I have found some suggested solutions to blocking the Nautilus desktop, but they appear to no longer work under the current versions of Ubuntu and Nautilus.

Thanks for all the help!

---

### Post by Frogs Hair on 2012-12-14
When using E17 on top of a Ubuntu distro use the E17 file manager or nautilus takes over the desktop. You may want to consider dual booting with Bodhi if you have the resources and feel comfortable with doing so.

---

### Post by Iggy64 on 2012-12-14
You know, I actually thought about setting up a dual boot; but I've never done a Linux/Linux dual boot.  (Always Linux/WinXP.)  I have plenty of room to dual boot Bohdi.  

Could I somehow use Nautilus as a file-manager-only in Bohdi?  This is certainly not a deal breaker; I just seem to get everything done faster with Nautilus than other FM's I've tried.  I do lots of batch file moves, file searches, USB mounts/dismounts, and so on.  Nautilus seems to handle all these things rather well.  However, I can just chuck Nautilus and use some combination of two or three other tools.

Thanks for all the continuing advice.

---

### Post by Frogs Hair on 2012-12-14
> **Iggy64 said:**
> You know, I actually thought about setting up a dual boot; but I've never done a Linux/Linux dual boot.  (Always Linux/WinXP.)  I have plenty of room to dual boot Bohdi.  

Could I somehow use Nautilus as a file-manager-only in Bohdi?  This is certainly not a deal breaker; I just seem to get everything done faster with Nautilus than other FM's I've tried.  I do lots of batch file moves, file searches, USB mounts/dismounts, and so on.  Nautilus seems to handle all these things rather well.  However, I can just chuck Nautilus and use some combination of two or three other tools.

Thanks for all the continuing advice.

I would check out their forum and ask what is available in the Bohdi repository because were now into the "other operating system" category. Bodhi is Ubuntu based though.

---

### Post by Iggy64 on 2012-12-17
Thanks for all the extra advice.  I did install Bodhi and am getting comfortable with it.  It may give LXDE a run for its money.

I have gotten Nautilus to coexist peacefully with e17 by modifying its launcher 

(changing     nautilus %U   to    nautilus --no-desktop)

The only remaining problem I discovered is that nautilus gives aliases to certain desktop files, instead of showing their true filenames.  That's a disappointment.

So far, Bohdi "feels" about as fast as LXDE, and that is very nice.  

The only minus: The Ubuntu Software Center isn't functioning well on my Bodhi installation.  I installed it, and it opens OK, and it  shows the packages.  It just doesn't install them when I click "install."  So I install through the Terminal.

Again, thanks for the help.

---

