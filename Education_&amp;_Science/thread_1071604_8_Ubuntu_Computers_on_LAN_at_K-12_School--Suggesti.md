---
title: "8 Ubuntu Computers on LAN at K-12 School--Suggestions?"
date: 2009-02-16
forum: Education &amp; Science
---

### Post by LaneLester on 2009-02-16
I'm the only science teacher at a small K-12 private school. I have very little money to spend, but I just dropped $200 for 8 refurbed systems loaded with Ubuntu (my main OS at home). Yes, $25 apiece including monitor, keyboard, mouse, NIC, & CD reader. There's an organization here that receives gift computers and fixes them up.

I have a DSL line, Linksys WRT54GLinux router, and two switches to connect everything together. This puts two machines at each student table to support 4 students. These are the tables at which the students sit for a daily 50-minute class period, all period. My largest class is 13 students, but I can handle 16 with this setup.

The point of this thread is to seek suggestions of the best way to utilize this network. I know to find good websites for the students to do simulated labs and such, but I'm wondering if you have some ideas about how the network can be used in-house to enhance learning.

Are there software packages that might be useful?

Lane

---

### Post by hubie on 2009-02-17
Are you asking within the context of science, or do you mean more from the angle of teaching about computers and networking?

The computers and networking angle is covered pretty nicely over in [this thread]("http://ubuntuforums.org/showthread.php?t=907449").

If you are talking about science or more educationally-related, there is, of course, the software listed on the [Edubuntu site]("http://edubuntu.org/").  All of that software should install easily.

If you are talking about specifically using the idea of software that uses a network of computers, then I would have to give that some more thought.  There is the [BOINC-type]("http://boinc.berkeley.edu/") programs.  Those are easy to set up and run, but I don't know what the teaching value would be in them unless you want to dig into the code.

The other angle might be client/server type of software.  If that is what you are thinking about, I would have to give that some thought as well.

---

### Post by LaneLester on 2009-02-17
> **hubie said:**
> Are you asking within the context of science, or do you mean more from the angle of teaching about computers and networking?
I'm thinking more in terms of using the network to manage learning experiences, and based on someone else's advice, I'm going to give a look at both Moodle and BuddyPress. But I hope to teach the students some basic stuff about computers along the way, particularly the effective use of the Web.

Thanks for the links; they will provide some good information for consideration.

Lane

---

### Post by ugm6hr on 2009-02-17
I am not a teacher, but had some thoughts you might like to consider.

Since you essentially have 1 spare computer (you only need 7 for 13 students), reinstall a Server OS (Ubuntu would be fine) on one.  You could then install moodle (or an alternative course management - I like Dokeos) and a wiki (for the students to create their own learning material - an alternative to creating posters etc).

Not sure if it is a good idea in school, but you could also create a local IM network or bulletin-board that archives all comments (meaning you can track abuse) to allow collaboration at a class level rather than just in pairs.  By giving certain students leadership roles in this scenario, they *may* surprise you with their maturity.

Let us know how this works out.

---

### Post by kerry_s on 2009-02-17
look into edubuntu and ltsp, it will be a lot easier to manage that many computers with ltsp and a lot safer.

---

### Post by ugm6hr on 2009-02-17
> **kerry_s said:**
> look into edubuntu and ltsp

Doesn't this require a server with minimum 256MB RAM per terminal?  I think the hardware described will not support this.

---

### Post by LaneLester on 2009-02-17
> **ugm6hr said:**
> I am not a teacher, but had some thoughts you might like to consider.
I really appreciate the suggestions I'm getting. My experience with installing and running a server has been limited and unpleasant. I have server space on the Internet, so I'm planning to use that for Moodle or whatever. That will have the extra advantage of allowing me (and the students) to work on the system from home.

I've installed Moodle and BuddyPress, and I've decided not to do any more with BuddyPress for now. It's WordPress Multi-user with lots of custom plugins. It looks like it could be quite complicated to learn and use.

I'm interested in your preference of Dokeos. Did you adopt that instead of Moodle? Do you see advantages of Dokeos over Moodle?

Lane

---

### Post by kerry_s on 2009-02-17
> **ugm6hr said:**
> Doesn't this require a server with minimum 256MB RAM per terminal?  I think the hardware described will not support this.

