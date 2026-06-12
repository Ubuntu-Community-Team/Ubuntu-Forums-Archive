---
title: "[SOLVED] scim-bridge can't start"
date: 2008-02-23
forum: Desktop Environments
---

### Post by wangrui on 2008-02-23
Hi,

I recently moved my root partition to a USB flash disk. After that scim can't start, and make every other application who accpet input stop working.
After doing some search, I know  that it's because some file permission is not correct. So I wrote a java program, compare every file's permission with corresponding file on another ubuntu disk from top down. And found some file is missing the setuid and setgid permission. After I modified all that files. The system start and works perfectly.

Then after some time, the same problem appears again. The scim-bridge can't start. So every application can't work because they link to scim. I have to use
```
im-switch -s none
```
to stop scim.

The root partition on a flash disk is mounted readonly. I use unionfs to redirect all modification of the 15 root directories to a ext3 partition on one of my hard disk. I'm sure the problem is caused by unionfs which messed the permission up. There should be two options for me to make it work:

[LIST=1]
[*]format the hard disk which accept all file modifications
If I remove the rw partition, my system will revert back and the problem will disappear. But there are too much changes since I made the flash. I don't want to abandon them.
[*]Compare the directory tree again
If I compare the directory tree again,  I will know what's the problem. But the problem is I left the compare code on one of my notebook which I left in another place. The notebook is not online so I can't access the code. I really shouldn't put anything on a notebook. And I don't want to write the code again. 
[/LIST]

Besides this, I really want to know the root cause of this problem. There might be some other services can't start because the permission problem.

For scim-bridge, if I started in the gnome terminal, I will receive the following error:
```
scim-bridge -v
Pinging for the another agent process...
It seems like there is no other agent for the old socket.
Cannot bind the socket: Operation not permitted
Finalizing scim...
Finalize, done
Failed to allocate the agent. Exitting...

```

Does anyone knows why scim-bridge don't have permission to bind the socket? Thanks in advance

---

### Post by wangrui on 2008-02-23
I tried it again with sudo, it works. It definite permission problem. But which file is missing the setuid permission. Can anyone help?

```
sudo scim-bridge -v
Pinging for the another agent process...
It seems like there is no other agent for the old socket.
Initializing scim...
There is no socket frontend at all.
Launching a SCIM daemon with Socket FrontEnd...
Loading simple Config module ...
Creating backend ...
Loading socket FrontEnd module ...
Starting SCIM as daemon ...
Initialize scim, done!
Loading configurations...
slot_reload_config ()
launch_panel ()
Launch "/usr/lib/scim-1.0/scim-panel-gtk"
ScimBridgeAgent is now ready
launch ()
Daemonizing...
```

---

### Post by wangrui on 2008-03-04
It's not permission problem. It seems scim don't works on unionfs. I have installed a 64bit ubuntu, everything works fine until I move the root partition to a flash disk. This time scim print the following error:

```
Mar  4 20:42:47 wangrui-desktop kernel: [  465.435219] scim-launcher[6554]: segfault at 00002ad5cb99caec rip 00002ad5cb99caec rsp 00007fffe0fdf588 error 14
```

Moving the root partition to a flash disk is really so great. I just bought some internel connectors so that I can put the usb disk into the box. But there are also something can't work out. It seems scim and javah will print very weird message if running on a unionfs. I don't really know why, are they trying to read from physical disk directly?

---

### Post by wangrui on 2008-03-08
After so many so many tries, I finally work it out.

The problem is we can't mount unionfs at /tmp,  After I mount /tmp as tmpfs. Everything works like a charm.

Finally every application is working on the Flash+Memory system. I guess I will enjoy it for a very long time.

---

