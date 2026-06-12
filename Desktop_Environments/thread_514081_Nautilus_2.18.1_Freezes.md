---
title: "Nautilus 2.18.1 Freezes"
date: 2007-07-31
forum: Desktop Environments
---

### Post by JoseArmandoJeronymo on 2007-07-31
Feisty Fawn on Intel Celeron 2.66 MHz 512 MB RAM
80 GB Nominal 73.3 GB (usable) HD:

hd1 Windows partition about 50GB;
hd5 Ubuntu - about 7 GB
hd6 swap - about 3 GB
hd7 home - about 10 GB

I have three users on my system, one (me) who uses it most of the time and the two for family members to log-in using Xdmcp (they seldom do).

When I log as my username I have verified that Nautilus freezes under the following circumstances:

- try to delete file from window
- try to display its version info from menu
- try to create a folder from menu

I then kill the application either by using program killer, system monitor termination or killall nautilus from terminal and a new instance of Nautilus replaces the frozen one however keeping the misbehaviour.

When logged as a different user or starting Nautilus with gksudo it works all right.

Also, I use Quanta+ (KDE) and manage to delete/rename files from its file management interface all right. I also noticed that Quanta lists files much faster than Nautilus.

Because my Linux partition is small (I did not antecipate adapting to Ubuntu so fast and decided to keep a large windows partition when partitioning my disk: a big operational mistake) and had no more than 800 MB free this morning,  I moved about 3 GB of music to hd1 but this does not seem to have solved the problem.

I hope this is the right place to post this message and any suggestions and ways to a solution will be most welcome.

Thanks in advance

---

### Post by JoseArmandoJeronymo on 2007-08-02
What is in fact happening is that Nautilus will not let me create a second window.

All three functions I mentioned on the original post (delete, display version and create new folder) require a new window.

When I try to create a new instance of Nautilus, it freezes and the original windows is blanked out. If I killall nautilus then the old window is killed and the one I requested is created.

I have also noticed from System Monitor that the original Nautilus process is started with these instructions:

--sm-config-prefix/nautilus-PXfjsy/ --sm-client-id (a identifier) --screen 0 --load-session /home/(user folder)/.nautilus/saved-session-IBU4VT

With a different user or gksudo there are no problems whatsoever.

---

### Post by JoseArmandoJeronymo on 2007-08-03
Problem solved!

When using System Monitor to kill another locked instance  of Nautilus, I right-clicked on its name and decided to check the Files Opened (I use French as desktop language so the function may not be called exactly that,  but it is the last one on the menu:)) list.

I then noticed one SVG file for some work I had done one week earlier and had no apparent reason to be on that list. Since I could not delete files with Nautilus I used Konqueror (all right, true sport should have been using the command line, but...) to send it to Trash.

I restarted Nautilus and the files opened list still showed that file but now in Trash (or, la Corbeille, which is one the most lovely spoken French words). Nautilus still hang as I tried to open another window.

Then I removed the files from the trash bin and presto1 I had my Nautilus back in full force.

BTW, when doing research on the problem I came across a bug report in Nautilus bugzilla regarding locking under very large SVG files.

The lesson learned is to check the files a misbehaving process opens.

---

### Post by kolyma on 2007-09-15
I just wanted to say thanks - I was tearing my hair out over this problem, and all I had to do to fix it was delete my most recent SVG. 

THANKS!  :KS

---

### Post by JoseArmandoJeronymo on 2007-10-22
Well, I never came to tear my hair out since I ain't got much of it left anyway LOL.
Thanks for thanking. It's great to learn that all this has been of use to someone else!

---

