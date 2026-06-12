---
title: "I think i broke my xorg file."
date: 2006-08-14
forum: Desktop Environments
---

### Post by offramp13 on 2006-08-14
So i tried to install compiz on my 64 bit amd with [this]("http://www.ubuntuforums.org/showthread.php?t=131267") and when i got the the step where you reboot, it gave me some confusing error message that i dont understand. I think it may have something to do with the xorg file...I dont know im a pretty big n00b when it comes to ubuntu, ive only had it installed a week or two. Would much appreciate help, thanks.

---

### Post by iamhugeinjapan on 2006-08-14
Do you get dumped to a console login instead of the gui login?

---

### Post by offramp13 on 2006-08-14
yes, i do

---

### Post by iamhugeinjapan on 2006-08-14
When logged in:

```
sudo vi /etc/X11/xorg.conf
```

That will get you into an editable xorg.conf which you can undo/comment out your changes in. It wont get you into XGL but back to a useable Ubuntu at least :)

If you're unfamiliar with using Vim editor, here are some commands:
[http://www.tuxfiles.org/linuxhelp/vimcheat.html](http://www.tuxfiles.org/linuxhelp/vimcheat.html)

---

### Post by offramp13 on 2006-08-14
Thank you for your help, but my buddy suggested to use the "startx" command, and that did the job for me, and i could edit xorg using gedit. Thank you for your help though.

---

### Post by iamhugeinjapan on 2006-08-14
Good to hear. I was in a situation once where I couldn't even do startx so Vim saved me. Keep it in mind for any future woe :).

---

