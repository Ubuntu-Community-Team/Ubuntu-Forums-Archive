---
title: "trash file help"
date: 2009-05-10
forum: General Help
---

### Post by jackbarnard on 2009-05-10
Hi, i recenty installed ubuntu linux 9.04 and i have deleted a few files by highughting the file and pressing the delet key as you would in windows, i thought this would move the files into the deleted items folder but it doesnt.  neither does right-clicking then choosing 'move to deleted items' strangely. i found the files i have been deleting by chance in the following directory:
/home/jack/.local/share/trash
do I have to keep going into this directory to clean up my deleted files? they seem pretty well hidden if u ask me! this is annoying as deleting items doesnt free up any memory.  help please!

---

### Post by jackbarnard on 2009-05-10
update: if i try to move the folders in the above directory into the deleted items folder, they disappear for a couple of seconds then reappear with a '.2' stuck on the end of te file name.

---

### Post by CatKiller on 2009-05-10
> **jackbarnard said:**
> i found the files i have been deleting by chance in the following directory:
/home/jack/.local/share/trash

That is the location of your Trash. The files being moved there when you select "Move to the Deleted Items folder" is expected behaviour. I don't know why you aren't getting the displays updated to reflect the fact that there are files in there though.

---

### Post by drs305 on 2009-05-10
You should be able to delete your own trash by right clicking the trash icon and selecting "Empty trash". As was mentioned, the folder you found is the trash folder. What is happening is that you are telling Trash to go to ... Trash, so it deletes it and puts it right back in the same place - which is where deleted files go. If using a file browser such as nautilus, if you are deleting things directly from the Trash bin use SHIFT-DELETE so they don't reappear.  The default way though is to right click the Trash icon on the panel or Desktop.

You might also want to check out root's trash, which resides as /root/.local/share/Trash in the 'info' and 'files' folders. This trash, like your own, takes up space until it is permanently deleted. Use SHIFT-DEL again if you are browsing to it.
```

gksu nautilus /root/.local/share/Trash

```

If you really want to know more about trash, check out the link to Trash in my signature line.

---

### Post by Xzilalnx2 on 2009-05-13
Thank you for the help you have provided. The "shift+delete" was probably the most useful.

My related problem: I have a "trash" icon on one of my panels. The problem is that it does not show any of the files that I have deleted.
 I was able to find them in the location: /home/userName/.local/share/Trash/files

I would expect that when I click on the "trash" icon on my panel, it should reveal the same files that[FONT=Verdana] nautilus[/FONT] does in the "/home/userName/.local/share/Trash/files" directory, but it does NOT. Also after having files in that trash directory, I right clicked on the "trash" icon and selected "empty trash" but this did not actually delete or permanently delete any of the files in question.

How can I get the "trash" icon on my panel to show the same files, and actually delete/permanently delete items when I use the "empty trash" option?

---

### Post by Xzilalnx2 on 2009-05-13
problem eas solved with a restart

---

### Post by CatKiller on 2009-05-13
Glad you got it fixed.

---

