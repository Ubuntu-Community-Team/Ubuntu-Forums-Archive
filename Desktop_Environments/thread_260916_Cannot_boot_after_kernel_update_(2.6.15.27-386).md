---
title: "Cannot boot after kernel update (2.6.15.27-386)"
date: 2006-09-19
forum: Desktop Environments
---

### Post by lorre on 2006-09-19
I just updated my system and after restarting it did not boot anymore..

At the point where normaly the login screen pops up, it now remains black.

When booting in recovery mode it stops after the following message:

```
select() to /dev/rtc to wait for clock tick times out.
```

After that I get a prompt but cannot do much. Booting (using Grub) with the previous version (2.6.15.26-386) works fine.

What's wrong?

---

### Post by tagra123 on 2006-09-19
Don't know whats wrong but load up the previous version using grub and try the update again. Maybe something didn't get written to disk before the restart???

---

### Post by lorre on 2006-09-20
>> Maybe something didn't get written to disk before the restart???

This might be the case, since it did not restart correctly after upgrading. How do I reinstall the update? If I boot with 2.6.15.26-386 and type 
```
apt-get dist-upgrade
```
I don't get the kernel upgrade.

---

### Post by nullmind on 2006-09-20
Can you boot into recovery mode into a terminal? Do you really need the 386 kernel? Maybe this could fix things easier and make it run better:

```

sudo -s
apt-get update
apt-get install linux-686

```

---

### Post by tagra123 on 2006-09-20
To get the distribution upgrade, from a terminal:

```
sudo apt-get updates
sudo apt-get dist-upgrade
```

TO CHANGE KERNELS

For the 386 kernel the line below will install the most recent kernel.

```
sudo apt-get install linux-386
```


For the 686 kernel the line below will install the most recent kernel.

```
sudo apt-get install linux-686

```
For the AMD kernel the line below will install the most recent kernel.

```
sudo apt-get install linux-k7

```

There are also other kernels for dual core, etc...
Here's a good link about the kernels:

[http://ubuntuforums.org/showthread.php?t=85917](http://ubuntuforums.org/showthread.php?t=85917)

---

### Post by lorre on 2006-09-20
If i type ```
sudo apt-get install linux-386
``` I get ```
Reading package lists... Done
Building dependency tree... Done
linux-386 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up flashplugin-nonfree (7.0.68~ubuntu1~dapper1) ...
Downloading...  done.
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
                -n: not really
                -f: force
dpkg: error processing flashplugin-nonfree (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
I only get the flashplugin update (which fails, but that's another problem).

This is after booting with the ...-26-386 kernel; uname -a gives:```
Linux anton-desktop 2.6.15-26-386 #1 PREEMPT Fri Sep 8 19:55:17 UTC 2006 i686 GNU/Linux

``` 

Back to my guestion; how can I re-install the ..-27-386 kernel?

---

### Post by lorre on 2006-09-20
After reading more about the kernels (thanks for the link ;))I decided to install the 686 kernel which it is downloading now so that might fix my problem. Thanks guys.

---

### Post by lorre on 2006-09-20
Hmm, not quite there yet; booting the -27-686 kernel still gives me no login screen. If I boot it in recovery mode it now boots normal. Could the kernel upgrade have broken my ati drivers somehow?

---

### Post by Marsup on 2006-09-20
I have the same problem, you can still switch between tty's though (eg ctrl+alt+F5). If I try a startx it says my nvidia drivers can't be found...

---

### Post by tagra123 on 2006-09-20
I do remember reading about the video drivers. You might need to install those too. I guess I missed that.

typing 

startx should help to reveal more problems.

I remember seeing a post about just that here on the forums about a week ago.

---

### Post by garretwp on 2006-09-20
I am running the K7 version of this kernel and when I go to reboot it will just hang! Also I can not get my usb drives to detect with this kernel either. They will not recognize at all. 

- Garrett

---

### Post by lorre on 2006-09-21
Recompiling my ati headers solved my problem. I can finally successfully boot the new kernel. Thnx for the help.

---

### Post by tagra123 on 2006-09-21
Glad to help.

---