i don't think so? i can't find any info for that on: [http://www.ltsp.org/](http://www.ltsp.org/)
however the k12ltsp says:
[http://www.k12ltsp.org/install.html](http://www.k12ltsp.org/install.html)

i also found the ubuntu instructions:
[https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall](https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall)

---

### Post by LaneLester on 2009-02-17
> **kerry_s said:**
> i don't think so? i can't find any info for that on: [http://www.ltsp.org/](http://www.ltsp.org/)
however the k12ltsp says:
[http://www.k12ltsp.org/install.html](http://www.k12ltsp.org/install.html)
Thanks for the info, Kerry! I checked the K12 site, and it looks like the RAM requirements are still too large for me. I suspect I'm best off with my current setup of Ubuntus on each machine and letting servers on the Web do the heavy lifting.

Lane

---

### Post by ugm6hr on 2009-02-17
The Edubuntu wiki: [https://help.ubuntu.com/community/EdubuntuDocumentation/EdubuntuCookbook/HardwareRequirements](https://help.ubuntu.com/community/EdubuntuDocumentation/EdubuntuCookbook/HardwareRequirements)

Suggests 256MB + 128MB / client RAM for LTSP; so I remembered that wrong.  Nevertheless, that's 1.5GB for a server in this context.

If you are using a paid-for webserver, then Moodle is probably an easier option, since many web-hosts have one-click install available for Moodle.  It is arguably more powerful for true educational purposes than Dokeos, and is used widely in higher education in the UK.

I have personally found the Dokeos interface much cleaner, and its handling of SCORM e-learning content better, which was important for my site (still a work in progress - and still being hosted on a free web-host which keeps breaking [http://ugm6hr.jwnmedia.com/](http://ugm6hr.jwnmedia.com/) ).  My reading of the situation was that Dokeos hardware requirements are lower from the server too, although that may have been biased reports from happy users!

I suspect that your web-host will be able to install a Wiki for you too, which I think will likely be more useful than BuddyPress, which, as you say, appears to try and replicate social networking sites capabilities.  Seeing as you are using the web anyway, if you need collaboration software, you could just use any of the free online ones. e.g Google / Yahoo groups.

---

### Post by LaneLester on 2009-02-18
> **ugm6hr said:**
> If you are using a paid-for webserver, then Moodle is probably an easier option, since many web-hosts have one-click install available for Moodle.
I was able to single-click install Moodle on my account, and I'm now setting it up for my classes.

> Seeing as you are using the web anyway, if you need collaboration software, you could just use any of the free online ones. e.g Google / Yahoo groups.
I'll see how much collaboration, etc. I can get out of Moodle, and if further capabilities are needed, I'll look for others.

Thanks again for the help.

Lane

---

### Post by LaneLester on 2009-02-18
The 8-computer LAN is in place... well, really 9 since I added one on my desk. Moodle is coming along.

But I'd like to configure some functions that don't require the Internet or a local server. I would like the students to be able to create a document on their machines and then save it to a directory on my machine.

However, when I clicked Sharing Options on the directory I wanted to use, it said I had to install a Windows routine to do that. Windows? I guess that means Samba, but isn't there a pure Linux way to share a directory? Or is this a lot more convenient?

Lane

---

### Post by ugm6hr on 2009-02-19
I'd suggest posting a specific question in the Networking section about that.

Samba (SMB) is an option.  I think ssh is probably not what you want, since it would require the students to have a login on your computer.  I think CFS is the other option, but I don't know much about it.

---

### Post by torry_loon on 2009-02-19
If there are no Windows machines on the network, NFS is what you need for sharing files across the network in Linux.
For example, you could store the /home directories on a server and mount them on each client computer.

Have a look at [this page]("https://help.ubuntu.com/8.04/serverguide/C/network-file-system.html") in the Ubuntu Server Guide to configure NFS.

---

### Post by LaneLester on 2009-02-20
> **torry_loon said:**
> If there are no Windows machines on the network, NFS is what you need for sharing files across the network in Linux.
I might give NFS a try. Although I've always found it easy to share files between Linux and Windows computers, I've not had much success with sharing between Linux machines... go figure.

Lane

---

