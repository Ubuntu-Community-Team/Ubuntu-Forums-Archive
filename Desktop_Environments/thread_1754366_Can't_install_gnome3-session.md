---
title: "Can't install gnome3-session"
date: 2011-05-10
forum: Desktop Environments
---

### Post by gwoodruff on 2011-05-10
Hello having problems with the gnome3 shell. when I try to install gnome3-session it says I have miising depends and broken packages. I have no broken packages and cant seem to get past the depends.

gary@gary-desktop:~$ sudo apt-get install gnome3-session
[sudo] password for gary: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gnome3-session : Depends: gnome-session-bin (< 2.33) but 3.0.1-0ubuntu1~build2 is to be installed
                  Depends: gnome-session-common (= 2.32.1-0ubuntu20) but 3.0.1-0ubuntu1~build2 is to be installed
E: Broken packages
gary@gary-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
gary@gary-desktop:~$

---

### Post by glx135 on 2011-05-10
i've got this issue too, only on dist-upgrade
tried it on my desktop pc and on a clean install in a virtualbox host

---

### Post by satanselbow on 2011-05-10
You need gnome-session (from the gnometeam ppa) - not gnome3-session to run G3.

You are looking to get a gnome3-shell session going right?

---

### Post by lisati on 2011-05-10
<aside>
No need to use [noparse]** and **[/noparse] in a thread title.
</aside>

---

### Post by gwoodruff on 2011-05-10
I have gnome3 shell up and running but it is buggy (see my post: [http://ubuntuforums.org/showthread.php?p=10793683#post10793683](http://ubuntuforums.org/showthread.php?p=10793683#post10793683)). I have seen posts directing people to install gnome3-session (I do have gnome-session). 

Gary

---

