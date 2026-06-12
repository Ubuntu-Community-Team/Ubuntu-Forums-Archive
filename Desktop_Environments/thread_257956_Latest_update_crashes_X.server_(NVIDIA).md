---
title: "Latest update crashes X.server (NVIDIA)"
date: 2006-09-15
forum: Desktop Environments
---

### Post by godefroy on 2006-09-15
Hello...im a ubuntu user!
Last night i made the kerne image update and rebooted my pc , then the x.server crashed...it simply wont load with my nvidia card!

Is there a fix to this issue? 
Tks

---

### Post by wkulecz on 2006-09-15
I was bit by this yesterday morning.  You can boot if you edit /etc/X11/xorg.conf and change Driver "nvidia" to Driver "nv"  You'll be using the broken open source driver, but it'll work well enough to make the fix work: [http://www.ubuntuforums.org/showthread.php?t=257459](http://www.ubuntuforums.org/showthread.php?t=257459)

I'd do "sudo -i" and give the commands described in the fix using this root shell and then undo your xorg.conf edit before rebooting.

worked for me.

You can edit the xorg.conf file from the text mode shell with:
sudo nano -W /etc/X11/xorg.conf

HTH,
--wally.

---

### Post by godefroy on 2006-09-15
> **wkulecz said:**
> I was bit by this yesterday morning.  You can boot if you edit /etc/X11/xorg.conf and change Driver "nvidia" to Driver "nv"  You'll be using the broken open source driver, but it'll work well enough to make the fix work: [http://www.ubuntuforums.org/showthread.php?t=257459](http://www.ubuntuforums.org/showthread.php?t=257459)

I'd do "sudo -i" and give the commands described in the fix using this root shell and then undo your xorg.conf edit before rebooting.

worked for me.

You can edit the xorg.conf file from the text mode shell with:
sudo nano -W /etc/X11/xorg.conf

HTH,
--wally.

that´s what i did.works for now but the fix that was uploaded (also yesterday) also doesn´t work :( !
Any ideas of when will this issue be solved?

---

