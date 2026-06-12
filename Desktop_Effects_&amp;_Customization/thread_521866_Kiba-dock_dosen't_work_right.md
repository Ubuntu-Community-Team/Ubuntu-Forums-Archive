---
title: "Kiba-dock dosen't work right"
date: 2007-08-09
forum: Desktop Effects &amp; Customization
---

### Post by arvvvs on 2007-08-09
Hi guys,
I recently installed ubuntu, and i decided to install kiba dock.  After much finding i found it, but...
whenever i tried to run it, this is what happened
[[IMG]http://img380.imageshack.us/img380/4060/screenshothq1.th.png[/IMG]](http://img380.imageshack.us/my.php?image=screenshothq1.png)

any help?

---

### Post by overdrank on 2007-08-10
> **arvvvs said:**
> Hi guys,
I recently installed ubuntu, and i decided to install kiba dock.  After much finding i found it, but...
whenever i tried to run it, this is what happened
[[IMG]http://img380.imageshack.us/img380/4060/screenshothq1.th.png[/IMG]](http://img380.imageshack.us/my.php?image=screenshothq1.png)

any help?

HI if you have not found any info on the issue you may try the forums in Kiba-dock
[http://www.kiba-dock.org/](http://www.kiba-dock.org/)
Hope this helps and good luck!

---

### Post by mikibg on 2007-08-11
new kiba is best version of kiba i install!!!!
looks great works nice and i think in future this will be the best dock.
2 download last kiba 
svn co [https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk](https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk) kiba
install kiba-dock,kiba-plugins,kiba-dbus-plugins
kiba-dock install with 
./autogen.sh --prefix=/usr/local --enable-akamaru
and rest with ./autogen.sh --prefix=/usr/local 
new kiba have reflection and looks better then avant when u use podest.
akamaru is fix and so many things.
[[IMG]http://img38.picoodle.com/img/img38/9/8/11/t_screenshot2m_9423de8.png[/IMG]](http://www.picoodle.com/view.php?img=/9/8/11/f_screenshot2m_9423de8.png&srv=img38)

---

### Post by strungoutfan78 on 2007-08-17
in order to completely install kiba-dock successfully i had to merge the instructions in the previous post and the instructions found here [http://ubuntuforums.org/showthread.php?t=268645&highlight=libakamaru]("http://ubuntuforums.org/showthread.php?t=268645&highlight=libakamaru")

i only had to do the whole automake thing in the beginning of the first post.  then i came back here and followed the links to the sourceforge files.

after all was said and done, i tried to run kiba-dock and i got an error message because it couldn't seem to find **libakamaru.so.0**.  what i had to do before i could get it to start was copy eerything with the name "**libakamaru**.*" from /usr/local/lib to /usr/lib.  after that i was golden.  hope this may end up helping someone as i couldnt find anyone else with the same problem.

cheers. :guitar:

---

