---
title: "Looking for Gnome Panel Applet to Display IP Address"
date: 2005-11-25
forum: Desktop Environments
---

### Post by Limulus on 2005-11-25
Right now, I can find out my IP address if I go to the Network Monitor Gnome Panel Applet, right-click, Select Properties and click on the Support tab.  I find that annoying :)

What I really want is a Gnome Panel Applet (not a gDesklet) that simply displays my IP address in plain text in the Gnome Panel (e.g. "192.168.0.101").

I've looked quite a bit in Synaptic and couldn't find anything.  Nor did my Google search turn up anything.  Does anyone know of such an applet?

---

### Post by Gudanov on 2006-08-22
Are you still looking for one? I'm writing one as a sort of learning exercise and it is working if you want to do a manual install. It's pretty simple to install manually, you just need to stick two files in the proper place and make sure you have python installed.

---

### Post by Limulus on 2006-08-22
> **Gudanov said:**
> Are you still looking for one? I'm writing one as a sort of learning exercise and it is working if you want to do a manual install. It's pretty simple to install manually, you just need to stick two files in the proper place and make sure you have python installed.

Wow, yes I am! =D

(I'm glad I stayed subscribed to this thread :)

I think that python is installed by default in Ubuntu (regardless, I have it :)  Just let me know where your website is and the instructions, thanks!

---

### Post by Gudanov on 2006-08-22
Okay, you can get the files from [http://www.artfulx.com/giplet](http://www.artfulx.com/giplet) there is giplet.py and GNOME_GipletApplet.server. You need to put giplet.py into /usr/local/bin and make sure it is executable by all (chmod a+x giplet.py). Then you need to put GNOME_GipletApplet.server into /usr/lib/bonobo/servers. If all goes well then you should be able to add it to a GNOME panel. It works on two machines with Ubuntu right now, so I think it should work. 

It aquires the ip address when the applet is started, so on add or whenever a GNOME session is started and it checks 'eth0' for the ip. I'll add more stuff to it, this is just sort of a starting skeleton.

It can also be set to use an internet server to get its ip address if you are behind a router and are wanting the ip address on the router rather than your computer's ip address, but it requires a little code change.

---

### Post by Limulus on 2006-08-23
Cool! Its perfect! Exactly what I wanted! Thanks so much! =D

OK, just a pair of questions now:

Have you decided what license to release it under? (might I suggest the GPL? ;)

Are you planning on making it into a DEB and if not, would you like me to try? :)

---

### Post by Gudanov on 2006-08-23
I'm planning on GPL and it would be great if you made a .deb out of it.

There are few things I want to do to it. I need to organize the script a bit better and add an about box and a properties page. Then I need to set up a few options, like which ethernet connection to look at, whether to get an external ip or interal ip, and how often to refresh. I also need to fix the background of the applet.

But a deb out of this version would be cool, that's what the term alpha is for after all.

---

### Post by Limulus on 2006-08-23
> **Gudanov said:**
> I'm planning on GPL and it would be great if you made a .deb out of it.

Spiffy! :)

