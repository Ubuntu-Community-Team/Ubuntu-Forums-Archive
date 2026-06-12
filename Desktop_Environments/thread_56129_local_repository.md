---
title: "local repository"
date: 2005-08-11
forum: Desktop Environments
---

### Post by Hairy_Palms on 2005-08-11
ive been trying to make a local repository on my hd, i created a folder and put all the packages in it and when i tried dpkg-scanpackages it gave me an error output of this

root@ubuntu:~ # dpkg-scanpackages repo /dev/null >Packages  ** Packages in archive but missing from override file: **
  bittorrent-4.0.3.linux bootchart bootchart-view bum cedega
  kooldock opera-static splashy sun-j2re1.5

 Wrote 147 entries to output Packages file.

anyway there was a long list of 147 packages but ive removed most for post length, then i tried adding it to synaptic anyway and it caused synaptic to crash
if i go to sources.list and comment it out synaptic works fine again.

any ideas appreciated,

---

### Post by AndyAWS on 2005-08-11
What you have posted looks like the expected output...perhaps your packages.gz isn't ending up in the right place, or there is something wrong with your sources.list entry.

Check out this thread for more info:

[http://www.ubuntuforums.org/showthread.php?t=42862](http://www.ubuntuforums.org/showthread.php?t=42862)

---

### Post by Hairy_Palms on 2005-08-11
i checked that out and followed the instructions and had the same problem, but there was a new part to the errror message after 
"Wrote 147 entries to output Packages file"
it says 
"Prototype mismatch: sub main::getopt: none vs (@) at /usr/bin/dpkg-scansources line 116."

and it says in synaptic "file:///root/repo/repo/Packages.gz: File not found" but i can see the file right there in the dir

---

### Post by Hairy_Palms on 2005-08-11
nvm it works now, hehe shouldnt be in repo/repo :D my bad :)

---

### Post by AndyAWS on 2005-08-11
The "prototype mismatch" error comes up for me every time, but everything seems to work fine so I just ignore it.

I believe it is because there are no sources to scan, since the error is in dpkg-scan**sources**. When I get home I'll try removing that line from the autorepo script.


Yes, commenting out the scansources line eliminates the error, so unless you have source packages to scan you should be able to do the same.

---

