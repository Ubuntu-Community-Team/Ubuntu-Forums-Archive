---
title: "How can I remove gdm?"
date: 2011-02-04
forum: Desktop Environments
---

### Post by shenghaiknight on 2011-02-04
Hi, I'm dual booting ubuntu 10.10 with Windows 7 and I recently installed the kubuntu desktop and greatly prefer it over GNOME. So, my question is, is there any way I can remove the ubuntu desktop? Also, a completely unrelated question, when I start my computer, it goes to a screen where I choose which OS to boot up. The thing is, I originally installed 9.10, and upgraded it to 10.04 then 10.10. So, that screen has all three on there in the format:

Ubuntu-linux ###### generic (10.10)
Ubuntu-linux ###### generic
Ubuntu-linux ###### generic (10.04)
Ubuntu-linux ###### generic
Ubuntu-linux ###### generic (9.10)
Ubuntu-linux ###### generic
Windows 7

is there anyway I can get rid of the other 2? Thanks, I'm pretty new to this.

---

### Post by Cypher2 on 2011-02-04
you will need to purge the corresponding packages in apt via apt-get autoremove and force an update on grubs boot list for it to comply.

on the other hand, it seems you have multiple separate versions of ubuntu running or partitionned into the drive.. you best bet would be to just format and clean install that section of it to a kubuntu 10.10 :)

---

### Post by inobe on 2011-02-04
here's the thing with that, there are many gnome apps that get left behind when removing stuff manually!

i recommend this approach [http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

at least that way it will reinstall missing kde components and the end result will be pure kde.

that is for 10.10, be sure to copy and paste "the entire command"

---

### Post by inobe on 2011-02-04
> **shenghaiknight said:**
> a completely unrelated question, when I start my computer, it goes to a screen where I choose which OS to boot up. The thing is, I originally installed 9.10, and upgraded it to 10.04 then 10.10. So, that screen has all three on there in the format:

Ubuntu-linux ###### generic (10.10)
Ubuntu-linux ###### generic
Ubuntu-linux ###### generic (10.04)
Ubuntu-linux ###### generic
Ubuntu-linux ###### generic (9.10)
Ubuntu-linux ###### generic
Windows 7

is there anyway I can get rid of the other 2? Thanks, I'm pretty new to this.


a different matter, these are old kernels, it's nice to have them encase one should fail!

however you can completely clean house?

if yes view this ubuntu forum thread, i wouldn't run this until you removed ubuntu desktop and rebooted "first"

read the thread before running the command

[http://ubuntuforums.org/showthread.php?t=1658648](http://ubuntuforums.org/showthread.php?t=1658648)

---

### Post by shenghaiknight on 2011-02-04
> **inobe said:**
> here's the thing with that, there are many gnome apps that get left behind when removing stuff manually!

i recommend this approach [http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

at least that way it will reinstall missing kde components and the end result will be pure kde.

that is for 10.10, be sure to copy and paste "the entire command"

I tried the link and copied the entire command, but ended up getting this error message:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package scrollkeeper is not installed, so not removed
Package linux-headers-2.6.35-22 is not installed, so not removed
Package linux-headers-2.6.35-22-generic is not installed, so not removed
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 librsvg2-2 : Depends: libcroco3 (>= 0.6.2) but it is not going to be installed
 libschroedinger-1.0-0 : Depends: liborc-0.4-0 (>= 0.4.6) but it is not going to be installed
E: Broken packages

And then it goes back to the prompt. Any ideas as to what this means?

---

