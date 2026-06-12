---
title: "updating failure"
date: 2009-05-20
forum: General Help
---

### Post by nir2000 on 2009-05-20
Hello!
Few days ago I tried to up date Ubuntu 8.04 through the update manager but the files took too long to download. Since I had no patient to wait for the download to finish I pressed cancel, and I was presented with all the names of all the files that were unable to download. later, when I tried to update again my system the update manager did not show all the files that I aborted downloading, and simply said that there are no files to download. Since this occurrence happened to me I am experiencing forced logged ins(the screen goes dark and the log in screen appears  immediately after). My question is: how do I install all the files I aborted downloading as mentioned before. And what can I do to stop my PC to go to the log in screen abruptly.
Please I need help because it is very disturbing.
Thank you in advance 
Nir

---

### Post by 3rdalbum on 2009-05-20
The problems are unrelated. If a program or graphics card driver manages to crash the X server (graphical display program) then all graphical programs will die and X will start up again, at the login screen.

There's no way that merely downloading updates could cause this problem; check that you haven't upgraded a video card driver recently. Or check that the system hadn't already downloaded all the files and was actually updating!

If you aborted downloading the files, then the files you did download are still cached. Apt won't re-download files that it already has. If this isn't the problem, then just reloading the package list should do the trick - in the update manager you press the Check button and this will do it.

---

