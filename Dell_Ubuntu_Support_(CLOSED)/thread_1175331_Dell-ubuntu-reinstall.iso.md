---
title: "Dell-ubuntu-reinstall.iso"
date: 2009-06-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ezhu_77 on 2009-06-01
Hi Friends,
I s it possible to do a fresh install on dell pc using this ubuntu-dell-reinstall ISO image. If not please tell me how to use the image.

Thanks

---

### Post by pastalavista on 2009-06-01
I believe it probably is possible. You'd need to burn the iso to a CD, or use USB-creator to burn it to a USB flash drive, and then boot from it.

---

### Post by ezhu_77 on 2009-06-01
Hi,
But if i choose from the install menu, reinstall system option it loads the image and stops prompting

(initparams)#
please enter help for help message...

How can i proceed with this....
help me pls...

---

### Post by apparle on 2009-06-01
> **ezhu_77 said:**
> Hi,
But if i choose from the install menu, reinstall system option it loads the image and stops prompting

(initparams)#
please enter help for help message...

How can i proceed with this....
help me pls...

I am not sure but maybe this will work.
After you get the above message wait for a minute and then 
```
exit
```

---

### Post by ezhu_77 on 2009-06-01
If I give exit, the system restarts.... To use dell-reinstall dvd whether the system should be ubuntu installed prior..

---

### Post by pastalavista on 2009-06-01
> **ezhu_77 said:**
> Hi,
But if i choose from the install menu, reinstall system option it loads the image and stops prompting

(initparams)#
please enter help for help message...

How can i proceed with this....
help me pls...

Did you try entering "help"? It did ask nicely.. even said "please"

---

### Post by ezhu_77 on 2009-06-02
Hi,
If i enter help, it shows as

code:

#help


Built-in commands:
_ _ _ _ _ _ _ _ _ _  

. : [ [[ alias break cd chdir command continue echo eval exec 
exit export false getopts hash help let local pwd read readonly
return set shift source test times trap true type ulimit umask
unalias unset wait [ [[ ash awk basename cat chmod chroot chvt
clear cmp cp cut deallocvt dumpkmap echo egrep env expr false
fbset fdflush fgrep find grep hostname ifconfig ip kill ln loadfont
loadkmap ls mkdir mkfifo mknod mkswap mktemp more mount mv openvt
pidof printf ps pwd readlink reset rm rmdir sed setkeycodes sh
sleep sort stat stty sync tail tee test touch tr true tty umount
uname uniq wget yes


How can i proceed.....

---

### Post by ezhu_77 on 2009-06-02
Hi
These are the options available if i boot using dell-reinstall dvd...

dell automatic reinstall
dell interactive reinstall
try ubuntu without any changes

I am using dell optiplex 320 machine...
If I choose any of the above method for install, i am getting the below message

[code=apparle;7381103]
[3.928019] ata1: softreset failed (device not ready)
[4.592010] ata2: softreset failed (device not ready)
Modprobe: FATAL : Could not load /lib/modules/2.6.28-11-generic/modules.dep :No such file or directory

Loading please wait.....

BusyBox  v.1.0.2 (Ubuntu 1:1.10.2-2Ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands

(initramfs)

(initramfs) help
Built-in commands:
- - - - - - - - - - - - - 

. : [ [[ alias break cd chdir command continue echo eval exec 
exit export false getopts hash help let local pwd read readonly
return set shift source test times trap true type ulimit umask
unalias unset wait [ [[ ash awk basename cat chmod chroot chvt
clear cmp cp cut deallocvt dumpkmap echo egrep env expr false
fbset fdflush fgrep find grep hostname ifconfig ip kill ln loadfont
loadkmap ls mkdir mkfifo mknod mkswap mktemp more mount mv openvt
pidof printf ps pwd readlink reset rm rmdir sed setkeycodes sh
sleep sort stat stty sync tail tee test touch tr true tty umount
uname uniq wget yes

(initramfs) exit

cp: cannot create '/root/var/log/' : No such file (or) directory
mount: mounting /dev on /root/dev failed: No such file (or) directory
mount: mounting /sys on /root/sys failed: No such file (or) directory
mount: mounting /proc on /root/proc failed: No such file (or) directory
Target filesystem doesnot have /sbin/init
No init found. Try passing init= bootarg
```
exit
```

---

### Post by andybleaden on 2009-06-02
This sounds exactly like the error message I get from running the Hardy live cd.

Although I get initramfs error instead 

I get this occasionally and had to put jaunty on instead of hardy. It seems to be something to do with busybox

---

