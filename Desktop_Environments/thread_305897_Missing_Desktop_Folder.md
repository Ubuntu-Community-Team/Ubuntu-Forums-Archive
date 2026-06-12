---
title: "Missing Desktop Folder"
date: 2006-11-24
forum: Desktop Environments
---

### Post by dummey on 2006-11-24
My friend was using my computer go online and check something and when I came back my whole desktop folder was empty. On my desktop, however, I could still see and use all the things. I then restarted and now they are nowhere to be found. Help?

---

### Post by 23meg on 2006-11-24
Are they in your trash by any chance? And what does ```
ls ~/Desktop

```return?

---

### Post by dummey on 2006-11-24
~/Desktop returns /home/dummey/Desktop

They are most definitely not in my trash. Before I restarted I could copy and run everything on my desktop, they just didn't show in the browser.

---

### Post by 23meg on 2006-11-24
I meant the output of the *ls* command in that directory; what does it return? Better if you try it with the -a option```
ls -a ~/Desktop
```By the way, are you using GNOME, with Nautilus as your file manager? I've just tried deleting a file from my desktop folder with a separate Nautilus instance, and its icon disappeared instantly from the desktop as well. Same goes for using the *rm* command from a terminal. This is with Edgy's GNOME 2.16.1 .

---

### Post by dummey on 2006-11-24
Using edgy with gnome and nautilus. Output of the ls command shows an empty folder. Normally it does disappear automatically, but it waited until the restart this time. None of the desktop items can be found with the search command and they are not in my trash. I am also sure that my friend did not delete them from my trash can because he doesn't know how to.

---

### Post by 23meg on 2006-11-25
Any chance your friend was able to navigate to your desktop folder in a terminal and wipe everything? One more possibility: do a system wide search if you haven't; your friend may have moved the files somewhere accidentally.

---

### Post by dummey on 2006-11-26
negetive on both. Large folders that I don't use on my profile folder have also been disappearing. Is this a sign that I need to reformat and do a clean install?

---

### Post by 23meg on 2006-11-26
You mean outside your home folder? Anything on your system shouldn't be disappearing without reason; do a S.M.A.R.T. check as well as a *fsck* on your HD to make sure it's working as it should. If it isn't, rescue whatever data you can and rid of it.

---

