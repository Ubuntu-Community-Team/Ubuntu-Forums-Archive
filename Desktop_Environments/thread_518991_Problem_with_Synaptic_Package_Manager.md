---
title: "Problem with Synaptic Package Manager"
date: 2007-08-06
forum: Desktop Environments
---

### Post by MacDuff on 2007-08-06
This question was asked a week ago but the only answer I received did not work.  The question and answer are shown below to save having to go over old ground:

Question: I have a problem with the Synaptic package manager of Ubuntu 7.04. A package won't install and I can not clear it from the manager. Is there a way to repair Ubuntu from the install DVD or can I delete some file(s) so that I can get the the Synaptic pkg manager working again?

Answer: Paste this command into the terminal:
sudo apt-get -f install  and then paste the output back here.

Result: 
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: The package mailwasher needs to be reinstalled, but I can't find an archive for it.

Next response:  Can you try pasting this command in:
sudo dpkg --remove --force-remove-reinstreq mailwasher

Result of above command:
macduff@macduff-laptop:~$ Reading package lists... Done
bash: Reading: command not found
macduff@macduff-laptop:~$ Building dependency tree
bash: Building: command not found
macduff@macduff-laptop:~$ Reading state information... Done
bash: Reading: command not found
macduff@macduff-laptop:~$ E: The package mailwasher needs to be reinstalled, but I can't find an archive for it.

So I still cannot re-install the package and I cannot use the package installer to install other software.  I tried to start Ubuntu in safe mode but do not know enough about what to look for to fix the problem.  (I am really new to Linux/Ubuntu.)

My questions are:
1. Is there a way to purge the package installer so that it discards the failed installation or must I re-install Ubuntu?  Bear in mind that I need detailed instructions as I know very little about Linux/Ubuntu.
2. If I re-install ubuntu does it re-install over top of the original installation or does it create new partitions?

Thanks for any assistance anyone can provide.

---

### Post by kelvin spratt on 2007-08-06
Go to Synaptic bottom left hand corner select custom filters you will see entry for broken packages, click on it then remove any broken packege showing in main panel

---

### Post by OzzyFrank on 2007-08-11
Unfortunately, not all culprits end up in Broken Packages. My pain-in-the-A was Adobe reader, and it never installed properly, yet did not end up in that section. I searched Synaptic for it, and when found (marked as installed) I simply marked it for COMPLETE REMOVAL and it hasn't bother me and Synaptic/Update Manager/apt-get anymore! Hope this is the answer you need!

---

### Post by Blindraven on 2007-08-11
sudo dpkg -l |grep symantec
then

sudo dpkg -r symantec (ow whatever it is called.

---

