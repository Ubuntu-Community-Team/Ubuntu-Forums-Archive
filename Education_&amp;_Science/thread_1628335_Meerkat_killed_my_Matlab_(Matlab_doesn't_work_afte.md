---
title: "Meerkat killed my Matlab? (Matlab doesn't work after the LL&gt;MM upgrade)"
date: 2010-11-22
forum: Education &amp; Science
---

### Post by slcooper on 2010-11-22
[FONT=Microsoft Sans Serif]As the title says: I use Matlab on a regular basis. I installed it on Lucid in May, or June. Few days ago, I upgraded Ubuntu, Maverick works just fine - but I can't start Matlab! 

The folder containing all Matlab files is on my second partition, and the message I get after typing[/FONT] 

[FONT=Courier New]sudo sh matlab

[FONT=Microsoft Sans Serif]is

[FONT=Courier New]matlab: 1218: /media/PartitionTwo/Matlab/bin/glnx86/fvwmfix: Permission denied
exec: 1: /media/PartitionTwo/Matlab/bin/glnx86/MATLAB: Permission denied
[/FONT]
What can I do?
[/FONT][/FONT]

---

### Post by gunksta on 2010-11-22
What are the current permissions of the two files listed in your OP? Using Nautilus/Thunar/Dolphin (depending on which *buntu you are using) browse to the directory and right click on the files and select properties. You definitely need read access and I suspect you will need permission to execute them.

I don't know anything about Matlab, but knowing what permissions you have to those files is certainly the first step. Using the same dialog box, you will be able to edit the permissions of the files.

As a side note, you may actually want to edit the permissions of the folders(s) holding the matlab files, or you may get to do this repeatedly to a large number of individual files.

---

### Post by slcooper on 2010-11-23
Hmm, quite weird. It says: 

[B]Owner: sheldon - Sheldon Cooper
Access: Read and write

Group: sheldon
Access: none

Others
Access: none[/B]

and I don't seem to be able to change anything - starting nautilus both as sheldon and as root gives the same situation: the senct I change something, it changes back immediately.

*(sheldon selected as a random name)*

Same permissions are for the entire MATLAB folder.

---

### Post by gunksta on 2010-11-23
Well, you have Read/Write Access to the folder, which is should be more than you need. Do you have permission to execute the files that are causing the error?

---

### Post by slcooper on 2010-11-23
Allow executing file as program checkbox is empty and I can't fill it (not even as a root via gksu nautilus).

EDIT: If I copy the files on desktop for instance, I can change the status of checkbox, and it stays checked. Still, when I copy it back - it goes off again.

---

### Post by gunksta on 2010-11-23
Your inability to change the permissions on the file is probably the underlying problem. Everything we have seen thus far is really just symptomatic. How are you mounting /media/PartitionTwo? That's an odd place for a separate partition.

---

### Post by slcooper on 2010-11-24
It's actually a Windows partition - when I installed Karmic, I already had XP installed, with two partitions, C: and D: (D: being called PartitionTwo). Through the Karmic setup, I made a swap partition and a partition for Ubuntu from a part of PartitionTwo, and left both C: and D: available for Windows. So, the "42 GB filesystem" (i.e. C) and "PartitionTwo" (i.e. D) appear in my "Places" menu.

---

### Post by gunksta on 2010-11-24
Oh my. That is quite a setup you have there. I haven't shared a drive like that between Windows and Linux in many years and things have changed a lot in the meantime.  I'm actually rather impressed that it ever worked. (I assume the shared drive is either NTFS.)

I still think the problem probably lies in the permissions, but now we're also into mounting and what not. This might be a question that would be better served on one of the more generic forums. Be sure to mention these details about how things are mounted and I would also provide the contents of /etc/fstab.

---

### Post by slcooper on 2010-11-24
I have strated a new thread [here]("http://ubuntuforums.org/showthread.php?p=10157469#post10157469"). We'll see if anyone has a solution for it.

EDIT: Matter resolved :)

---

### Post by Blutkoete on 2010-11-26
Grats it works now!

Would you mind marking both threads as solved? It's in the thread tools on top of the thread. That way people browsing through the forums or searching for solutions see that a problem was solved.

Thank you!

---

