---
title: "nautilus-actions Places-&gt;Desktop opens with wrong app"
date: 2009-05-03
forum: Desktop Environments
---

### Post by doas777 on 2009-05-03
Update: See the resolution to this problem on this thread: [http://ubuntuforums.org/showthread.php?t=1151325](http://ubuntuforums.org/showthread.php?t=1151325)

-----------------------------------------------------------------------------------------------------------------------------------
My Places Menu "Desktop" and "Home Folder" and all my bookmarks open with the Mirage image viewer instead of opening with nautilus. 

I installed Mirage and the Nautilus-Actions packages and opened a folder with mirage, by selecting open with other application, and selecting it from the list.

Windows opened via nautilus work just fine, but i have to get an instance of it open first.

I've selected folders and told them to open with "open folder" from the list, and even tried supplying 'nautilus' as the command. I've seen references to an "open with..." tab in file properties, but I do not have one. likely related to this bug: [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/366963/+viewstatus](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/366963/+viewstatus)

If i uninstall nautilus actions, the problem goes away, so I'm guessing that it has something to do with the problem.

any ideas?

---

### Post by doas777 on 2009-05-03
hmmm. the issue still persists if I remove nautilus-actions and leave mirage in place. I guess it's a gnome/nautilus thing after all.

I'm doing a search of my hdd looking for files with text containing 'mirage' but it'll take alnight to complete.

---

### Post by doas777 on 2009-05-06
ok, since there are no hits here, and I've established that the issue is not with nautilus-actions. i will close this thread, and open a new one based on a the gnome issue specifically.
 
I hate to create a new thread, but can't figure out how to edit the thread title (and I've looked). based on this thread: [http://ubuntuforums.org/showthread.php?t=839064](http://ubuntuforums.org/showthread.php?t=839064) it is not possible without admin intervention, and I imagine that they are too busy to be bothered about it.

thanks,
Franklin

---

### Post by doas777 on 2009-06-24
this issue has been addressed on the thread linked above (5/6 post). check it out!

---

### Post by frytek on 2009-10-19
gedit .local/share/applications/mimeapps.list

and in the section 
[Added Associations]

find the following line and make it similar to this: 

inode/directory=nautilus-folder-handler.desktop

by removing the extra launchers (the first one is most probably your "wrong" application)

---

### Post by Torchmann on 2010-12-26
All this time using ubuntu and I never had the problem till recently with my new install of ultimate edition 2.8.
Here's what happens
I wanted to open not just a single song but to open the whole file with VLC (not the default)
when I opened the folder with VLC, nautilus made VLC the default...Not for music files...but for file folders.
it is not a glitch or a bug.
It was me!
I opened the file folder with nautilus setting VLC as the default becuase I did not uncheck "remember this..." which is by default checked positive
So I unchecked "remember..."  and VLC now is the top selection on the list of apps in Nautilus i can chose to open the folder with but it is not set as the default and the folder opens normally in file browser. 

This thread taught me how to fix it
And my post here will teach you how to not break it again.
Bye bye

---

