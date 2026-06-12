---
title: "Tacker Applet popup won't go away."
date: 2009-05-09
forum: General Help
---

### Post by scatmandude on 2009-05-09
I recently upgraded to 9.04 and then ran Computer Janitor. Ever since I did this, when I start up I get a pop up that says: "Tracker Applet. There was an error while performing indexing. Index corrupted."

There are also three tabs to choose from in the popup: "Reindex all contents", "cancel", and "o.k." However, no matter which one I select it just keeps on popping up over and over. I finally just get rid of the popup by right clicking and selecting "move to workplace right", but the next time I start the system it happens again.

What can I do to fix this?

Thanks.

---

### Post by soro2005 on 2009-05-09
It's been answered many times, for instance [here](http://ubuntuforums.org/showpost.php?p=7239105&postcount=7). Also, you don't make friends here if you ask the same question in [multiple threads](http://ubuntuforums.org/showthread.php?t=1153624).

From the [release notes](http://www.ubuntu.com/getubuntu/releasenotes/904):
> Tracker index corruption

In some cases it can happen that the index of the "tracker" desktop search engine becomes invalid. A dialog will be shown, offering you to "Reindex all contents". This button does not work, and the tracker service might start to use large amounts of CPU and disk resources. As a workaround, please press Alt+F2 and run tracker-processes -r. This will be fixed in a post-release update soon (361205).

---

### Post by scatmandude on 2009-05-09
I did that and got this error popup reading:

/home/lab11/Pictures/Screenshot-Error-1.png

I hope you can view that. I also have no idea how to post a screen shot within my reply.

Thanks for all your help, I'll delete my post in the other forum.


Scott

---

### Post by soro2005 on 2009-05-09
You can attach an image by clicking on by clicking on "Manage Attachments" under "Additional Optoins." I can't see your screenshot, it's on your computer.

---

### Post by scatmandude on 2009-05-09
I think I managed to get it right this time.

Thanks for your help with all this.

---

### Post by soro2005 on 2009-05-09
Take the solution from the first link:
```
rm -rf ~/.cache/tracker ~./.local/share/tracker/data
```
in a terminal. Then reboot.

---

### Post by scatmandude on 2009-05-09
That seems to have done it. Thanks for all the help.


Scott

---

