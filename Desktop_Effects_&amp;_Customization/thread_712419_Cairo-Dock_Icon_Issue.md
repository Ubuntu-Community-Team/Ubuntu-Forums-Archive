---
title: "Cairo-Dock Icon Issue"
date: 2008-03-01
forum: Desktop Effects &amp; Customization
---

### Post by wierzbicki on 2008-03-01
Hi.  I installed cairo-dock the other day and have been playing around with it a bit.  I started with one of the themes and modified it to my liking, adding icons, deleting some default icons, etc.  A problem I can't seem to solve is if I logoff, and then log back on, when cairo-dock starts, the default icons I deleted show up along with the icons I modified and kept.

Any ideas about what's going on?

---

### Post by tact on 2008-03-01
Maybe you need to save the modified theme...  right click on the dock, manage themes, save it under a name of your choice.

see if that helps.

---

### Post by wierzbicki on 2008-03-01
I tried that.  Still doesn't help.  Even if I load the theme I saved, the default icons appear :confused:

---

### Post by tact on 2008-03-01
Hmmm weird.   Sorry I cannot help further as it just works as expected for me here.  :(

---

### Post by wierzbicki on 2008-03-01
Could it be that I forgot to install something from the site?

[https://developer.berlios.de/project/showfiles.php?group_id=8724&release_id=14273](https://developer.berlios.de/project/showfiles.php?group_id=8724&release_id=14273)

I didn't install the sources tar.bz2.

---

### Post by tact on 2008-03-02
You don't need to install the sources...  

I cannot connect to the berlios website at the moment but if I remember correctly there are 2 deb files (cairo-dock is one and the other is plugins).   

You need to download the 2 deb files  and install the cairo-dock one first, then the plugins.  

I think there were also some "glitz" or "libglitz" packages that also need to be installed.  (These are in normal ubuntu repositories so installation is like sudo apt-get install libglitz1   ....  or similar)   Sorry I cannot be more explicit as my net connection is too flakey at the moment (tropical storm).

If you have all that (2 debs and the libglitz things installed) then thats it....  def no need to install the sources.

---

### Post by YeFFreY on 2008-03-05
It's one of the many problems I got with cairo dock. Sometimes, it disappears and I need to reload it, sometimes, a closed application(stop running) is not deleted from the icon tray, hard to delete some of the applet...
Need log on - log-out to apply some parameters...

And I also tried AWN : 5 minutes... too buggy...

GOD !

I use "rocket dock" under VISTA : That software is a real piece of heaven because it works ! no crash, drag & drop features,... I miss it a lot under ubuntu...

You software developpers for linux : Please make it bug free before going to add a lot of features... a simple working tool is better than a crappy soft with a thousand features which crash the computer...

Sorry to be agressive but, when I read all over the web that vista is worst than linux : try it and you'll live in a world where every hardware works, where a simple dock run ! no more 500 packages to install (thanks synaptics because that one is great) for a simple media player...
I like vista, I'm a developper and windows is the default environnement but I'm a JAVA dev, so I like that my tools works on a lot of platform so I try linux (ubuntu) but I don't like it a lot...

A winUser who wish to be a linux(desktop, no more bash please...) friend :)
:guitar:

---

### Post by larryfroot on 2008-03-05
yep, the man was right about libglitz...I popped libglitz glitz into the search box in synaptic and there they were....doing their bit for the cairo-dock.

---

### Post by Kasbell4 on 2008-03-17
i have a question about cairo-dock, if anybody can help me--

I just changed my icons for launchers, but when i open an application, the applications have the older/uglier icons. how do i fix this? any thoughts?


thanks, cause i really suck at this apparently

---

### Post by g_dwarf on 2008-03-28
I'm trying to find a solution for the same problem, it's just that for the launchers cairo-dock can use custom icons, but for running applications it takes the system icons, which will be the enlarged .png ones and look very anti-aliased. When I find a solution I'll post it here.

---

