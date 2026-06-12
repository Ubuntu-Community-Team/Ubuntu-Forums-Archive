---
title: "Desktop background problem"
date: 2006-09-18
forum: Desktop Environments
---

### Post by msandoy on 2006-09-18
While moving some files from a locl disk to a USB disk, the copy process failed, and almost everything locked up. Tried to switch to console(ctrl+alt+F2), to do a sudo reboot. Was able to log in and do the command, but ended up having to use the reset switch on the computer. 

After restarting, all Icons are gone from my desktop, and I can not access the right click menu on the desktop itself. 

Everything else seems to be working, but this is irritating.

Any ideas on how to fix this?

---

### Post by yota on 2006-09-18
I don't know what the specific problem is... but I strongly suggest you to force a file system check before anything else; type in a terminal:
```

sudo touch /forcefsck

```
and reboot.

The system will do a check on next start, maybe this will not fix your desktop, but it's a good practice after an hardware hang.

---

### Post by msandoy on 2006-09-18
Tried the above sollution, but there is no difference. Still no icons or right click menu on desktop. The computer with this problem is operated via VNC remote connection, but the problem is the same when I operate it locally.

---

### Post by yota on 2006-09-18
Ok, now at least we are sure is not something worse than it looks.

Launch gconf-editor and go to /apps/nautilus/preferences/ key; is show_desktop flagged? (if not the behaviour should be like the one you're experiencing)

Have a look at apps/nautilus/desktop too and make sure that the icons you need are selected.

Let me know.

---

### Post by msandoy on 2006-09-18
Thanks for the tip, but sadly it did not help me this time. 

Well, in gconf-editor everything looks as it should, no need for me to enable anything. All the icons that I want displayed on my desktop is located in ~/Desktop as usual. No change there. I do not have any permanent device icons except mounted removable drives. Those are also missing after this problem occured.

---

### Post by PRGUY85 on 2006-09-18
Im havint the same problem...any help would be appreciated...

---

### Post by msandoy on 2006-09-18
I still havent found any solution, I can't find anything wrong, so please if anyone have found a solution, I would apreciate to hear about it. Have tried to search for this in the forum, but no luck...

---

### Post by yota on 2006-09-19
Hi,

please try to create a new user and log on with that.
If the desktop is ok we can narrow the search to the gnome configuration, and eventually reset it.

If it still does not work... I'm getting out of ideas :(

---

### Post by msandoy on 2006-09-19
Well, I created another user, logged out and logged in with the new user without rebooting. Desktop background is ok, and the right click menu works as it is supposed to on the new user. Still the same problem with my own account. :-(

Will continue looking later today. gtg for now.

---

### Post by yota on 2006-09-19
Ok, at least we have a workaround:

if you delete .gconf, .gnome, .gnome2_private, .gconfd and .gnome2 from your home dir (before logging on) the default gnome config will be recreated.

Before this extreme solution you can spend some time trying to guess what's wrong with your current config, expecially looking at differences from the default.

---

### Post by chavo on 2006-09-19
Make sure nautilus is running also, it is what paints the icons and background.

---

### Post by msandoy on 2006-09-19
Ok, I will look around, and I will post if I can find what has happened. From what I can see, I am not the only one to experience this problem. Thanks for the help so far...

---

### Post by msandoy on 2006-09-21
This is very strange, I have been occupied the last two days, and today everything has come back to normal on my desktop. The computer has been on the whole time. All of a sudden when I looked at it just now, All the icons had returned. I only had to set the background picture. Even the right click menu has started working again. I have not done anything with any files. I have no explenation to how this happened. Just glad it is back to normal. :-)

---

### Post by puppy on 2006-09-21
You've got to hand it to those gnomes - you probably left some food out and they thought it was an offering or something and put everything back the way it was in gratitude  :) 

I had a similar problem recently - on third or fourth reboot everything was miraculously ok... :rolleyes:

---

