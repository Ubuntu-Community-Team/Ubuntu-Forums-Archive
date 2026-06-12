---
title: "install a cache flusher"
date: 2011-05-28
forum: Desktop Environments
---

### Post by boblizar on 2011-05-28
if you have not noticed, this is my ubuntu master thesis....
[http://ubuntuforums.org/showthread.php?t=1836890](http://ubuntuforums.org/showthread.php?t=1836890)
check it out and share it with your friends =)

if you would like to clear your disk cache from info, open a terminal then run.

```
sudo su
```

&& once root drop this script.

```

cat > /usr/sbin/flushcache << "EOF"
#!/bin/bash
sync; echo 3 > /proc/sys/vm/drop_caches
EOF
chmod 550 /usr/sbin/flushcache
exit

```

then hit enter to exit out of root mode.

now you have a command and as a user you can type "sudo flushcache" to get your cache flushed out

now for swap flusher

enter root, drop script

```
sudo su
```

```

cat > /usr/sbin/flushswap << "EOF"
#!/bin/bash
swapoff -a && swapon -a
EOF
chmod 550 /usr/sbin/flushswap
exit

```

2 commands installed /usr/sbin/flushcache && /usr/sbin/flushswap

to use this

alt + f2

then run

```

gksu flushcache

```

to flush the cache

or

alt + f2

then run

```

gksu flushswap

```

my system never uses swap so that solution is not tested, but it should work.
[IMG]http://img651.imageshack.us/img651/2277/flushcache1.jpg[/IMG]
[IMG]http://img822.imageshack.us/img822/4626/flushcache2.jpg[/IMG]

---

### Post by karmila on 2011-05-28
Hi,

Can you explain how this works?

---

### Post by boblizar on 2011-06-11
you type "sudo flushcache" and then it clears your disk cache out...  ill post a swap flusher also if i do not have one up.



"mkultra [ ~ ]$ sudo su
[sudo] password for mkultra: 
root [ /home/mkultra ]# cat > /usr/sbin/flushcache << "EOF"
> #!/bin/bash
> sync; echo 3 > /proc/sys/vm/drop_caches
> EOF
root [ /home/mkultra ]# chmod 550 /usr/sbin/flushcache
root [ /home/mkultra ]# exit
exit
mkultra [ ~ ]$ sudo flushcache
"

and my disk cache goes to zero....

it writes a simple script, and the script information was gathered from net and condensed.... use gnome system monitor, you will see disk cache going crazy in ram.  you can flush out the old cached information if your no longer using it.

full on maden commentary of the cache flusher

cat > /usr/sbin/flushcache << "EOF"
write to the file /usr/sbin/flushcache << UNTIL EOF denotes the END OF FILE
#!/bin/bash
call the bash interpreter since we write sexy bash scripts to think for us so we dont have to

sync; echo 3 > /proc/sys/vm/drop_caches
sexy command that i googled up to flush cache ;-)

EOF
end of file QUIT WRITING TO THE FILE /usr/sbin/flushcache

chmod 550 /usr/sbin/flushcache
change the permissions of the file to make it readable and executable to the owner and group (root, root since we used sudo su to build this command)

exit
leave root, quit playing in root!!!

---

### Post by boblizar on 2011-06-16
just used it.... alt + f2 (loads dialog to run commands)

gksu flushcache

---

### Post by masuch on 2011-11-08
Wow, thanks a lot for flushcashe script !!!

I am using it to tune my huge grub2 grub_config.cfg using virtualbox. I had a problem because after virtual reboot, it remembered my grub files in memory and did not use any my changes in grub config. Now, it is just run this script and any changes within virtual boot process appears in grub menu immediately.

I have been using before:
sudo sync && sudo sysctl -w vm.drop_caches=3 && sudo sysctl -w vm.drop_caches=0
but it was not reliable.

:-)

---

