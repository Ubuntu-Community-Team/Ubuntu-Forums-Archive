---
title: "System freezes occasionally"
date: 2009-06-18
forum: General Help
---

### Post by jis on 2009-06-18
Nothing moves in screen then. I can't get to console by e.g. Ctrl-Alt-F1 then. I have to reboot by  Alt-SysRq-s, Alt-SysRg-u, Alt-SysRq-b. Then some config files are corrupted preventing some applications to start. I use jaunty, encrypted ext4 /home (by ecryptfs). jaunty-proposed and jaunty-backports software sources enabled, system updated.

---

### Post by abyrne on 2009-06-18
I've had this problem before. When this happens, can you use Ctrl-Alt-Backspace? (This command is disabled in Jaunty by default. Run this to enable it:
```
sudo apt-get install dontzap
sudo dontzap -d
```
Tell me if this fixes it)

---

### Post by jis on 2009-06-19
Unfortunately Ctrl-Alt-Backspace does not work in such cases even if DontZap is set to false.

---

### Post by kerry_s on 2009-06-19
ext4 is unstable alone, throw in encryption, ouch.
are you running any effects?

---

### Post by jis on 2009-06-19
effects?

---

### Post by kerry_s on 2009-06-19
> **jis said:**
> effects?

yeah, composite?

---

### Post by idef1x on 2009-06-19
I also had freezes when on ext4, but since upgrading the kernel to 2.6.30 I don't have them anymore (and hope it stays like that ;) )

---

### Post by jis on 2009-06-19
No, composite is not in use.

---

### Post by jis on 2009-06-19
> **idef1x said:**
> I also had freezes when on ext4, but since upgrading the kernel to 2.6.30 I don't have them anymore (and hope it stays like that ;) )

I don't see that in repositories. I guess I had better return to using ext3.

---

### Post by DeMus on 2009-06-19
> **idef1x said:**
> I also had freezes when on ext4, but since upgrading the kernel to 2.6.30 I don't have them anymore (and hope it stays like that ;) )

Where did you get this new kernel and how did you install it?
Does it make me loose my video driver or will it be included into this new kernel?

---

### Post by idef1x on 2009-06-19
I had to compile it myself (including makeing the kernel package to install with dpkg) cause it's not in the repository. Maybe ubuntu will backport it in their jaunty repos later, but couldn't find info about that. In the new release karmic they allready use the 2.6.30 kernel. 
Anyway i didn't want to wait for or the backport or until the karmic release is out in the open and ext4 definitely gave my system a performance boost. Besides that with kernel 2.6.30 your system boots faster :)

---

