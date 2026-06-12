---
title: "Trash Bin Problems"
date: 2005-05-13
forum: Desktop Environments
---

### Post by dmccarney on 2005-05-13
I seem to have encountered a strange bug with the trash icon on my gnome display.
I emptied it one day and for some reason it is stuck thinking that there is still 1 trash item in it. So it looks full on the taskbar. I've tried emptying it again but it still stays at 1 thing in the trash. I've enabled viewing hidden items when I open the trash as well thinking that maybe the 1 item is hidden or something, but that didn't work either. Its not a major issue. If anyone can help, I'd appreciate it.

---

### Post by Sam on 2005-05-13
Maybe you haven't the permission to remove it. Do it manually with
```
$ sudo rm -rf /home/<your username>/.Trash/*
```

---

### Post by Maestro23 on 2005-05-13
[QUOTE=Sam]Maybe you haven't the permission to remove it. Do it manually with
```
$ sudo rm -rf /home/<your username>/.Trash/*
```[/QUOTE]

Just getting ready to post this myself.... Beat me to it... :wink:

---

### Post by rusi_pathan on 2005-05-13
This happens to me too (using warty). Whenever I empty the trash bin the taskbar icon doesnt get refreshed i.e. it still shows the trash inside. Though restarting gnome makes it all right.

---

### Post by dmccarney on 2005-05-13
Ok, I rm'd the contents of my trash just to give it a try, It still says there is 1 thing in there. Its not gone and the taskbar icon is still full :( How does one go about restarting gnome? Can I do it without a reboot?

---

### Post by Sam on 2005-05-13
I don't know if it'll work, try:
```
$ killall gnome-panel
```

---

### Post by monkey89 on 2005-06-05
The issue seems to be with gamin, the program that tells gnome when files are changed.  Not sure if this is the best way really, but if you enable inotify, the trash applet seems to work again.  My friend just had this issue, so I'm going by what he said worked.

If you don't know how, you need to add "inotify" to the kernel options.  Edit /boot/grub/menu.lst (with sudo, of course), and theres a line that says kopts or something, don't uncomment it, just add "inotify" to the end and run update-grub.

-Monkey

---

### Post by Iwantu_ubuntu on 2005-06-24
[QUOTE=Sam]Maybe you haven't the permission to remove it. Do it manually with
```
$ sudo rm -rf /home/<your username>/.Trash/*
```[/QUOTE]

New to Ubuntu...so my question is why doesn't the regular user account have permission to empty the trash can? I've used FC3 and FC4 a bit and was able to empty the trash can without going thru a command line (which by no means looks easy to remember).  Anyway to give my regular user account permission to empty trash? i.e. right click and Empty Trash.

TIA

---

### Post by Alexander Kirillov on 2005-06-24
[QUOTE=Iwantu_ubuntu]New to Ubuntu...so my question is why doesn't the regular user account have permission to empty the trash can? I've used FC3 and FC4 a bit and was able to empty the trash can without going thru a command line (which by no means looks easy to remember).  Anyway to give my regular user account permission to empty trash? i.e. right click and Empty Trash.

TIA[/QUOTE]
 Normally, a regular  user does have permissions to empty trash - but in htis case something went wrong.

---

### Post by Iwantu_ubuntu on 2005-06-24
[QUOTE=Alexander Kirillov]Normally, a regular  user does have permissions to empty trash - but in htis case something went wrong.[/QUOTE]
 Strangest thing?!  After I typed "sudo rm -rf /home/<your username>/.Trash/*" in command prompt it emptied the trash can and now I'm able to right click and empty anything in the trash can... :???:

---

### Post by Alexander Kirillov on 2005-06-24
[QUOTE=Iwantu_ubuntu]Strangest thing?!  After I typed "sudo rm -rf /home/<your username>/.Trash/*" in command prompt it emptied the trash can and now I'm able to right click and empty anything in the trash can... :???:[/QUOTE]
 It shows that probably .Trash had wrong permissions (have no idea why - it shouldn't have...). After you removed it, it was recreated - with correct permissions.

---

### Post by John Jason Jordan on 2005-06-25
[QUOTE=Alexander Kirillov]It shows that probably .Trash had wrong permissions (have no idea why - it shouldn't have...). After you removed it, it was recreated - with correct permissions.[/QUOTE]
 I just experienced the same thing. But the problem was permissions on the files in Trash, not the permissions on the Trash folder. I had a thousand files or more and I deleted them fine by right-clicking and selecting Empty Trash. But that left two folders stuck in Trash that required root privileges to remove. I got them out with the "sudo ..." line discussed above, but doubtless this will happen again sometime.

---

### Post by ssck on 2005-06-25
this problem has happened to me too.the file is gone after it is deleted but it still shows up in the trash can.i'll normally leave it as it is as after a re-login or re boot, it will be gone.or i'll remove the trash can from the panel and add it back.it will be back to normal.

---

