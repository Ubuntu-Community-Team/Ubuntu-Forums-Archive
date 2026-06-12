---
title: "Folder icon not showing up in Places"
date: 2010-11-03
forum: Desktop Environments
---

### Post by RBLevin on 2010-11-03
Hi. This is just a minor annoyance, but I am determined to understand what happened and how to fix it. I was testing Motion, following the instructions here: [http://www.chriswpage.com/2009/05/setup-an-advanced-webcam-security-system-with-ubuntu-8-04-and-motion/](http://www.chriswpage.com/2009/05/setup-an-advanced-webcam-security-system-with-ubuntu-8-04-and-motion/)

You'll note that the writers says to invoke Motion with sudo. Not thinking, I did that. Well, that caused the folders that Motion accesses to become owned by root.

I was directing Motion to store photos in home/myname/Pictures/Webcam. Needless to say, Motion rooted the Pictures folder. Now I couldn't add or delete files in those folders unless I was logged on as root.

Because Motion had also deleted files that were in that folder (not nice), I deleted the Pictures folder and restored it from a backup. In retrospect, I should have simply used chown and then restored the files.

I noticed after I deleted the folder that the custom icon was gone. I restored that by going into the folder's properties. BUT ... while the custom icon shows up when I view the folder in Nautilus, it does not show up in Places on the menu bar or in Nautilus.

I'm guessing this has something to do with symbolic links? I'm wondering how to restore the folder's icon in such a way that it is recognized by the entire system.

(I'm also wondering how to uninstall Motion so I can reinstall it without sudo, but that's for another forum.)

Thanks.

---

