---
title: "What exactly are the other disks on debian used for?"
date: 2008-04-06
forum: Debian
---

### Post by whitefang5412 on 2008-04-06
As the thread title says. I am downloading debian and only downloaded the first disk. What do the other disks have to offer? I know in Pc-BSD you need other disks for the web browser etc...is debian the same way?

---

### Post by jdhore on 2008-04-06
> **whitefang5412 said:**
> As the thread title says. I am downloading debian and only downloaded the first disk. What do the other disks have to offer? I know in Pc-BSD you need other disks for the web browser etc...is debian the same way?

The other disks offer basically the entire Debian repos...For a standard GNOME system with all of GNOME and iceweasel, etc, all you need is the first disk...I do netinstall though :)

---

### Post by whitefang5412 on 2008-04-06
I really like debian, but I have no instant messanging client like Pidgin. Where can I get pidgin, do I have to download another disk?

---

### Post by jdhore on 2008-04-06
> **whitefang5412 said:**
> I really like debian, but I have no instant messanging client like Pidgin. Where can I get pidgin, do I have to download another disk?

umm...the repos? apt-get install pidgin

---

### Post by whitefang5412 on 2008-04-06
> **jdhore said:**
> umm...the repos? apt-get install pidgin

Never worked. Typed in my pass word and it didn't work. Hm. I typed the password in right.

---

### Post by jdhore on 2008-04-06
> **whitefang5412 said:**
> Never worked. Typed in my pass word and it didn't work. Hm. I typed the password in right.

Debian doesn't use sudo for default...Use su and THEN run the apt-get command...or go to Applications-Accessories-Root Terminal and run the apt-get command

---

### Post by whitefang5412 on 2008-04-06
> **jdhore said:**
> Debian doesn't use sudo for default...Use su and THEN run the apt-get command...or go to Applications-Accessories-Root Terminal and run the apt-get command

Still won't let me.

EDIT: To install kopete I even need another disk.

---

### Post by jdhore on 2008-04-06
> **whitefang5412 said:**
> Still won't let me.

EDIT: To install kopete I even need another disk.

no you don't...I've never used the non-netinstall (well...i have a long time ago)...you may have to uncomment the web repos from your sources.list or something like that...or just say: "Screw it" and download and install from the netinstall CD

---

### Post by whitefang5412 on 2008-04-06
> **jdhore said:**
> no you don't...I've never used the non-netinstall (well...i have a long time ago)...you may have to uncomment the web repos from your sources.list or something like that...or just say: "Screw it" and download and install from the netinstall CD

Meh, or go back to mint. I thought I'd like debian but...

---

### Post by jdhore on 2008-04-06
> **whitefang5412 said:**
> Meh, or go back to mint. I thought I'd like debian but...

If you did it correctly, you would've...Debian is quite a bit more work than Mint, but the advantages are worth it...Using the netinstall disk is basically the only good way to go on Debian...Any Debian developer/user will tell you the ONLY reason you shouldn't use the netinstall CD is if your NIC doesn't work out-of-the-box...That's IT.

---

### Post by ntowakbh on 2008-04-07
I see in your signature that you have Debian Etch listed.  Last I used etch, it didn't have pidgin in the repos yet, still gaim.  Testing (lenny) does though.

---

### Post by jdhore on 2008-04-07
> **ntowakbh said:**
> I see in your signature that you have Debian Etch listed.  Last I used etch, it didn't have pidgin in the repos yet, still gaim.  Testing (lenny) does though.

yep, i got him all fixed up :)

---

