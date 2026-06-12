---
title: "Identify installed apps?"
date: 2006-01-09
forum: Desktop Environments
---

### Post by djjazzyjeff on 2006-01-09
Hi, I have a question for the group. I have installed a large number of apps via Synaptic from the Networking (universe) catagory that I want to work with and learn from. After stepping through the install, I thought it would be useful to have a list of them to reference but I have no idea how to create/locate such a list. Can anyone point me in the right direction?

---

### Post by welsh_spud on 2006-01-09
You can get a Debian Installed Apps menu that shows you (almost) all the apps installed on your computer.

You can install the Debian Menu with [Automatix]("http://www.ubuntuforums.org/showthread.php?t=80295")

---

### Post by Olav on 2006-01-09
[QUOTE=djjazzyjeff]Hi, I have a question for the group. I have installed a large number of apps via Synaptic from the Networking (universe) catagory that I want to work with and learn from. After stepping through theinstall, I thought it would be useful to have a list of them to reference but I have no idea how to create/locate such a list. Can anyone point me in the right direction?[/QUOTE]
Not sure if this is what you mean, but with this ```
dpkg -l
``` you get a list of all installed packages.

---

### Post by leech on 2006-01-09
Even easier...  

Open up Synaptic, click on the Status button in the lower left hand corner (usually it's there by default) and then select the Installed or Installed (local or obsolete).

The difference between the two, are that Installed will show you all the software you have installed from the repositories.  The local or obsolete one will show everything that is installed, even packages like Cedega that were not installed from the repositories.

Leech

---

### Post by djjazzyjeff on 2006-01-09
That's what I am looking for, thanks Olav!

-Jeff

---

### Post by djjazzyjeff on 2006-01-09
I appreciate the help, one more dumb question tho. Can I display installed apps using either method based on the "Sections" catagory in Synaptic, so like just "Networking" instead of all installed apps? Thanks in advance.........Jeff

---

### Post by Olav on 2006-01-09
[QUOTE=djjazzyjeff]I appreciate the help, one more dumb question tho. Can I display installed apps using either method based on the "Sections" catagory in Synaptic, so like just "Networking" instead of all installed apps? Thanks in advance.........Jeff[/QUOTE]
You could make a filter in Synaptic.

---

### Post by djjazzyjeff on 2006-01-09
I'm not sure how to do filtering in Synaptic, my ultimate goal is to have a printed list to reference, thanks.......Jeff

---

### Post by Olav on 2006-01-09
[QUOTE=djjazzyjeff]I'm not sure how to do filtering in Synaptic[/quote]
Easy: -> Settings -> Filters -> New Filter
Then on the Status tab you make sure only "installed" is checked, and on the Sections tab you select your desired sections and check "include selected sections only".

> , my ultimate goal is to have a printed list to reference, thanks.......Jeff
Sorry, can't be done from Synaptic I believe... And I don't know how to make the filter on the command line with dpkg or apt-*.

---

### Post by djjazzyjeff on 2006-01-09
Thanks anyway Olav, I have the list in a text file, sometimes the quickest means to an end is plain old elbow grease. I'm just going to edit out the non-networking apps and what remains will be what I'm looking for. Learned something today tho, thanks to all for the input..........Jeff

---

