---
title: "Problem with firefox 3.0"
date: 2009-06-24
forum: General Help
---

### Post by Headfirst on 2009-06-24
Ok so I am hoping this is the right forum to be posting in please redirect me if I am barking up the wrong tree.

A couple days ago I opened up firefox and it loaded a blank page with nothing in the URL bar, none of my bookmarks are there anymore, and the back forward refresh buttons are not clickable. So I checked preferences and it still was showing my desired home page I tried changing to default then repasting the address this did not fix the problem. Also when I click the home button rather than taking me to my homepage it takes me to mozilla.org but the URL bar is still showing nothing. If I continue to navigate I am unable to use any navigation buttons. At this point I checked the error console and saw there were a large amount of warnings that were all in different .css files. Now I decided to completely remove firefox and all of its dependencies and then reinstalling. This still did not fix my problem. I was browsing the web and have yet to find any solution. Granted I can still use the internet..it is not perfection and I demand perfection:)

Thanks in advance for any help,

Jason

---

### Post by philcamlin on 2009-06-24
hmm interesting error 

try this 

go to terminal

rm -rf .mozilla

should help

---

### Post by fooman on 2009-06-24
try renaming or even deleting the hidden .mozilla directory in your home folder.  it contains your firefox configuration files....something there may be corrupt and causing your problems.

first backup your bookmarks/favorites as this will start you off with a fresh firefox that has no bookmarks or extensions/themes installed!!

close firefox if it is open.

then open your home folder and in the taskbar, click view. put a check next to "show hidden files". then scroll down and find the .mozilla folder....right click on it and either rename it or send it to the trash (firefox will create a new one when it restarts).

 start firefox....hope that helps.

---

### Post by philcamlin on 2009-06-24
hehe i recommended that :D

---

### Post by Headfirst on 2009-06-24
sudo rm -rf did just the trick thank you so much.

But now my question is why:confused: Any insight?

Also, does anyone happen to know what I have to do to get flash videos to play I don't have a problem with youtube.com and all the stuff I have read was related to youtube videos not playing. I have installed the codecs that I need ( I hope ) 

Currently in preferences>applications I am using mplayerplug-in 3.55

Again thank you much fooman and philcamlin.


-Jason

---

### Post by lovinglinux on 2009-06-24
I recommend reading [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567). See quote below for explanation about your problem and a better solution.

> **lovinglinux said:**
> 

**[size="5"][color=#CC0000]Troubleshooting[/color][/size]**

Several Firefox problems are related to corrupted profiles and can be easily fixed by restoring a profile backup (see Backup section), by deleting the corrupted profile or deleting specific files inside the profile. Usually, there is no need to re-install Firefox.

I don't know why everyone recommends moving, renaming or deleting ~/.mozilla folder to solve Firefox issues. The ~/.mozilla folder is also the place where other Mozilla applications might store their profiles (Sunbird, etc), so deleting this folder will delete their settings too. 

Firefox profiles are stored under ~/.mozilla/firefox folder. So if you need to remove a Firefox profile to fix a problem, then delete, rename or move ~/.mozilla/firefox not ~/.mozilla.

Here are some common issues and corresponding solutions:


**Problems:**

[list][*] 
[*] **All bookmarks have disappeared and backups cannot be restored.**
[*] **Bookmarks changes are reverted after restart**
[*] **The Home Page is blank no matter what you put in the settings.**
[*] **Address bar does not work.**
[*] **Browser history does not work.**[/list]

**Solution:**

Delete the file *places.sqlite* from the profile folder. 



---

