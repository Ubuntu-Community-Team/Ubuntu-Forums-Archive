---
title: "Different xorg.conf's for different users"
date: 2006-09-04
forum: Desktop Environments
---

### Post by sniper85 on 2006-09-04
On my main user account I am using twin view to use 2 monitors and XGL. Is there any way to make it so that when I login with another user account it uses a different xorg.conf so that there isn't twinview and just a stamdard X server??

---

### Post by nikhilk on 2006-09-04
I am not sure if this will work correctly, just thought it might help you experiment and find your own solution.

The actual xorg.conf (/etc/X11/xorg.conf) can be replaced by a symlink to another symlink somewhere, maybe something like /my_xorg_conf/xorg.conf. This link then points to the actual file in the home directory, maybe something like ~/xorg.conf, this solution requires the /my_xorg_conf directory to be writable by all the users concerned.

The symlink /my_xorg_conf/xorg.conf must obviously be changed every time a new user logs in.

So the link chain can be like
/etc/X11/xorg.conf -> /my_xorg_conf/xorg.conf -> ~/xorg.conf
The first link of this chain will remain static, whereas the second link should be changed automatically per user.

I hope you are not confused cause it feels like I am ;)

---

### Post by sniper85 on 2006-09-04
Ill try and see if I can get it to work. In the mean time anyone else know of any other ways??

---

### Post by sniper85 on 2006-09-05
Can't seem to get this to work is there anyway to do this?

---

