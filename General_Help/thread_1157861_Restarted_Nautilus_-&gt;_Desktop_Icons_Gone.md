---
title: "Restarted Nautilus -&gt; Desktop Icons Gone"
date: 2009-05-13
forum: General Help
---

### Post by XCan on 2009-05-13
I installed a plugin and had to restart nautilus. I thought I was smart and killed nautilus, then proceeded to access one of my 'Places' to force it to restart. This basically worked, but none of my desktop icons are showing anymore and I don't get any menu when I right click on the desktop. Is there any way to reinvoke the desktop without restarting X?

---

### Post by KhurramM on 2009-05-13
I hope u can goto cli.

Execute on prompt:

metacity

Hope this works.

---

### Post by Peter09 on 2009-05-13
You may not have started nautilus correctly.

Try in a terminal

```
nautilus&
```

---

### Post by XCan on 2009-05-14
Ah, indeed I had to manually start nautilus. I just assumed that opening a 'place' would do it automatically. :)

---

### Post by CatKiller on 2009-05-14
I don't know about the other Places shortcuts, but the default Home folder shortcuts are for ```
nautilus --no-desktop
```

---

### Post by omnidecay on 2009-05-27
An issue that popped up for me with 9.04 ubuntu is my desktop icons disappear and you cant click on the desktop. Using "sudo killall nautilus" and then followed by "nautilus&" in the terminal fixed the issue. Just thought I would share.

---

### Post by AlexanderDGreat on 2010-02-10
Hi, I'm using JJ. Whenever I open my Trash, the icons will disappear on my desktop, and there's no window popping up to view the folder of my Trash.

What's wrong with my desktop?

So, you're right, it works when you nautilus& all icons appear again. But when I close the Terminal Window, the icons are gone again! How do you solve that? Or is there a bigger problem in my computer? Thanks.

---

### Post by AlexanderDGreat on 2010-02-10
By the way, here's the error that appears when I open my Trash.

```
alex@ubuntu:~$ Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: info_fn: file /var/lib/samba/usershares/public is not a well formed usershare file.
info_fn: Error was Path is not a directory.


** (nautilus:13198): WARNING **: Unable to add monitor: Not supported

(nautilus:13198): GLib-GIO-CRITICAL **: g_file_info_get_name: assertion `G_IS_FILE_INFO (info)' failed

** (nautilus:13198): WARNING **: Got GFileInfo with NULL name in trash:///, ignoring. This shouldn't happen unless the gvfs backend is broken.


(nautilus:13198): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed 
```

Can anyone please help me?

---

### Post by kavoura on 2010-02-26
I am now getting the same error messages in the terminal when trying to run Nautilus. This just starting happening today, a few minutes ago, without warning. One minute everything was okay, then suddenly when I tried to open a new Nautilus window, from the Places menu, it crashed and took out all existing open Nautilus windows. Even rebooting my PC twice has not cured the problem.

---

### Post by kavoura on 2010-02-26
From what I read elsewhere, the problem seems to be with libglib upgrading to 2.22 from 2.20, which causes the bug in Nautilus.

To revert to 2.20 I found this helpful

sudo aptitude install libglib2.0-0=2.20.1-0ubuntu2.1

---

### Post by AlexanderDGreat on 2010-02-27
@kavoura - thanks for the tip, yes I also saw that thread, but I'm scared of doing this, what is this glib? And should I just answer yes to all the following questions of this command? Thanks.

---

### Post by rnerwein on 2010-02-27
hi
in a terminal (not as root ) type: nautilus -p && nautilus

ciao

---

### Post by AlexanderDGreat on 2010-03-01
> in a terminal (not as root ) type: nautilus -p && nautilus - what's this for?

I tried it, said: Could not parse arguments: Unknown option -p

---

### Post by kavoura on 2010-03-01
> **AlexanderDGreat said:**
> @kavoura - thanks for the tip, yes I also saw that thread, but I'm scared of doing this, what is this glib? And should I just answer yes to all the following questions of this command? Thanks.

I'm guessing that glib is a Gnome Library. Not sure though, but it worked for me and everything works again. I cannot remember what I answered to any questions, I think I just selected the defaults (which usually just means pressing ENTER).

---

### Post by kickwin on 2010-03-02
> **kavoura said:**
> 

sudo aptitude install libglib2.0-0=2.20.1-0ubuntu2.1

This fixed my problem. Same problem AlexandreDGreat reported. On clicking Trash can/accessing SFTP on nautilus, my desktop icons disappeared/right click on desktop did not work. Now it is all fixed after doing the downgrade. 

I am disappointed to see errors like this on Ubuntu and afraid to recommend it to friends/parents who are not so much into googling and finding fixes for bugs.

PS: I use Ubuntu 9.04 Jaunty Jackalope

---

### Post by kendoori on 2010-03-02
I have the same problem in Karmic; and when I initially saw this fix (revert libglib) I tried it and it worked. After an update, I'm no longer able to fall back to this version. I show that I 2.22.3. If I try to force the version, I can only go back to 2.22.2. Anyone have a fix for this?

---

### Post by AlexanderDGreat on 2010-03-02
> I am disappointed to see errors like this on Ubuntu and afraid to recommend it to friends/parents who are not so much into googling and finding fixes for bugs. Very true.

Can anyone file a bug? Damn, my love & hate relationship with Ubuntu.

---

### Post by TxRxBuffer on 2010-03-06
I'm having the same problem.

---

### Post by huangweiqiu on 2010-03-06
You may tried to delete .Nautilus folder which under you home folder,and then reboot computer. If you don't see that folder,please press CTRL+H

---

### Post by TxRxBuffer on 2010-03-06
> 
You may tried to delete .Nautilus folder which under you home folder,and then reboot computer. If you don't see that folder,please press CTRL+H


I just tried that and it didn't help. I'm not sure what to do anymore. I tried everything thing that's be suggested. I can still access the files using command-line.

---

### Post by males on 2010-06-19
Hi,
I have the same problem with Ubuntu 9.10. I was do the downgrade glib, and now the desktop icons disappear only when I do right click on USB stick.
Does anyone can help?

---

