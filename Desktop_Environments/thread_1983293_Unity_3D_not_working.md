---
title: "Unity 3D not working"
date: 2012-05-20
forum: Desktop Environments
---

### Post by glennsargent on 2012-05-20
I am running 12.04 which was installed as an upgrade from 11.10.  Unity is running in 2D mode for the default user and I cannot get 3D mode working. Unity_support_test indicates that my machine is capable of running in 3D mode. If I log in as a 'guest user' 3D seems to work perfectly.

Any help in getting 3D to work would be greatly appreciated.

---

### Post by sikander3786 on 2012-05-20
Welcome to the forums! :)

Please try commands mentioned under 'Reset Unity / Compiz' section from here:

[http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html](http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html)

---

### Post by glennsargent on 2012-05-20
Thanks sikander3786 for the help.

I tried all of the commands under Reset Unity/Compiz on the page you referred me to.

When I ran 'unity --reset', two panels appeared at the LSH of screen - one appeared like the 3D version and the other was the (current) 2D version.  When I loged out/loged in, I was back at 2D again where I started.  I ran the reset command initially and after running all of the others.

---

### Post by Peter09 on 2012-05-20
Check the third party drivers app, see if you need to install a graphics driver.

If nothing there can you post the output of:

```
lspci -C video
```

---

### Post by glennsargent on 2012-05-20
This is the output of the command (hopefully it is attached).  I have the latest version of nvidia-current installed.

---

### Post by glennsargent on 2012-05-21
I have been able to get Unity 3d working by trail and error but I don't know exactly how. :confused:

The last things that I tried before success, was to log into Unity by selecting Ubuntu on log in.  When Unity started up there was no menu on the LHS and no boarders.  Used the RHS mouse button to bring up Terminal issued Ctl-Alt-F1 logged in and then issued "unity --reset".  Unity stated up again with the menus and boarders and a terminal that had frozen.  Closed the terminal and the menus disappeared.  Shut down via Ctl-Alt-F1 and had a good nights' sleep.

Next day 3d was working!! :P

Hope this is helpful.

---

