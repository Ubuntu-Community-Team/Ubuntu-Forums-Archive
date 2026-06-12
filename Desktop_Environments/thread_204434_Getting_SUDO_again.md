---
title: "Getting SUDO again"
date: 2006-06-27
forum: Desktop Environments
---

### Post by Cazilla on 2006-06-27
Hi there. Hopefully this is a fairly easy issue to resolve.
When I installed Dapper I ran the expert setup and set up the user and root accounts. At that time I didn't think ( note the not thinking part 8)) that getting admin priviledges for running say Synaptic in the UI would require the user to have SUDO and that I could simply type in the Root PW and Id be on my way. Currently to do any changes in the gui I have to relog in failsafe log as root and start X, What a pain! HAHAHAHA

ANYWAYS, My question is HOW, minus reinstalling this fine OS, can I get my user to be able to use SUDO again or get permission in the user gui to access restricted services?](*,) 

If there is another post that covers this I coulnd find it off hand.

Thank you VERY much for viewing this and possibly pointing me in the right direction.

---

### Post by mlind on 2006-06-27
This post should solve it for you [http://www.ubuntuforums.org/showpost.php?p=1180504&postcount=9](http://www.ubuntuforums.org/showpost.php?p=1180504&postcount=9)
If your /etc/sudoers look the same, you just need to add yourself to described groups.

To accomplish this, you need to boot on recovery mode. It's the alternative kernel on GRUB boot menu.

Recovery mode boots you on runlevel 1, where you're logged as root user.
Then you just add your self to necessary groups and execute

```

init 2

```

---

### Post by Cazilla on 2006-06-27
Can I do this from the user terminal and use SU? then reboot?

---

### Post by mlind on 2006-06-27
[QUOTE=Cazilla]Can I do this from the user terminal and use SU? then reboot?[/QUOTE]

I didn't quite understand.. sorry.

You can't **su** untill your user is on *admin* group, which grants you **sudo**ing
privilege. You can see your groups by typing just *groups* on terminal.

You can try **sudo su**, but since root has no password on Ubuntu by default - plaing su
won't (and shouldn't) work.

To gain root privileges, you must get to runlevel 1 and add yourself to *admin* group.
And to accomplish all this, you must boot and select recovery mode.


I hope this helps you to understand this issue.

/edit
after you've got yourself on admin group, admin stuff can be performed using sudo.

---

### Post by aysiu on 2006-06-27
I'm not sure if this'll work from an expert install, but you may want to check this out:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

### Post by Cazilla on 2006-06-28
Thank you both for the  help It pointed me in the right direction and yes IF you can SU to root but not SUDO, you can enter a terminal in the gui and SU to root and make those changes. BTW my issue turned out that I didnt have an admin group which was easily solved by adding the admin group then adding my user to that group after adding the %admin line form the first link :D

---

