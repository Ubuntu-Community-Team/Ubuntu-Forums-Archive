---
title: "breezy-updates is giving me a error on a apt-get update with the following error"
date: 2005-10-13
forum: Desktop Environments
---

### Post by jabberwocky on 2005-10-13
Reading package lists... Done
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems

:confused:

---

### Post by Ronbo on 2005-10-13
Same thing here.

---

### Post by jdmpike on 2005-10-13
Did your installation fail to install past the gstreamer0.8 package?

I have a lot of packages that didn't get configured and I am getting the same error....

Anyone have any thoughts?

---

### Post by jabberwocky on 2005-10-13
i believe the solution to the problem is "apt-key update"

---

### Post by xcolour on 2005-10-13
I'm getting this too.  I tried apt-key update, but my keys were not changed.

---

### Post by gflores on 2005-10-13
Same.

---

### Post by psychicdragon on 2005-10-13
I got that same error earlier in the day but I was able to apt-get update successfully more recently. It may just be a side effect of the extreme load the servers are under right now.

---

### Post by jdmpike on 2005-10-13
I was able to:
1) start synaptic
2) remove my cd-rom as a repository
3) select ubuntu-desktop

Then apply and now everything is groovy - I hope that helps for all of you!

Take care.

---

### Post by Amaranth on 2005-10-14
This error will occasionally show up if you're trying to use apt right when the mirror you're using is updating. Usually waiting 5 minutes and trying again will help but with the load the servers are under right now it might take longer.

---

### Post by moopere on 2005-10-16
[QUOTE=Amaranth]This error will occasionally show up if you're trying to use apt right when the mirror you're using is updating. Usually waiting 5 minutes and trying again will help but with the load the servers are under right now it might take longer.[/QUOTE]

Its been stuffed all day here for me (I'm a bit miffed...took me most of the day to find a work around)

Check this thread if you need to get going and can't wait for a fix to the gpg error thingy:

[http://www.ubuntuforums.org/showthread.php?p=416599&posted=1#post416599](http://www.ubuntuforums.org/showthread.php?p=416599&posted=1#post416599)

---

