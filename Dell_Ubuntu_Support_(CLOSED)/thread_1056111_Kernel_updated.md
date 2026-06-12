---
title: "Kernel updated"
date: 2009-01-31
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Arndtwe on 2009-01-31
I purchased a Dell mini 9 a few months ago and love it!! When I bought it I also bought a 2 gig memory stick... To my disappointment, only 883Mb were detectable by the kernel. A few days ago I did an update, and now I can use all gigs, great! But one thing that is still a mystery to me... Why wont my version of ubuntu (8.04 hardy) allow me to upgrade to 8.10? It doesn't even detect a new version is out there... has anyone else had this problem, and found a solution? Please help, I would like to upgrade to 8.10.

Also, if I do get it to upgrade... Will anything on my current setup be lost or changed? e.g. my theme, the buttons on my panel, programs that I have installed... Thanks for all and any help!! :-)

---

### Post by prshah on 2009-01-31
> **Arndtwe said:**
> Why wont my version of ubuntu (8.04 hardy) allow me to upgrade to 8.10? It doesn't even detect a new version is out there... 

Also, if I do get it to upgrade... Will anything on my current setup be lost or changed?

The 8.04 version is an LTS (Long Term Support) version, and it may be setup to only upgrade to another LTS. To check / change this setting, look in System-Administration-Software Sources-Updates-"Release Upgrade" and change the settings from "Long term support releases only" to "Normal releases" to allow upgrades to non-LTS versions as well.

If you upgrade successfully, nothing should change (Theme, background etc). Obviously the setup will change. Also note that if you've used non repository software (eg, compiz extensions) these may cause problems in the newer version.

---

### Post by Arndtwe on 2009-01-31
I have already set up my update manager to allow "normal releases" and yet it will notlet me upgrade... I cannot figure out why this wont work.

---

### Post by buzzware on 2009-01-31
> **Arndtwe said:**
> I have already set up my update manager to allow "normal releases" and yet it will notlet me upgrade... I cannot figure out why this wont work.

The Dell repositories do not have 8.1 yet.  They probably won't update until there is a new LTS version.  They also seem to be a bit behind on other updates as well.

---

### Post by Arndtwe on 2009-01-31
Here is some documentation of what I am working with.
These are the screenshots of how I have my software sources set up under "System>Administration>Software Sources"
[IMG]http://i203.photobucket.com/albums/aa289/joearndt/Screenshot-3.png[/IMG]
[IMG]http://i203.photobucket.com/albums/aa289/joearndt/Screenshot-2.png[/IMG]
[IMG]http://i203.photobucket.com/albums/aa289/joearndt/Screenshot-1.png[/IMG]
[IMG]http://i203.photobucket.com/albums/aa289/joearndt/Screenshot.png[/IMG]

Something else that may be found useful is this error box that pops up after running the updat manager. If there are updates it still allows me to do them, but this error wont stop coming up. Can anyone tell me how to solve this problem?
[IMG]http://i203.photobucket.com/albums/aa289/joearndt/Screenshot-4.png[/IMG]

I hope that this information can help someone help me to get this fixed. Thanks for any help in advance!!

P.S. If you are wanting to help, but need more info, let me know and I'll try to provide it.

---

### Post by s3kt0r on 2009-01-31
Just new in the topic, but my guess is that dell's server is not working? 
Or like buzzware replied, they just don't make available normal release updates, even though you select it to be so?

---

### Post by ugm6hr on 2009-01-31
If you want 8.10, there are plenty of tutorials on installing it on the Mini 9.  Not sure whether the LPIA kernel is pre-packaged with Intrepid yet though.

The standard ubuntu repos do not have lpia architecture support - hence the errors on update manager.  You may as well untick them.

If you want non-Dell updates, you will have to manually add the netbook repos:
[http://dell-mini.archive.canonical.com/dists/](http://dell-mini.archive.canonical.com/dists/)

As you can see, no Intrepid repo is present yet.  As far as I know, these are hosted by Canonical for all the LPIA Netbook versions of Ubuntu (inc Toshiba etc).

PS: Found this [http://mydellmini.com/forum/8-10-lpia-iso-who-have-tried-it--t2943.html-st=0&sk=t&sd=a&sid=2f4e34cf535006ce8673f7a85ae2f078](http://mydellmini.com/forum/8-10-lpia-iso-who-have-tried-it--t2943.html-st=0&sk=t&sd=a&sid=2f4e34cf535006ce8673f7a85ae2f078) but not sure it is recommended.

---

### Post by buzzware on 2009-01-31
Arndtwe, since you are using Hardy, I have an off-topic question.  What is that theme?

Thanks!

---

### Post by Arndtwe on 2009-02-01
buzzware, to answer yuor question my theme is Slickness-black... It's pretty cool.

---

### Post by stopie on 2009-02-01
Heres what I found. 

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

If you made a separate partition for your /home, then you can just use a liveUSB of 8.10 and delete your / partition and recreate it. I'd recommend having a separate partition for your /home incase your like me and tend to mess things up when you try and fix them :P

Edited because I can't read!

---

### Post by superm1 on 2009-02-01
> **Arndtwe said:**
> I purchased a Dell mini 9 a few months ago and love it!! When I bought it I also bought a 2 gig memory stick... To my disappointment, only 883Mb were detectable by the kernel. A few days ago I did an update, and now I can use all gigs, great! But one thing that is still a mystery to me... Why wont my version of ubuntu (8.04 hardy) allow me to upgrade to 8.10? It doesn't even detect a new version is out there... has anyone else had this problem, and found a solution? Please help, I would like to upgrade to 8.10.

Also, if I do get it to upgrade... Will anything on my current setup be lost or changed? e.g. my theme, the buttons on my panel, programs that I have installed... Thanks for all and any help!! :-)
The important question before you ponder an upgrade is what's in 8.10 that you need/want?  If you can't name any specific items that you need or want, than why do you want to switch?

If you determine that you do want to switch, you will have to do a reinstall with 8.10.  The 8.04 based distribution is customized and uses a custom architecture (lpia) that is not available to do dist-upgrades as you would a normal 8.04 install.

---

### Post by prshah on 2009-02-03
> **Arndtwe said:**
> I have already set up my update manager to allow "normal releases" and yet it will notlet me upgrade...

You can also download the ubuntu 8.10 "alternate" CD and run an upgrade from that. (You will be automatically prompted to upgrade when you insert the CD).

---

### Post by superm1 on 2009-02-03
> **prshah said:**
> You can also download the ubuntu 8.10 "alternate" CD and run an upgrade from that. (You will be automatically prompted to upgrade when you insert the CD).
Not for an LPIA based install.  You'll need an 8.10 LPIA disk to do that then.

---

### Post by crewkid89 on 2009-02-03
You could do a standard ubuntu 8.10 install.  As I understand it, Dell only uses LTS releases for their computers because they tend to be more stable.  Ubuntu 9.10 maybe?

---

### Post by Arndtwe on 2009-02-03
...And besides Dell not having support for 8.10, I would need a CD drive on the laptop to do that... I suppose though, that I could burn the ISO to a thumb drive to solve that problem. But in the end, I really don't care enough to go through the trouble only to "hope" that everything runs smoothly. So, I will stick with 8.04 for now.

Off-topic question, and completely unrelated... Does anyone know of any bowling management software for Ubuntu? Something that doesn't cost money would be what I'm looking for. I am not picky at all, so if it doesn't interface througha pretty GUI, or heck, even a GUI at all that's kosher. Thanks for any help in advance!!

---

