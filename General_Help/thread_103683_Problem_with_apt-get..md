---
title: "Problem with apt-get."
date: 2005-12-14
forum: General Help
---

### Post by TeraDyne on 2005-12-14
Ok, I had a problem and I managed to fix it. I'd like to point it out, though, incase there is something wrong. Sorry if this is the wrong forum.

Basicly, I installed the xubuntu-desktop and then gnome onto my Kubuntu 5.10 install. When I did, they wanted abiword and abiword-gnome. However, when I got rid of Abiword for Abiword-Gnome, something stranged happened. I couldn't use apt-get as it wanted to install Abiword, but wouldn't remove Abiword-Gnome. To fix it, I tried to remove both, only to realize that abiword-common needed one or the other. 

Well, I tried uninstalling all three, and it wouldn't because the 
xunubtu-desktop dummy package wouldn't uninstall. Here's the first wierd part, because I removed the dummy package when I installed Gnome. I couldn't remove it, though as it didn't exist.

Well, it pointed to a line in the "/var/lib/dpkg/status" file. Instead of waiting to get help, I did what any self-respecting idiot would do and decided to dive in with Kwrite. When I got in, I went down to the line that was beeing called and it happened to be the "abiword" package status. I do not have a record of what it said, but I removed all information reguarding it.

I tried again, and it pointed to another line. This time, the xubuntu-desktop package. I removed everything on it and tried once more. It worked.

I've enclosed everything left in the Konsole window in the attacted txt file. It pretty much tells the story.

Again, sorry if this is the wrong forum.

---

### Post by aysiu on 2005-12-14
Is there a question...?

---

### Post by TeraDyne on 2005-12-14
Gah. Thanks for reminding me. Dummy me forgot to add the question before posting.

I was wondering if anyone knew what would cause it to happen. 

Also, I do remember one of the lines that was in the entry for the Abiword package that seemed strange:

> Status: purge ok installed

Any ideas?

---

### Post by shakin on 2005-12-14
I would have suggested running 'sudo apt-get -f' to let apt-get fix its own problems.

---

### Post by TeraDyne on 2005-12-14
I did. Here's what happened:

> shawn@ubuntu:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  abiword
The following NEW packages will be installed:
  abiword
0 upgraded, 1 newly installed, 0 to remove and 45 not upgraded.
Need to get 0B/2508kB of archives.
After unpacking 7008kB of additional disk space will be used.
Do you want to continue [Y/n]? y

Preconfiguring packages ...
dpkg: parse error, in file `/var/lib/dpkg/status' near line 19335 package `xubuntu-desktop':
 missing version
W: Encountered status field in a non-version description
W: You may want to run apt-get update to correct these problems
E: Sub-process /usr/bin/dpkg returned an error code (2)

---

