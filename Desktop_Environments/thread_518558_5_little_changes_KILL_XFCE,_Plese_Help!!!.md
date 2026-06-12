---
title: "5 little changes KILL XFCE, Plese Help!!!"
date: 2007-08-06
forum: Desktop Environments
---

### Post by ela04cz on 2007-08-06
In order to run Beryl smoothly, I followed an instruction on a website, and make changes to 5 system files, they are:

1. /etc/modprobe.d/aliases 
 alias net-pf-10 ipv6    was changed to    alisas net-pf-10 off #ipv6

2. /etc/init.d/rc
CONCURRENCY=none   was changed to   CONCURRENCY=shell

3. /etc/hosts
127.0.0.1 localhost.localdomain myhost
127.0.1.1 myhost 
was changed to
127.0.0.1 localhost myhost
127.0.1.1 myhost

4. I run this: sudo sysctl vm.swappiness=10
and  edited /etc/sysctl.conf ( I add this line: vm.swappiness=10 to the file )

5. /boot/grub/menu.lst
I placed "profile" at every lines end which starting with strings including "kerne .../vlminuz"

RESULT: turn on the xubuntu 7.04, usual mode, after the xubuntu logo it shows /etc/init.d/rc: 2: startup: not found    on a black screen for about 20 times, then stuck, do nothing. I typed    login myhost  and    myhost  login   it does nothng. need to force to shut it down.

turn on he recovery mode, it shows the same thing, only with one more line at the end       root@(none):~#      which use to be     root@ela04cz:~#     before.   

I use     sudo nano  /etc/init.d/rc   and access this problematic file, and modify it back to what it looked like before, but canno save it! It says Read only file system... I think this is the biggest problem now, I do not have the permission to change the system files back! Can some one tell me how to get the permission?

I tried to login with my uername, and I got this: -bash:  /dev/null:  Permission denied.

Guys please give me some suggestions, I appreciate everything you say!

---

### Post by aidanr on 2007-08-06
don't know which one (if any) is causing the problem, but i'd start with 3 and 5
boot a live cd, mount the partition and revert the changes you made

edit:// duh, just re-read it, the error is about /etc/init.d/rc and you made a change to that, so change that back

---

### Post by ela04cz on 2007-08-06
Well, the problem is my optical drive is not working, so I cannot use the live CD to boot it now (plus I don't have it).

Can you clarify your last sentence for me? How can I re-read it? Yes I know the init.d is the problem and how can I change it back?

---

### Post by aidanr on 2007-08-06
> edit:// duh, [SIZE="4"]**i**[/SIZE] just re-read it,
that's what i meant

do you dual boot? or have any other os on there that you could fix it from, or maybe does your motherboard support booting from usb, maybe boot a distro off a usb key

that's all the ideas i have, gl

---

### Post by ela04cz on 2007-08-06
Oh, I see, thanks for clarifing. I do have a dual boot XP system here, but the strange thing is I can see the XP partition from Ubuntu, while cannot see ubuntu partition within XP, someone told me there is a way to do this, can you tell me how?

---

### Post by ela04cz on 2007-08-06
I installed a script and now I can access ubuntu file system from XP. But after I change everything back, it still cannot be turned on. It says  exec:7: /etc/init.d/rc not found! But while I am in windows, I can see this file and I changed it back to what it was before, how can ubuntu says it cannot find it?

---

### Post by aidanr on 2007-08-06
sorry should have mentioned [http://www.fs-driver.org/](http://www.fs-driver.org/) for windows, but you figured that out anyway

not sure what to do about that error, possibly check the permissions of the file
```
ls -l /etc/init.d/rc
-rwxr-xr-x 1 root root 8187 2007-04-22 21:19 /etc/init.d/rc

```
though i'm not sure how to do this from windows
also if you edited it with gedit originally, gedit will have made a backup of it called rc~
so you could delete rc and rename rc~ to rc

---

