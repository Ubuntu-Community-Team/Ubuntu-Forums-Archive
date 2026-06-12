---
title: "Can i have Vista and ubuntu in my desktop"
date: 2008-08-31
forum: Desktop Environments
---

### Post by manoindia2020 on 2008-08-31
I have installed Vista Ultimate in my pc. But i am interested in working with ubuntu. Can i now install ubuntu and make my pc work with dual OS.
Becoz i heard that vista boot loader dont allow for dual os.
Can some one help me....
In fixing this...

---

### Post by jolx on 2008-08-31
yes u can by using the grub bootloader

---

### Post by henryjm206 on 2008-08-31
hey I'm dual booting ubuntu and vista and it works just fine
I used the ubuntu live CD
Henry

---

### Post by manoindia2020 on 2008-08-31
Now i have working vista in my pc...
if i now insatll ubuntu will it affect vista???

---

### Post by jolx on 2008-08-31
check [this]("http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm") out

ubuntu wont affect vista if u install it correctly. u need to make sure u dont format vista's partition when u install ubuntu

---

### Post by manoindia2020 on 2008-08-31
i dont want to work with live CD ..
I want it to be booted from my hard disk....

---

### Post by henryjm206 on 2008-08-31
no it shoudn't

---

### Post by henryjm206 on 2008-08-31
you can install ubuntu from the live disk just boot up from the live CD and there will be an install icon on the desktop

---

### Post by jolx on 2008-08-31
> **manoindia2020 said:**
> i dont want to work with live CD ..
I want it to be booted from my hard disk....

wat?

before it just magically appears on your hard drive you need to install it. you can install it via the 'live cd' which will give you a graphical way of installing it, or the 'alternate cd' which will give u a framebuffer environment to install it from

---

### Post by pastalavista on 2008-08-31
You can load Ubuntu (live CD) with Windows (Wubi) and it will install like a program without any formatting at all and can be easily uninstalled by Windows at any time. If you decide to dual boot, be sure to shrink your Windows partition first (with the Windows drive management tool) and leave your drive with at least 5 gigs (more is better) of "unallocated space" then Ubuntu will automatically (after you choose "manual" and check the right options) install in a new partition that it creates in that empty space. Good luck. It's really pretty easy.

(make the "mount point" of the new partition "/"... disregard the quotes.. and the parentheses)

---

### Post by Sef on 2008-08-31
If you need to shrink Vista, be sure to use its partitioner to shrink it.

---

### Post by gjoellee on 2008-08-31
if you install virtual box in Windows you can use both systems together (without a virtual machine window!!!)

---

