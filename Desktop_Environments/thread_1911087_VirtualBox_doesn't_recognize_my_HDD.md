---
title: "VirtualBox doesn't recognize my HDD"
date: 2012-01-18
forum: Desktop Environments
---

### Post by tallnginger on 2012-01-18
So I finished my install of 10.04 LTS x64 and needed to put on a VirtualBox of Windows 7 for some programs for school. 

Everything was going great until I got tired of mounting my 2nd internal HDD (the one I installed the Win7 Vbox on) every single time I logged on.

I searched around for some ways to fix it: Editing the pysdm and even the nautilus area in gconf-editor to get the icon off the desktop.

The problem is that when I go into VirtualBox it can't find my 2nd internal HDD regardless of whether it is mounted or not. I can't find it to create a brand new Environment nor can I access my current one.

Side note that may be related, even though my HDD appears mounted in the File Manager and even the Disk Manager when I click the Places dropdown menu it doesn't show up like it's mounted (no eject button)


Is there a way to just set all the mounting options back to the way they had been?

---

### Post by BC59 on 2012-01-18
You could install the Storage Device Manager from the Ubuntu Software Center and manipulate the settings for each HDD.

And a suggestion. Win7 in a virtual machine is too slow. Better use Win XP.

---

### Post by tallnginger on 2012-01-18
> **BC59 said:**
> You could install the Storage Device Manager from the Ubuntu Software Center and manipulate the settings for each HDD.

And a suggestion. Win7 in a virtual machine is too slow. Better use Win XP.

I have that and edited it to try to get my HDD to auto-mount. That's what I think messed it up in the first place.

---

### Post by BC59 on 2012-01-18
Another solution is to open fstab and comment with hash (#) in front of the devices you have problem, to make the line inactive.

```
gksu gedit /etc/fstab
```

Mounting again the device a new correct entry will be created.
If you have problem, just un-comment the line again.

---

### Post by BC59 on 2012-01-18
Some details about how you could solve the problem are [here]("https://help.ubuntu.com/community/AutomaticallyMountPartitions").

---

### Post by tallnginger on 2012-01-18
> **BC59 said:**
> Some details about how you could solve the problem are [here]("https://help.ubuntu.com/community/AutomaticallyMountPartitions").

I've been there and I know how to edit all that. What I don't know is what the default is for everything. Because when I simply hit the default button VirtualBox is still unable to see that I have a second internal hard drive. 

I want to get it back to as if I had just formatted it as an NTFS drive, and set up VirtualBox to send all the data for my Virtual Environment over to that drive

---

### Post by tallnginger on 2012-01-18
Update: Checked my user setting and under Advanced Settings, the box the said "Allowed to use VirtualBox Software" was unchecked


I checked it, but it still didn't work

---

### Post by tallnginger on 2012-01-20
I made a new user and it was able to see my internal hard drive, though it was unable to start my virtual drive. Therefore, I'm fairly certain this is a problem within my user settings.


Any help?

---

