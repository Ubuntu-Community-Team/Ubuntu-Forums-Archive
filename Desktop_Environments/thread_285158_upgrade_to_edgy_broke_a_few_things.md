---
title: "upgrade to edgy broke a few things"
date: 2006-10-26
forum: Desktop Environments
---

### Post by jaredvolkl on 2006-10-26
I kicked off my Edgy Eft upgrade this morning which went without a hitch. After the reboot, I was introduced to more-or-less my same old desktop.

I've run into a few minor problems since then though. First of all Firefox would not launch. I tried it from the terminal and found it was getting a seg fault. The next thing I tried was launching it with sudo which worked. So I figured it was a problem with an extension or configuration from my old version of Firefox. No problem, just backed up my profile folder and let Firefox generate a new one (you also have to remove a few lines from profiles.ini). After copying back over my bookmarks and extensions, it is just fine.

Second, I used to see thumbnails of images instead of the standard icon. I've checked the preferences for this and it is set to display thumbnails on images under 5MB. I'm sure all the files I have in my images directory are under that limit and so I'm a little confused as to why it isn't working.

Lastly, my mouse scroll wheel stopped working. I have the ZAxisMapping "4 5" line in my xorg.conf and I even tried regenerating the file from the terminal without any success. What the scroll wheel seems to be doing now is scrolling through my history in Firefox. So when I'm on a tab and I scroll up, it's like I keep hitting the back button.

Any and all help with fixing these minors bugs would be much appreciated.

---

### Post by jaredvolkl on 2006-10-27
I fixed the issue with my mouse scroll wheel. Appearently in the switch to Edgy, the button numbers for the scroll wheel changed from 4 and 5 to 6 and 7. Use xev to determine what buttons your scroll wheel uses and change the ZAxisMapping line in your xorg.conf file. Restart X or reboot and you're set.

Still no luck on the image thumbnails, but I'll post here if I figure out a solution.

---

### Post by jaredvolkl on 2006-11-10
> **jaredvolkl said:**
> Still no luck on the image thumbnails, but I'll post here if I figure out a solution.So in messing around this week I manged to get my image thumbnails back. All I did was turn them off completely and then turn them back on and that was it.

---

