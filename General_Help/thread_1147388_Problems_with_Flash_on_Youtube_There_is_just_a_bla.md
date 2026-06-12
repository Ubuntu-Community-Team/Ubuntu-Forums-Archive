---
title: "Problems with Flash on Youtube: There is just a black screen"
date: 2009-05-03
forum: General Help
---

### Post by rasungod_7 on 2009-05-03
I have almost the same problem as Mega_Fauna in his thread

[http://ubuntuforums.org/showthread.php?t=1074523]("http://ubuntuforums.org/showthread.php?t=1074523")

I removed gnash, my computer said it didn't have adobe-flashplugin, and I reinstalled flashplugin-nonfree.

When I right click on the black screen it says "movie not loaded" and click on "about Adobe flash 10", I get this site:

[http://www.adobe.com/software/flash/about/]("http://www.adobe.com/software/flash/about/")

I do have NoScript installed but I disabled it. Then I disabled all of my plugins and that didn't help either.

Yesterday I installed xubuntu-desktop on my ubuntu computer. Maybe there is a conflict?

Other flash sites seem to work.

Can anyone help?

---

### Post by wpshooter on 2009-05-03
My "guess" is that you don't have Adobe Flashplayer installed correctly.

Go to this site [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/) and download and install the tar.gz version of Flash.

Write back if you need instructions on how to install.

---

### Post by rasungod_7 on 2009-05-03
Yes, can I please have some instructions on how to install?

---

### Post by wpshooter on 2009-05-03
> **rasungod_7 said:**
> Yes, can I please have some instructions on how to install?

1) Download tar version of Flashplayer to your /home directory.
2) Right click on the Flash tar file and then choose to extract to here.
3) Go to the terminal and change directories to the **install_flash_player_10_linux** directory.
4) Before issuing command to do the install, you need to find out what version of Firefox you are using.  Will be something like Firefox 3.0.10.  And more specifically what the **NAME** of the directory for the browser is.  For instance mine is /usr/lib/firefox-3.0.10
5) Make sure that Firefox browser is closed.
6) Issue the command:  **sudo ./flashplayer-installer**
7) Put in the path to your Firefox browser directory when prompted.

Good luck.

---

### Post by miegiel on 2009-05-03
Don't know if you're running 64bit ubuntu, but I'm a happy puppy since I installed the 64bit flash player. Check [_this thread_]("http://ubuntuforums.org/showthread.php?t=772490") if you're running 64bit.

---

### Post by rasungod_7 on 2009-05-04
The 64bit fixed the problem!

Thank you very much,

Rasungod_7

---

