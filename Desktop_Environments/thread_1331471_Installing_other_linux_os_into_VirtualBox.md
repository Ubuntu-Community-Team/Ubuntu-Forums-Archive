---
title: "Installing other linux os into VirtualBox?"
date: 2009-11-19
forum: Desktop Environments
---

### Post by duncan503 on 2009-11-19
Hello has any one has any idea how to install another Linux OS into **Virtual Box ? **When it come to selecting a place to mount it (hard drive) that where I get confuse! hope to hear from y'all.

---

### Post by TCSnyder on 2009-11-19
well, if you have virtualbox installed, you can use the wizard to create a new linux distro. you will point virtualbox at a cd .iso image of the live/install cd and install as normal

---

### Post by Invincible23 on 2009-11-19
> **duncan503 said:**
> Hello has any one has any idea how to install another Linux OS into **Virtual Box ? **When it come to selecting a place to mount it (hard drive) that where I get confuse! hope to hear from y'all.

Start VirtualBox

Click on New, which starts Virtual Machine Wizard

Click Next

Enter a name, select the OS type from dropdown list, then select version

Select how much base memory you want to allocate

Now select Create new hard disk, click Next which starts New Virtual Disk Wizard, click Next

Here you have 2 options
Dynamically expanding storage OR Fixed sized storage, 
Go for the first option if you plan to install softwares which would need more storage else select Fixed storage
Click Next

Now select size of guest OS, click Next and then Finish.

[B]Now click on settings, select CD/DVD-ROM and Mount CD/DVD Drive. 
If you have a ISO image on the hard disk select ISO Image file and point its path.
If you have burnt an CD then select insert the CD and select Host CD/DVD Drive and click OK.[/B]

Click Start which begins the install process.

---

### Post by duncan503 on 2009-11-19
Thank you for your response but there is a glitch. Some how when I arrive where to choose where to mount the Linux OS it does not and will not let me install it. ? Now what!

Thank you there in Internet land virtualbox did not take sabayon 4.2 don't know why: but we don't know We just don't know!

---

