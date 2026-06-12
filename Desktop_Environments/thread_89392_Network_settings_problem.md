---
title: "Network settings problem"
date: 2005-11-12
forum: Desktop Environments
---

### Post by mithion on 2005-11-12
I'm having a very annoying problem with profiling network settings with network-admin.  I'm using a laptop, and there I move around a lot, from school, to work, to home.  Of course, these three locations have three different set of network settings.  At home and school, it's a wireless connection.  At work, it's standard ethernet.  My problem is that each time I change location (both physically, and in the network-admin app), my settings magically disappear.  For example, at work, we use static IP addresses, DNS servers, default gateways and subnet mask.  And I have created a location in network-admin called "work" in which I entered all this information.  Then, I head back home, where we use a wireless connection encrypted with a WEP key.  So I also created a location called "home" and entered this key.  Each time I turn off my computer, and switch location, my settings have magically disappeared.  All the fields I had entered are empty and replaced with some defaults.  How do I fix this annoying problem?

---

### Post by teaker1s on 2005-11-12
save your session when you log out after altering settings and although location is blank when you boot you can select home or work for example

---

### Post by mithion on 2005-11-12
I have tried so, and it hasn't worked.  I keep getting the same problem.  I have noticed when booting, there is some sort of configuration tool that runs.  I have the feeling that this steps overwrites the /etc/network/interface file and the other file that deals with profiling.  But I have no idea how to deactivate this manager.

---

### Post by teaker1s on 2005-11-12
sorry I can't be of more help I know that a lot of people has had various network bugs-maybe someone else will suggest a solution

---

### Post by bartc on 2005-11-12
Profiles don't seem to work here too, although it takes quite some time to switch between profiles. The network-admin tool also seem to lack an option to switch between `ad-hoc' and `managed' mode. As a result I find myself manually editing the /etc/networking/interfaces file each time...

---

### Post by mithion on 2005-11-12
I've looked at these files, the interface file and the profile file, and I'm very unsure about manually editing them.  I believe that if I could configure those two files to my liking, and then lock them in place such that there is no override, I think that would work.  But i'm far too ignorant to attempt that.  Anybody know anything about a tutorial to manually edit these two files?

---

### Post by n00blar on 2005-12-06
Oh, good to hear some of you are having these issues. I've been going mad trying to figure out what's happening to my networking profiles.
I do have my session to save when I log off, but that really does not help.

In my case, I have two network profiles, Home and Work. Both are setup to use Wireless with different configurations for each profile, but I end up having to manually configure all wireless settings every time I switch back and forth.

Hopefully will get this bug fixed in the next 'bug fix' release? :)

---

### Post by ahave2005 on 2005-12-06
Have a look at the wiki on wifi, there is a script you might be able to use:
[https://wiki.ubuntu.com/WiFiHowto]("https://wiki.ubuntu.com/WiFiHowto")

/ahave

---

