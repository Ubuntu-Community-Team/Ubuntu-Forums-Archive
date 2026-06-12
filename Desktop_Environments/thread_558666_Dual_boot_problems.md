---
title: "Dual boot problems"
date: 2007-09-24
forum: Desktop Environments
---

### Post by digital_exhaust on 2007-09-24
I have no idea what I did wrong here, but I seem to have killed my bootloader. 

Decided I wanted to give Fedora a shot, so I used GParted to make a 40g partition behind my Ubuntu install....installed Fedora there and re-booted...... 

The only boot options I am given are Fedora 7 and "other". When I select other, I am greeted with an unresponsive black screen and the only text is the word "chainloader" 

What do I need to do to repair my bootloader? Any help here would be great....

---

### Post by be4truth on 2007-09-24
I assume you can boot into Fedora, right?
If so go there and open a terminal/shell
Then type 

```
sudo fdisk -l 
```
and post the output here.Try to identify which partition is what like /dev/sda1 is XP /dev/sda3 is Ubuntu ect.

---

### Post by digital_exhaust on 2007-09-24
Thanks for the reply... I got it... I just installed Ubuntu over the Fedora install, grub loads fine now and I am able to boot into my original Ubuntu install normally... 

Thanks again..

---

