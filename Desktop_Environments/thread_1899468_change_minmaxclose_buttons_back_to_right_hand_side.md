---
title: "change min/max/close buttons back to right hand side"
date: 2011-12-23
forum: Desktop Environments
---

### Post by cccc on 2011-12-23
hi

I've Ubuntu 11.10 with Unity Desktop.
Howto change apps buttons min/max/close from left to right hand side?

---

### Post by SnickerSnack on 2011-12-23
A google search for 'unity move window buttons' tells me you should use ubuntu tweak.

---

### Post by cccc on 2011-12-23
> **SnickerSnack said:**
> A google search for 'unity move window buttons' tells me you should use ubuntu tweak.

I've tried to install Ubuntu Tweak from:

[https://launchpad.net/ubuntu-tweak/+download](https://launchpad.net/ubuntu-tweak/+download) using:```

dpkg -i ubuntu-tweak_0.6.0-1~oneiric1_all.deb
```but get errors. 


BTW here is another solution:

[http://www.howtogeek.com/howto/13535/move-window-buttons-back-to-the-right-in-ubuntu-10.04/](http://www.howtogeek.com/howto/13535/move-window-buttons-back-to-the-right-in-ubuntu-10.04/)

and it seems to work well.

---

### Post by hackb0y294 on 2011-12-23
You've already found the easiest solution, but in case you want to try Ubuntu Tweak, the best way would be to run this in a terminal:

```
sudo add-apt-repository ppa:tualatrix/ppa

sudo apt-get update

sudo apt-get install ubuntu-tweak
```

---

### Post by Dennis N on 2011-12-23
There is a ppa for the new ubuntu tweak version for Ubuntu Oneiric only.

Information Here:

[http://ubuntu-tweak.com/source/tualatrix-next/](http://ubuntu-tweak.com/source/tualatrix-next/)

I believe that tool is what I used to briefly move them a while back. 

Even though the window buttons (on unmaximized windows) can be moved to the right, the buttons that appear on the upper panel when you maximize the window will remain on the left. So for consistency, I left all buttons on the left.

---

