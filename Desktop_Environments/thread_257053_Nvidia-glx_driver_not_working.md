---
title: "Nvidia-glx driver not working"
date: 2006-09-14
forum: Desktop Environments
---

### Post by flathampster on 2006-09-14
Hi all

When I rebooted, my PC recently the X server would not load. The error messages were exactly the same as when a patch killed the Xserver about 3 weeks ago.

When I tried to "apt-get install nvidia-glx" it I recieved the following messages
------------
The following packages have unmet dependencies:
nvidia-glx: Depends: libglu1-mesa but it is not going to be installed or libglu1
---------------

When I tried to "apt-get upgrade libglu1" it said

Note selecting libglu1-mesa instead of libglu1
libglu1-Mesa is already the newest version.
0 upgraded, 0 newly installed etc

The last thing I can remember doing was installing sypheed-claws by adding a line to my sources.list

---

### Post by angkor on 2006-09-14
What line did you add to your list?

You could try commenting out that line and try again after an 'apt-get update'.

---

### Post by flathampster on 2006-09-14
The line I added was this
deb [http://www.sylpheed-claws.net/ubuntu/dapper/](http://www.sylpheed-claws.net/ubuntu/dapper/) ./
I have already installed the program. After the problem started I removed the sources line, but still got the same error trying to install nvidia-glx. It wont upgrade at all.
I have since tried "dpkg-reconfigure -phigh xserver-xorg" and lowered the resolution to 800*600. Now the Xserver kind of loads but the screen just has a weird series of coloured lines and is not viewable. I need to boot in Recovery Mode to even use commands. I think that the nvidia drivers are still not installed properly, but cant work out how to install them again.

---

### Post by flathampster on 2006-09-15
This was due to the recent Xserver update that killed everyones X, but also because of something I had done to try and fix the problem before the official fix was released, that prevented me from upgrading nvidia-glx. Even after folowing the official fix I still could see the Xserver. I could hear the login sound affects though, so I knew the xserver was working just not the graphic drivers.

To resolve the issue I downgraded the nvidia drivers to the legacy version, then rebooted the PC. Natrually it didnt fix the problem and my monitor went offline. (probably bad for the graphics card). But I was able to boot up again in recovery mode and upgrade the drivers to the latest ndivia-glx which worked perfectly.

Thanks to this bug I now know more about configuring my X server than I ever would have otherwise, and for that Im happy. Im a windows tech that uses Linux at home, and my diagnostic skill got me through.However people from a non-technical background will struggle with problem like this.

---

