---
title: "Windows 7 sets it's own partition active, messes up grub's boot."
date: 2010-02-20
forum: Desktop Environments
---

### Post by Andre-D on 2010-02-20
I had an empty Partition 1
Partition 2 was ubuntu, mounted as "/" (part 2 was active)

I installed win7 to Partition 1 - as usual,the arrogance of M$ make it boot from partition 1, ignoring any existing OS.

I marked partition 2 as active, and again, Grub works, and I can select os.

the problem is, that if I wish to boot to the pile of bloat'n'bugs called win7 - it sets it's own partition active !

how can I disable this extremely rude, crappy, ignorant OS from doing so ?

---

### Post by Markus72 on 2010-02-20
Hi,

try variant 2 from [here]("http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7").

Worked for me

Markus

---

### Post by Andre-D on 2010-02-20
please observe that I do not need to restore grub, as it's untouched iono partition 2 , just make the windows stop setting partition 1 as active.

---

### Post by meierfra. on 2010-02-20
> just make the windows stop setting partition 1 as active. 

I would  guess it's Grub who makes the partition active. So try this:


```
gksudo gedit /boot/grub/menu.lst
```

Remove  "makeactive"  from your Windows item

---

### Post by Andre-D on 2010-02-20
wow , thnx, I did the change, will try next time I need to boot to windows.
-why would Grub do that ? - I've never seen this, and I've dual-booted before using grub - and never experienced this.

makeactive, if that means "make that partition active" - is a one-way road..

---

### Post by meierfra. on 2010-02-20
> -why would Grub do that ? 
I think its  due to the myth that Windows needs to boot flag to be able to boot.


> makeactive, if that means "make that partition active" 
It does.


> I've never seen this, and I've dual-booted before using grub 
It only matters if Grub is not installed in the MBR.  




> how can I disable this extremely rude, crappy, ignorant OS from doing so 
You owe Window 7 a public apology;)

---

### Post by Andre-D on 2010-02-20
I see, that may be the MBR stuff.

I hereby apologise for assuming win7 was as nasty as I did, sorry.

This was based by 23year long IT career as senior administrator and security consultant, where only the 2 last years I've been using Linux only, except for a virtual windows when needed, so I've seen so much bad microsoft stuff that I am generally negative towards their products, sometimes without good reason.

:)

---

