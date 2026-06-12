---
title: "Set Resolution Above 640x480"
date: 2006-06-02
forum: Desktop Environments
---

### Post by Rydel on 2006-06-02
I installed Ubuntu 6.06 on my Dell Inspiron 1100 laptop, and I think Ubuntu is by far the best distro I've tried, but I have one problem: I cannot set the screen resolution above 640x480. I'm thinking that this is a driver issue, but I do not know where to look for one. Any ideas?

---

### Post by arsolto on 2006-06-02
Hello, partner, type in the Terminal the following command:

**sudo gedit /etc/X11/xorg.conf**

Substitutes in the archive all the lines that contain the available resolutions for:

**“1024x768” “800x600” “640x480” “1024x768” **

Then its resolution will start to be of “1024x768”.

---

### Post by durableapostle on 2006-07-16
Look here:
[URL="http://www.ubuntuforums.org/showthread.php?t=190022"]
http://www.ubuntuforums.org/showthread.php?t=190022[/URL]

---

