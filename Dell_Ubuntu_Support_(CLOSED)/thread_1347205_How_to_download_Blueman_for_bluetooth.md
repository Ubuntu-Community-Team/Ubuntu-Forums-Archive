---
title: "How to download Blueman for bluetooth"
date: 2009-12-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by bmman on 2009-12-05
I want to use the Bluetooth capability in my Dell Netbook (running Ubuntu 8.04) and apparently need to download Blueman. This, I am having trouble doing. The following error message resulted

E: Malformed line 15 in source list /etc/apt/sources.list (URI parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.ed

Can anyone point out what I'm doing/not doing wrong??

---

### Post by michael37 on 2009-12-06
> **bmman said:**
> I want to use the Bluetooth capability in my Dell Netbook (running Ubuntu 8.04) and apparently need to download Blueman. This, I am having trouble doing. The following error message resulted

E: Malformed line 15 in source list /etc/apt/sources.list (URI parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.ed

Can anyone point out what I'm doing/not doing wrong??

Which netbook? Mini 10?  

What kind of changes did you make to your /etc/apt/sources.lits?

U got to give us more details.

---

### Post by bmman on 2009-12-06
> **michael37 said:**
> Which netbook? Mini 10?  

What kind of changes did you make to your /etc/apt/sources.lits?

U got to give us more details.

I'm using the mini 9 netbook.

I tried typing "cat /etc/apt/sources.list" into the terminal. This dropped the cursor down to the next line, but I wasn't asked for my password (as when I entered "sudo getit /etc/apt/sources.list") 
and therefore was not directed to the sources.list page. In other words, there was no post.
When I typed in the sudo getit..... line I was directed to the sources.list page, which had the following post on it:

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy main universe multiverse restricted 
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy main universe multiverse restricted 
 
deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-updates main universe multiverse restricted 
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-updates main universe multiverse restricted 
 
deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-security main universe multiverse restricted 
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-security main universe multiverse restricted 
 
deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-netbook-base main universe multiverse restricted 
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-netbook-base main universe multiverse restricted 
 
deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-dell-mini main universe multiverse restricted 
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-dell-mini main universe multiverse restricted

I had tried entering 
deb [http://ppa.launchpad.net/blueman/ppa/ubuntu](http://ppa.launchpad.net/blueman/ppa/ubuntu) hardy main 
in a different way, which brought up the error message. I have since backed that line out, and now the error message is gone. But I still can't seem to get Blueman to Save.

---

### Post by michael37 on 2009-12-08
> **bmman said:**
> I'm using the mini 9 netbook.


Which version of Ubuntu are u running?

---

### Post by gradinaruvasile on 2009-12-08
He is using 8.04 (first post).

And what is exactly the problem (besides the repository one)?

Also you might consider upgrading to a newer version of Ubuntu (i recommend 9.04).

---

### Post by michael37 on 2009-12-09
Follow these steps

Select System -> Administration -> Software Sources

Type in your password

Click on Third-PArty Software tab

Click on +Add

In the APT line, type in 
deb [http://ppa.launchpad.net/blueman/ppa/ubuntu](http://ppa.launchpad.net/blueman/ppa/ubuntu) hardy main 

Click on Add Source

Answer OK when it asks you to reload.

Then select System -> Administration -> Synaptic Package Manager

and search for blueman

---

### Post by bmman on 2009-12-14
> **michael37 said:**
> Follow these steps

Select System -> Administration -> Software Sources

Type in your password

Click on Third-PArty Software tab

Click on +Add

In the APT line, type in 
deb [http://ppa.launchpad.net/blueman/ppa/ubuntu](http://ppa.launchpad.net/blueman/ppa/ubuntu) hardy main 

Click on Add Source

Answer OK when it asks you to reload.

Then select System -> Administration -> Synaptic Package Manager

and search for blueman

Thanks for the helpful reply! I've been away for a few days, just got back, found and followed your instructions. Everything went as described until after "Click on Add Source".
After adding the source, there was no prompt or option asking to reload. The Blueman URL appears on the Software Sources page now, but not in the Synaptic Package Manager.
Any ideas?

---

### Post by teward on 2009-12-15
I'm assuming you have bluetooth.  You might need to find a .deb download for it, rather than the add/remove apps menu.  I've encountered versions of programs like that where you need to do a manual install (Limewire, for example).

---

### Post by bmman on 2009-12-15
> **TrekCaptainUSA said:**
> I'm assuming you have bluetooth.  You might need to find a .deb download for it, rather than the add/remove apps menu.  I've encountered versions of programs like that where you need to do a manual install (Limewire, for example).

Yes, I had Bluetooth built in when I bought the mini-9. How do I go about finding a .deb download for it?

---

