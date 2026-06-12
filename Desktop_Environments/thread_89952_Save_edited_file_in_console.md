---
title: "Save edited file in console"
date: 2005-11-13
forum: Desktop Environments
---

### Post by majkmil on 2005-11-13
I was trying to install ATI drivers via the instructions in the starter guide in Brezzy Help section. I must have done something wrong because when I rebooted I could't get in to XSERVER. I went into console and edited my xorg.conf file but I don't know how to save the edited file. Please help.    Mark

---

### Post by ow50 on 2005-11-13
[QUOTE=majkmil]I was trying to install ATI drivers via the instructions in the starter guide in Brezzy Help section. I must have done something wrong because when I rebooted I could't get in to XSERVER. I went into console and edited my xorg.conf file but I don't know how to save the edited file. Please help.    Mark[/QUOTE]
It depends on what editor you're using. Easiest console editor should be nano.
```
sudo nano /etc/X11/xorg.conf
```
The commands are at the bottom of the screen. ^ corresponds to Control. So to save, hit Ctrl+O and then Enter to confirm the filename.

---

### Post by majkmil on 2005-11-13
Thank you . If I need to go back to my back_up file can you tell me how to do this also. Thanks

---

### Post by NewWithoutClue on 2005-11-13
Could you not just "cp" the file to a different name? 
cp ./file.txt ./file.txt.back 
or you could just use the editor to save it as another name. I suggest the first suggestion before you edit the file Paul.

---

### Post by majkmil on 2005-11-13
Thank, I used this command,  (cp /etc/X11/xorg.conf-backup /etc/X11/xorg.conf )  this overwrote the original and all is well.   Thanks very much.  Now to find out what I did wrong when trying to install ATI drivers.

---

### Post by NewWithoutClue on 2005-11-13
i must have missunderstood, i thought you were asking how to backup the file...not restore a backup...but, i am glad you used what i said for you situation...even though it was not a sensable answer

Sorry,
Paul.

---

### Post by majkmil on 2005-11-13
Thank you,  I am still new and a command line is a little scary to me. But I am really learnig alot, and having a great time doing it.   Thanks again

---

