---
title: "Grub Boots to Error 2; Now booting to Grub Command Line"
date: 2009-05-27
forum: General Help
---

### Post by Ryan Yo on 2009-05-27
I have no idea what triggered this, but all of a sudden, my computer was booting a "Grub Error 2" when I started it up. I did:
```
sudo grub
find /boot/grub/stage1
root (hd0,1) #where I think my Ubuntu install is
setup (hd0)
```
from a Live CD. I think it was this procedure that caused my computer to boot to the Grub command line. I've repeated that procedure (with the Live CD and from the Grub command line) and have yet to make any progress. 

I've also tried to boot to Ubuntu from the Grub command line with:
```
grub> root (hd0,1)
grub> kernel /vmlinuz root=/dev/sda2 ro splash
grub> initrd /initrd.img
grub> boot
```
and that takes me to the 9.04 loading screen with text that says:
"                                                      ok
 Running /scripts/init-premount                        ok
 Mounting root file system...                          
 Running /scripts/local-top                            ok
 Waiting for root file system...                       ok"
and then my 'caps lock' and 'scroll lock' icon start blinking on my laptop and the operation seems to freeze.

I have no idea what to do about this. I've only been able to get this far from searching the forums.

Any ideas out there? Would a reinstall of Ubuntu fix up Grub (I'd rather not if I don't have to)? I'm dual-booting Ubuntu 9.04 with Windows 7.

Thanks in advance,
Ryan

---

### Post by VMC on 2009-05-27
Those "blinking lights" usually mean kernel panic. You don't see that message on the screen?

Also, don't assume. Let "grub> find /boot/grub/stage1" tell you where it is.

---

### Post by Ryan Yo on 2009-05-28
No, I don't see anything on screen saying something about a "kernel panic" - just the message I originally posted.

And also, the "grub> find /boot/grub/stage1" verified that I was working with the right partition.

---

### Post by nebileix on 2009-05-28
Check out here --> [http://www.linuxquestions.org/questions/linux-general-1/grub-error-2-and-possibly-related-problem-352343/]("http://www.linuxquestions.org/questions/linux-general-1/grub-error-2-and-possibly-related-problem-352343/")

---

### Post by Ryan Yo on 2009-06-02
In case anyone else has this problem, I took the easy way out and just reinstalled Ubuntu. Everything is back to normal now.

---