[http://members.shaw.ca/Limulus/Conrad/giplet.deb](http://members.shaw.ca/Limulus/Conrad/giplet.deb)

This is the first time I've made a DEB other than a metapackage; it worked on my system (Ubuntu Dapper).  If anyone reading this thread feels like trying it, please post your experience here :)

Note: it may take a few moments after installation before it shows up in the "Add to Panel" window.  It will show up at the bottom under "Utility" as "Giplet".

---

### Post by Gudanov on 2006-08-24
I updated the applet and replaced the files at [www.artfulx.com/giplet](www.artfulx.com/giplet) 

The new file giplet_globals.py should reside at the same location as giplet.py (/usr/local/bin is my usual location) and does not need to be executable.

It now will adjust to the panel background, has a proper about box, goes into Utilties instead of Utility in the add applet window, and has a different stock gnome icon. 

Once I get in the properties it will be ready to move to a proper home someplace and should be pretty functional for the little thing it does.

Shoot me your name and I'll add you to the credits for DEB packaging.

---

### Post by Limulus on 2006-08-25
> **Gudanov said:**
> I updated the applet and replaced the files

I've updated the DEB; same URL :)

---

### Post by Limulus on 2006-08-25
> **Gudanov said:**
> You need to put giplet.py into /usr/local/bin
A member of my local LUG pointed out some issues with my DEB package ([http://list.slg.org/200608/11408.html](http://list.slg.org/200608/11408.html)), but one of the more important ones is that DEBs aren't supposed to install items into /usr/local as per lintian (the DEB package checking program).

I checked another Gnome applet that I use, bubblemon, and it creates a directory /usr/lib/bubblemon so can we move the two files that are now in /usr/local/bin to /usr/lib/giplet ?  Would the only change in the server file  be to change location="giplet.py" to location="/usr/lib/giplet/giplet.py" or some such?

---

### Post by Gudanov on 2006-08-25
That should work fine. At some point I needed to stash stuff into a directory anyway since it will need more files than the main script.

Thanks for working on the DEB.

---

### Post by Limulus on 2006-08-26
> **Gudanov said:**
> That should work fine. At some point I needed to stash stuff into a directory anyway since it will need more files than the main script. Thanks for working on the DEB.

Thank you for writing the applet! :)

BTW, I managed to get the DEB in good enough shape that lintian is no longer giving me error messages so I've uploaded a new version (0.1-2).

---

### Post by Limulus on 2006-08-26
Say... who wants to see a screenshot? :)

[IMG]http://members.shaw.ca/Limulus/files/GnomePanelRight.png[/IMG]

Left to Right: Notification Area, Timer Applet, Bubbling Load Monitor, GNOME Sensors Applet, Battery Charge Monitor, Network Monitor, Giplet, GNOME Lunar Clock, Clock, Quit

---

### Post by Gudanov on 2006-08-29
I've updated Giplet again. This time I've added preference settings that allow the selection of how to obtain the ip address so you can see how the outside world views your ip or how your computer sees its ip. Also, it can also be set to check every few minutes to see if the ip address has changed. It's available at [http://www.artfulx.com/giplet](http://www.artfulx.com/giplet) as a tarball now using the common './configure', then 'make install' commands to install.

---

### Post by Limulus on 2006-08-30
I've added Giplet to the list of applications to be considered for Ubuntu's Universe repository:

[https://wiki.ubuntu.com/MOTU/Packages/Candidates](https://wiki.ubuntu.com/MOTU/Packages/Candidates)

---

### Post by Gudanov on 2006-09-01
Giplet has a home.

[http://sourceforge.net/projects/giplet]("http://sourceforge.net/projects/giplet")

It also has a new version 0.1.2 and a tarball that isn't broken this time.:oops:

---

### Post by braddcadd on 2006-09-02
Thanks to both of you, I really enjoyed reading this thread.  This is OpenSource at work!

I'm downloading the file from Sourceforge now.  I am installing Ubuntu on a friends computer.  With the ip address so handy, he can call me for vnc help.

Nice job.

---

### Post by Gudanov on 2006-09-02
Let me know if there are any problems or something that can work better. This is my first GNOME Panel Applet, the first time I've used Python, and the first time I've used autotools to generate the scripts and Makefiles.

---

### Post by Limulus on 2006-09-17
Sorry for the DEB delay folks!  Here's 0.1.2 as a working DEB :)

[http://members.shaw.ca/Limulus/Conrad/giplet0.1.2-1.deb](http://members.shaw.ca/Limulus/Conrad/giplet0.1.2-1.deb)

Note, again: it may take a few moments after installation before it shows up in the "Add to Panel" window (just try again in a few seconds). It will show up under "Utilities" as "Giplet".

---

### Post by trash on 2006-09-17
I haven't installed it yet but it looks awesome.. I use gnomemeeting and find it annoying as all hell that I have to search for my IP.
Just thought I would mention ppc could use this tool to.:)
thanks!

---

### Post by Gudanov on 2006-09-17
> **trash said:**
> 
Just thought I would mention ppc could use this tool to.:)


It's written in python, so it's processor independent. Should work with ppc computers if python is installed (and libglade and pygtk). 

BSD is an issue though, by default it won't point to the correct interface. When I get a chance I'm hoping to fix that up. I need to find the right calls to get the list of ethernet interfaces and provide a dropdown instead of a text field.

---

### Post by Limulus on 2006-09-18
> **Gudanov said:**
> It's written in python, so it's processor independent. Should work with ppc computers if python is installed (and libglade and pygtk).

When I created the DEB I set the architecture field to "all" and the only dependency for "python" so it should install on any Ubuntu system.  For those with PPC, please try the DEB out :)

---

### Post by trash on 2006-09-18
installed ok on ppc but I am running xfce and it won't show up in the panel add list... kinda forgot there are those small differences between gnome and xfce lol

---

### Post by Gudanov on 2006-09-18
Are you using [xfapplet]("http://goodies.xfce.org/projects/panel-plugins/xfce4-xfapplet-plugin") to try to display the applet in XFCE? 

I haven't tried to run the applet in XFCE with xfapplet yet.

---

### Post by trash on 2006-09-18
> **Gudanov said:**
> Are you using [xfapplet]("http://goodies.xfce.org/projects/panel-plugins/xfce4-xfapplet-plugin") to try to display the applet in XFCE? 

I haven't tried to run the applet in XFCE with xfapplet yet.

Thats what was needed. it's good on xfce ppc. Thanks:KS

---

### Post by Limulus on 2006-10-28
> **Limulus said:**
> When I created the DEB I set the architecture field to "all" and the only dependency for "python" so it should install on any Ubuntu system.

I just upgraded to Edgy and thought I should mention that Giplet still works perfectly :)

---

### Post by trash on 2006-10-28
me to:) but for some reason it only worked after i downgraded to the one in the repos(ppc).
giplet1.2-1 -> giplet1.2

---

### Post by Limulus on 2006-11-18
> **trash said:**
> me to:) but for some reason it only worked after i downgraded to the one in the repos(ppc).
giplet1.2-1 -> giplet1.2

You know what, I TOTALLY missed what you were saying.  Only today (by accident when testing Feisty) did I just realize that Giplet is in the Ubuntu universe repositories as of Edgy! =D

And since the MOTU team is now in charge of this, I can happily retire from DEB-making (at least for now ;)

---

### Post by trash on 2006-11-18
It was an accident when I found it in the repos as well and I was a bit baffled by it since it was also my first time using GDebi, which reported to me that there is one in the repos and it was recommended that I use it!

Thanks again!

---

