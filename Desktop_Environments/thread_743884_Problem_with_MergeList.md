---
title: "Problem with MergeList"
date: 2008-04-03
forum: Desktop Environments
---

### Post by Robbyx on 2008-04-03
I started the machine up this morning and noticed a need to update via the synaptic udater. Hovering over it it states:

> This usually means your instaled packages have unmet dependancies

This is the full error message when I run sudo apt-get update


> Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_gutsy_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.


In order to fix it I tried:

sudo apt-get update 
sudo apt-get upgrade
           (same error message each time.)

I then tried:
> robin@robin:~$ sudo dpkg --configure -a
robin@robin:~$ sudo apt-get install -f
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_gutsy_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.


I do not know what to do next. Could I please have some help.

---

### Post by Robbyx on 2008-04-03
Please could I have some help because currently I can not install any updates through the file update manager.

Robin

---

### Post by iamforgiven on 2008-04-11
I had this problem. I tried all of the commands and none worked.

Finally, loaded my sources list file (/etc/apt/source.list) into a text editor (Kate) using my file manager as superuser to get there and then clicked on the sources.list to open it in Kate and deleted some of the lines that seems to produce the conflict. You can probably just add # before the lines one at a time until you resolve it. After saving it, Synaptic loaded fine. You can always add the sources again once it reloads.

I hope this works for you. I did it for me.

---

### Post by p_squared on 2008-04-11
> **iamforgiven said:**
> I had this problem. I tried all of the commands and none worked.

Finally, loaded my sources list file (/etc/apt/source.list) into a text editor (Kate) using my file manager as superuser to get there and then clicked on the sources.list to open it in Kate and deleted some of the lines that seems to produce the conflict. You can probably just add # before the lines one at a time until you resolve it. After saving it, Synaptic loaded fine. You can always add the sources again once it reloads.

I hope this works for you. I did it for me.

Which line was it that was causing your problem?

---

### Post by eznet on 2008-04-12
I had to remove the AWN from the sources. Commented it out of /etc/apt/sources.list, but the realized that I could just do it from System->Aministraction->Software Sources->Third-Party Software->un-select 'http://ppa.launchpad.net/awn-testing/ubuntu hardy main' . Now Synatpic is working again.

I wonder what is causing this. I tried deleting the corresponding files in /var/lib/apt/list, but every time I would run 'apt-get update' it would throw the same error. I even copied the contents of the same file at 'http://ppa.launchpad.net/awn-testing/ubuntu/dists/gutsy/main/binary-amd64/' to the local file to no avail. So far seems like disabling is the only way.

---

### Post by iamforgiven on 2008-04-12
> **p_squared said:**
> Which line was it that was causing your problem?I had to delete the last two in my list which were for awn (the same as the previous post). Once I deleted these lines then Synaptic worked. Then I updated and did any upgrades. Then I added the awn repositories again and everything is working as if nothing happened.

---

