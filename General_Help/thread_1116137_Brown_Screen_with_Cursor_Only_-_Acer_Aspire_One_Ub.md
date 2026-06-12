---
title: "Brown Screen with Cursor Only - Acer Aspire One Ubuntu 8.10"
date: 2009-04-04
forum: General Help
---

### Post by drewsus on 2009-04-04
Hello all,

So, I have run into a problem today with my Acer Aspire One running Ubuntu 8.10. I have had it running Ubuntu for quite some time with no problems  and today I was trying to get ffmpeg going with mp3 support and now when I try to login all I get is a light brown screen with my arrow cursor and the tribal login sound. Nothing else, not even in fail safe mode. Oddly enough, I have gnome-do running on start up and if I press <super>+space the prompt comes up for that. But, if I try to launch anything it stays brown with the cursor. Ive tried resetting x org. Running in recovery mode seems to yeild no positive results. 
Now, I will say that I tried using someones tutorial which I am having trouble finding again, but iirc he said to delete all .a and .so files that start with something similar to libav* in /usr/lib/ and so I did. I am imagining that this is the root of my problem? But, it could also be unrelated. 

I tried accessing trash with gnome-do and then emulating the key sequences to restore all files that were in the trash (ie. <ctrl>+A to select all, <alt>+E for edit menu and R to restore). That seems to have done nothing and there is no way of telling if that was successful in restoring them anyway. 

Furtehermore, I do see ONE thing when I boot-up for the first time after my netbook is off. Whenever I boot-up like this when my netbook was working fine a window popped up asking me to enter my password so the keyring could access my wireless network. Always a nuisance, But, I still see that popup when get the brown screen and cursor now as well. But, that is it. 

Additionally, I see nothing when I press <alt>+F2. 

PLEASE HELP asap! *I have exams right now and need access to this computer!*

Thanks in advance, 
Drewsus


Here is the tut that mentioned to delete those files:
[http://juliensimon.blogspot.com/2008/12/howto-compiling-ffmpeg-x264-mp3-xvid.html](http://juliensimon.blogspot.com/2008/12/howto-compiling-ffmpeg-x264-mp3-xvid.html)
(Last part of step 0 just before step 1 begins)

---

### Post by drewsus on 2009-04-04
I put the live cd on a usb stick, got in there, found the trash from my install, restored those deleted files and... fixed it. What a stupid tutorial there. 
I want to punch that author in the throat. But instead I will now EAT SOMETHING.

---

