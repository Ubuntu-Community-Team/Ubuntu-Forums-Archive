---
title: "Help, Terminal wont launch"
date: 2006-08-19
forum: Desktop Environments
---

### Post by ModBoyZZ on 2006-08-19
Hi all,


Just recently I've tried to launch terminal numerous times, and its a no go. When I click the icon, it looks like its trying to open, but nothing comes up. I've rebooted the system a couple times and still no luck.

Any suggestions? 


Thanks in advance...

---

### Post by taurus on 2006-08-19
Are you talking about the terminal from Applications -> Accessories -> Terminal?

---

### Post by ModBoyZZ on 2006-08-19
> **taurus said:**
> Are you talking about the terminal from Applications -> Accessories -> Terminal?

Yes

---

### Post by ModBoyZZ on 2006-08-19
Anyone? 

Do I need to reinstall ubuntu?

---

### Post by DBO on 2006-08-19
> **ModBoyZZ said:**
> Anyone? 

Do I need to reinstall ubuntu?

are you using compiz?  I have a good idea where your issue is if that is the case.

DBO

---

### Post by ModBoyZZ on 2006-08-20
Now that you mention it, I recently installed compiz. How can i remove it?

---

### Post by nativesun on 2006-08-20
> **DBO said:**
> are you using compiz?  I have a good idea where your issue is if that is the case.

DBO

I'm using compiz, and am having this same problem.  If you have a possible fix, I'm listening as well.

---

### Post by xtknight on 2006-08-21
Press Alt-F2 and type xterm to get some type of terminal open.  OK, now could you perform these three commands and report the result?

dpkg -s gnome-terminal | grep Version
dpkg -s gnome-terminal-data | grep Version
dpkg -s libvte-common | grep Version

Also, if you try and start gnome-terminal from the xterm can you report the error?

---

### Post by ModBoyZZ on 2006-08-21
dpkg -s gnome-terminal | grep Version
Version: 2.14.2-0ubuntu2


dpkg -s gnome-terminal-data | grep Version
Version: 2.14.2-0ubuntu2

dpkg -s libvte-common | grep Version
Version: 1:0.12.2-0ubuntu1

---

### Post by ModBoyZZ on 2006-08-21
(gnome-terminal:15987): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
gnome-terminal: symbol lookup error: gnome-terminal: undefined symbol: vte_terminal_set_opacity

---

### Post by Burke on 2006-08-21
Well, I'm not sure how to fix it. When I ran into that problem I just did apt-get install gnome-terminal, but it doesn't look like that will work for you. I know x-terminal-emulator is (exactly?) the same thing... can you launch that?

---

### Post by xtknight on 2006-08-21
Did you try these fixes?

[http://www.ubuntuforums.org/showthread.php?t=239238](http://www.ubuntuforums.org/showthread.php?t=239238)

---

### Post by ModBoyZZ on 2006-08-22
anyone?

---

### Post by mcduck on 2006-08-22
well, did you try the fixes suggested in the above post?

Anyway, this is how I solved it: ```
sudo ln -s /usr/lib/libvte.so.9.1.2 /usr/lib/libvte.so.4
```

---

