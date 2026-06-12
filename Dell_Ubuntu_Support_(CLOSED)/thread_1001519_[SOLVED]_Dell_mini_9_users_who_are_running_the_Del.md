---
title: "[SOLVED] Dell mini 9 users who are running the Dell's Ubuntu 8.04"
date: 2008-12-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by shiningkenmonster on 2008-12-04
What version of Firefox Web Browser do you have?

I still have version 3.0.3

I notice that firefox 3.0.4 is out

I was just wondering if i messed up a configuration in my computer or is it a Dell's problem of lacking updates to the repository in the update manager/source software. 

because for some odd reason i still have firefox 3.0.3

---

### Post by andreasis on 2008-12-04
Hi,

Please see System>Administration>Software Sources and ensure you've checked off the boxes.  When is the last time that you've checked for updates using update-manage?  When's the last time you've checked for updates using the update manage?

---

### Post by shiningkenmonster on 2008-12-04
yeah, i did that yesterday and today. unchecked everything but the third party software. updated. did not get the firefox 3.0.4

i even unchecked the third-party software, and checked everything on the "Ubuntu Software" and "Updates" tab. I had some problem broken link that says error can not download some links due to not being found. (this is a common thing with the Dell mini 9 users who are using the Dell's version of Ubuntu 8.04)

since it does download files like this, i think it does an incomplete update. i am not sure

thats why I have the third party software on, which is on by default on a factory restore from dell. (when i do this,  i don't have the broken update links saying its not found.)

---

### Post by andreasis on 2008-12-04
What concerns me is not that you are not receiving the latest firefox update, but that it could mean that you are not receiving any of the latest updates.

In the same place in software sources, under the updates tab, make sure you have check marks in the first two boxes.  Firefox 3.0.4 should be part of hardy-updates, so chances may be that you're not getting firefox 3.0.4 because you're not telling the program to check for hardy-updates.

now that there are check marks in the first four boxes under "Ubuntu Software" tab, did you try downloading from the Main server, or, for example, from lug.mtu.edu in the US?  If yes, then go into Synaptic Package Manager, search for firefox, right-click, properties, versions, and what do you see there?

Also, under Synaptic>Settings>Preferences>Distribution, do you have "Always prefer highest version" checked?

---

### Post by shiningkenmonster on 2008-12-04
yeah, i did that before. 

even for your instruction, I followed them and i decided to give you the error message which i've received.

> Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/main/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/main/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Some index files failed to download, they have been ignored, or old ones used instead.

(this is a common thing for the dell mini 9 users)

that is why i only have the third-party software tab checked only. so i won,t get these messages.

under Synaptic>Settings>Preferences>Distribution, the "Always prefer highest version" is checked. it was checked by default, i didn,t changed it.

and as for Synaptics, for a search for firefox and right click and properties it says:

> Version 3.0.3+build+1+nobinonly-0ubuntu0.8.04.1netbook2build1

still no update for firefox.

---

### Post by andreasis on 2008-12-04
Okay, we're making good progress here.

I've taken a look at the dell-mini repositories [http://dell-mini.archive.canonical.com/ubuntu/dists/](http://dell-mini.archive.canonical.com/ubuntu/dists/) and I was appalled to see that the last time they were updated was 23-Oct-2008. It therefore makes perfect sense that firefox 3.0.4 wouldn't be available to a dell mini. However, the problem at hand is that the sources are broken:

Do note that the hp mini repositories are up do date. We can try and switch over to the hp repositories, or at the very least, fix the repositories that you have right now so you don't have to put up with those 404 errors. NOTE: if you are not comfortable switching to the hp repositories , I'll want to request the following from you regardless:
Could you post your /etc/apt/sources.list

Basically, we need to replace what's wrong with what's right in that file, so that Ubuntu finally starts looking in the right place for its updates.

[EDIT]

Never even mind. You don't even need to post the file, unless there's further questions, in which case it would definitely be useful. Make a backup of the file just in case.

when you ```
sudo gedit /etc/apt/sources.list
``` , comment out (put a # to the left of) the lines that contain the broken repositories.  Then, right underneath each broken repository that you've commented out, paste the new, corrected link.

I will give you one example:

# [http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-lpia/Packages.gz)
[http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/restricted/binary-lpia/Packages.gz](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/restricted/binary-lpia/Packages.gz)

(this is the dell-mini repository that is not up to date)

if you want to use the hpmini repository which is up to date and has the latest firefox as well, then instead of 

[http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/restricted/binary-lpia/Packages.gz](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/restricted/binary-lpia/Packages.gz)

you would put

[http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-hpmini/restricted/binary-lpia/Packages.gz](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-hpmini/restricted/binary-lpia/Packages.gz)


[EDIT]

Okay, I see that ubuntu forums automatically shortens the urls which is exactly what we don't want, so I will give you the above three urls in the same order, but without http://

archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-lpia/Packages.gz (broken)

dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/restricted/binary-lpia/Packages.gz (dell-mini)

dell-mini.archive.canonical.com/ubuntu/dists/hardy-hpmini/restricted/binary-lpia/Packages.gz (hpmini)

I will check up on this thread in 8 hours again and see if this helped.

---

### Post by yakker.yak on 2008-12-04
I also have the default Dell Ubuntu install running and haven't received any updates.

It actually looks as though Dell and Canonical have fallen asleep at the wheel on this one. Check out launchpad for the latest status, and see for example this [bug report]("https://bugs.launchpad.net/dell-mini/+bug/302755").

BTW, not sure if it's a good idea to mix repositories and use the hp mini ones for your Dell since there may be hp mini specific settings/tweaks for hardware that may not be applicable/good for your Dell mini.

---

### Post by andreasis on 2008-12-04
> BTW, not sure if it's a good idea to mix repositories and use the hp mini ones for your Dell since there may be hp mini specific settings/tweaks for hardware that may not be applicable/good for your Dell mini.

I have thought about the implications of using the hpmini repositories, but then again, looking at the addresses, both the dell and the hpmini repo's start with dell-mini.archive.canonical.com/ubuntu/dists/

I looked at the package that shiningkenmonster mentioned, per se:

Old Dell package:

firefox-3.0-gnome-support_3.0.3+build1+nobinonly-0ubuntu0.8.04.1netbook2build1_lpia.deb

from 
dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/

as opposed to new hp mini package:
firefox-3.0-gnome-support_3.0.4+nobinonly+nb2-0ubuntu0.8.04.1netbook1_lpia.deb

from

dell-mini.archive.canonical.com/ubuntu/dists/hardy-hpmini/main/binary-lpia/

Too bad that I don't have the dell mini to test this out on.


What could be done as a (temporary) fix (until dell+ubuntu may decide to roll out updates once again) is at the very least fix the broken links in sources.list

yakker, do you get the 404 errors too, or are you just not getting the updates?

Switching to the new dell-mini repositories, as mentioned above, is confirmed:

[http://ubuntuforums.org/archive/index.php/t-983005.html](http://ubuntuforums.org/archive/index.php/t-983005.html)

---

### Post by yakker.yak on 2008-12-05
> **andreasis said:**
> 
yakker, do you get the 404 errors too, or are you just not getting the updates?

Switching to the new dell-mini repositories, as mentioned above, is confirmed:

[http://ubuntuforums.org/archive/index.php/t-983005.html](http://ubuntuforums.org/archive/index.php/t-983005.html)

Just haven't had a single update using the default repos, no 404 issues. Can install applications from the repos fine though.

---

### Post by jheaton5 on 2008-12-05
The Dell repositories are not updated as often as the ubuntu repositories.  I have been told that installing the standard ubuntu 8.04 or 8.10 will allow you to use the ubuntu repositories.

---

### Post by shiningkenmonster on 2008-12-06
hey andreasis,

thanks for your help.

but i just did a usb flash system restore not that long ago.

i don,t want to tamper with it.

i just need to focus more on school for now.

if you get a dell mini 9. why dont you try it :)

---

