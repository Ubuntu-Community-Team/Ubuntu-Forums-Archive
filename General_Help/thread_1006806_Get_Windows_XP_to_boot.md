---
title: "Get Windows XP to boot"
date: 2008-12-09
forum: General Help
---

### Post by Beloved Bob on 2008-12-09
I have an older Dell laptop which I had both Win XP and Ubuntu dual booted. Using another computer I now have no need for the dual boot. So, I removed Ubuntu...it is on the other computer...and tried booting XP. Cannot get it to boot. Any suggestions? Thanks.

---

### Post by eBoxNet on 2008-12-09
Did you remove ubuntu partitions?

Try this :

Boot off your Windows XP CD.

   1. Choose “Repair”
   2. When it asks for the installation number, I put in “1&#8243;, and it worked fine (you may want to test this first to be sure.)
   3. Enter Admin password.
   4. At the command prompt type “fixmbr”, then confirm. Windows will overwrite the dual boot info in the MBR that Ubuntu put there.
   5. Reboot!

---

### Post by Beloved Bob on 2008-12-09
When I try doing this I cannot get past step #3...I do not know of an admin password...I did not have one. What do you do if there is no password? Use "Admin"? Or something else?

Thanks for your help.

---

### Post by oilchangeguy on 2008-12-09
> **Beloved Bob said:**
> When I try doing this I cannot get past step #3...I do not know of an admin password...I did not have one. What do you do if there is no password? Use "Admin"? Or something else?

Thanks for your help.

if there is no admin password, just press enter to bypass the prompt. then type fixboot and press enter, then type fixmbr and press enter, then type exit and press enter.

---

### Post by Beloved Bob on 2008-12-09
I tried to bypass the prompt by pressing enter...it did not work. I cannot get past the #3 step...and I have no idea what password it wants. Any ideas?

---

### Post by oilchangeguy on 2008-12-09
> **Beloved Bob said:**
> I tried to bypass the prompt by pressing enter...it did not work. I cannot get past the #3 step...and I have no idea what password it wants. Any ideas?

who ever installed windows on your computer set an admin password during the install. the only other way around it is to reinstall windows.

---

### Post by Beloved Bob on 2008-12-09
Thanks!

---

### Post by caljohnsmith on 2008-12-09
Fortunately, you don't have to use your Windows Install CD to install a Windows MBR--you can use your Ubuntu Live CD instead. How about booting your Live CD, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo lilo -M  /dev/sda mbr
```
Reboot, and you should be all set. If not, let me know what the problem is and we can work from there if you want.

---

### Post by TeXtonyx on 2008-12-10
That is a nice Lilo trick. I think that on the SysRes cd
that there is a utility to reset the Admin Password also.

---

### Post by Beloved Bob on 2008-12-10
> **caljohnsmith said:**
> Fortunately, you don't have to use your Windows Install CD to install a Windows MBR--you can use your Ubuntu Live CD instead. How about booting your Live CD, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo lilo -M  /dev/sda mbr
```
Reboot, and you should be all set. If not, let me know what the problem is and we can work from there if you want.
Hello...and thanks for helping me, again. I followed your suggestion and keeping getting "sudo: lilo: command not found" and I installed lilo, supposedly, but it continues to say "command not found." Any suggestions? Thanks for your help.

---

### Post by caljohnsmith on 2008-12-10
> **Beloved Bob said:**
> Hello...and thanks for helping me, again. I followed your suggestion and keeping getting "sudo: lilo: command not found" and I installed lilo, supposedly, but it continues to say "command not found." Any suggestions? Thanks for your help.
That's really strange, because Lilo is all ready installed on the Ubuntu Live CD; which version of the Live CD did you use? If you type:
```
which lilo
```
Does it return "/sbin/lilo"? If that doesn't work, there's actually a number of ways to install a Windows MBR from the Live CD. You could also do it with this method:
```
sudo apt-get install syslinux
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda
```
If for some reason that doesn't work, please copy/paste your terminal session with the above commands so I can get a better idea of what is going on.

---

