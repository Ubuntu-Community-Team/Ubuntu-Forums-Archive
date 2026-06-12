---
title: "Dapper &amp; mjpegtools dependency problem"
date: 2006-07-22
forum: Desktop Environments
---

### Post by gilgongo on 2006-07-22
Hi, I'm using Dapper and trying to make a DVD of an AVI file using Kmediafactory. 

Kmediafactory calls the following line:

ppmtoy4m -S 420_mpeg2 -n 1 -r -I p -F 25:1 -A 59:54 Main_1.pnm | mpeg2enc -a 2 -f 8 -n p -F 3 -o Main_1.m2v && 

and then fails after it gets:

ppmtoy4m - command not found
mpeg2enc - command not found

Sure enough, those commands are nowhere to be seen. If I try to apt-get mjepegtools, I get:

> Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  mjpegtools: Depends: aalib1 (>= 1.2)
              Depends: slang1 (> 1.4.9dbs-4) but it is not installable
E: Broken packages

Anyone know why?

---

### Post by Ziox on 2006-07-22
try sudo aptitude update, then sudo aptitude dist-upgrade, and then try sudo aptitude install mjepegtools

---

### Post by gilgongo on 2006-07-22
Hmm. If I do that, it looks like aptitude can't find the package at all:

> sudo aptitude install mjepegtools
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "mjepegtools"

---

### Post by Ziox on 2006-07-22
my fault...sudo aptitude install mjpegtools
had a extra e in there lol

---

### Post by ColinG on 2006-07-22
mjpeg trools shows up in my Ubuntu Dapper under synaptic. I have Kmediafactory installed and have burned a dvd ok (runs on my home dvd player).

Not sure which repsoitory MJPEGTOOLS is in - do you have multiverse and universe enabled?

---

### Post by Ziox on 2006-07-22
again...he copied and pasted my command, however i had spelled mjpegtools wrong, so....

---

### Post by ColinG on 2006-07-22
Our original posts must have crossed on the post so to speak :) 

Pleased you've got it sorted 

Have fun

---

### Post by gilgongo on 2006-07-22
Still no joy with this. Something is obvioulsy wrong. When I try installing mjpegtools

> The following packages are BROKEN:
  mjpegtools
The following NEW packages will be automatically installed:
  libmjpegtools0
The following packages have been kept back:
  vim
The following NEW packages will be installed:
  libmjpegtools0
0 packages upgraded, 2 newly installed, 0 to remove and 1 not upgraded.
Need to get 508kB/722kB of archives. After unpacking 1892kB will be used.
The following packages have unmet dependencies:
  mjpegtools: Depends: aalib1 (>= 1.2) which is a virtual package.
              Depends: slang1 (> 1.4.9dbs-4) which is a virtual package.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
mjpegtools [Not Installed]

Score is -1

Accept this solution? [Y/n/q/?]  y
The following packages have been kept back:
  vim
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done


Yet still no mpeg2enc or ppmtoy4m appears. Should I try uninstalling mjpegtools and trying again? Why's it broken?

---

### Post by Ziox on 2006-07-22
ok...maybe we should take a different approach, go to synaptic, and on the left section select status and choose broken and see if it can fix the broken software.

---

### Post by gilgongo on 2006-07-22
Ah - I'm on Kubuntu - I get "bash: synaptic: command not found"

---

### Post by Ziox on 2006-07-22
o...then use adept, make sure the command is kdesu adept

---

### Post by gilgongo on 2006-07-23
OK tried that. No dice - it just says there's an error, which I assume is about the "broken" mjpegtools package. I can't see why it's broken though. There seems to be a conflict with a package called dvd-mpegtools - but that shows as not being installed... this is all a bit confusing.

Is anyone able to use Kmediafactory with Dapper at all?

---

