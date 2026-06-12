---
title: "Firefox launcher not working"
date: 2005-11-07
forum: Desktop Environments
---

### Post by fossean on 2005-11-07
****The Firefox launcher on the toolbar does not properly launch the program, it locks up immediately. It will successfully launch when I type sudo -H /usr/lib/mozilla-firefox/firefox in terminal. 

I have searched thoroughly but can't seem to solve this. Under launcher properties, the command is firefox %u. I have tried other suggested lines with no luck (/usr/lib/mozilla-firefox/firefox). Also tried changing the permissions.

I really can't understand why this should be so difficult.

---

### Post by linbetwin on 2005-11-07
Try removing the launcher and make a new one.

---

### Post by 23meg on 2005-11-07
Did this by any chance start happening after you installed some plugins and/or extensions? If you only have the standard Ubuntu build of Firefox, make a new launcher with just the command "firefox" and see if it works. And don't launch Firefox with sudo; it's a security risk.

---

### Post by fossean on 2005-11-07
Thank you for your replies. I have just tried both suggestions above without success. I do have several extensions, but FF was working fine over the course of several sessions before this problem arose. Have tried uninstalling/reinstalling Firefox and it didn't help. I have considered reinstalling Ubuntu from scratch, but it doesn't appeal; I'm pretty new at this andI know it would take me hours just remembering everything I did first time round... ndiswrapper for wifi was nearly the end of me.

---

### Post by fossean on 2005-11-07
I found a partial solution in this post [http://ubuntuforums.org/showthread.php?t=87049](http://ubuntuforums.org/showthread.php?t=87049)

I renamed the .mozilla folder in Home directory and Firefox now launches successfully from the toolbar launcher. A new .mozilla folder has been created with new profile, so will have to reinstall extensions and bookmarks backup. Not sure why this works, but I'm glad to have solved this; obviously didn't search properly the first time round.

I'm very impressed with Ubuntu generally. Mostly it works out of the box, and the support on the forum is excellent. 

The only downside is that I can't leave it alone. Time flies when I'm playing around with Ubuntu, to the point that I 've only had twelve hours sleep in three days.

---

