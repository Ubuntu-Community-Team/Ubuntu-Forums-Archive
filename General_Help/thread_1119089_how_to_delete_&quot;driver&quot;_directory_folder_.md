---
title: "how to delete &quot;driver&quot; directory folder at desktop"
date: 2009-04-07
forum: General Help
---

### Post by Zireth ZH on 2009-04-07
I was following the steps from this url: [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

Following the second method to manually install my ATI driver at step 2:

"2. Download the latest Catalyst package.

Download page: Catalyst 9.3. This package contains both the 32-bit and 64-bit driver.

Open a terminal window and switch to the directory you downloaded the installer to.
For example:

cd Desktop"

I opened the terminal and typed cd Desktop.... my drivers were there...

I followed all the steps and got stucked at step 5... there were errors and i didnt know what to do.
I decided to jump to "FInishing installation" step and verified that my drivers for HD 3850 were there.  So I thought that everything was fine and minimized all the windows that were opened. I found that there were bunch of ".deb" packages or whatever and a "driver" folder with a lock on its icon.

I restarted my PC and then attemptted to delete all those files on my desktop. I could delete all of them but couldnt delete "driver" folder. It says "Permission denied" cuz its a directory folder or something like that.

I tried sudo -i to go as root and tried sudo rm -R .. all sudos commands that i could find but nothing worked.. 

These are some of the things that I did and appeared at the terminal showing me "no such file or directory" bla bla bla : 

"zireth@zireth-desktop:~$ sudo -i
root@zireth-desktop:~# sudo rm -r kl
rm: cannot remove `kl': No such file or directory
root@zireth-desktop:~# sudo rm -R kl
rm: cannot remove `kl': No such file or directory
root@zireth-desktop:~# 
root@zireth-desktop:~# sudo rm -R durver
rm: cannot remove `durver': No such file or directory
root@zireth-desktop:~# sudo rm -R driver
rm: cannot remove `driver': No such file or directory
root@zireth-desktop:~# sudo rmdir -r driver
rmdir: invalid option -- r
Try `rmdir --help' for more information.
root@zireth-desktop:~# sudo unlink/home/Desktop/driver
sudo: unlink/home/Desktop/driver: command not found
root@zireth-desktop:~# sudo rm -rf/home/zireth/Desktop/driver
rm: invalid option -- /
Try `rm --help' for more information.
root@zireth-desktop:~# ls -l /home/user/Desktop
ls: cannot access /home/user/Desktop: No such file or directory
root@zireth-desktop:~# ls -l /driver/user/Desktop
ls: cannot access /driver/user/Desktop: No such file or directory
root@zireth-desktop:~# ls -l /home/user/Desktop/driver
ls: cannot access /home/user/Desktop/driver: No such file or directory"

Please someone help me get rid of this... I uninstalled the ATI catalyst drivers 9.3 already ... i decided to use envy ng to go back with my 8.6 drivers .. I got tired of trying to install these drivers.
I decided to use windows for games when i need to...

I just want my ubuntu's desktop clean without that folder in there... 

Thanks

---

### Post by mhgsys on 2009-04-07
you could use 
```
sudo rm -rf /home/username/Desktop/name of the driver.

``` in a terminal.
but be carefull with this command, if you use it on the wrong map or path, everything in that map or path will be deleted.

a safer way is to 
```

 gksudo nautilus

```

---

### Post by Zireth ZH on 2009-04-07
> **mhgsys said:**
> you could use 
```
sudo rm -rf /home/username/Desktop/name of the driver.

``` in a terminal.
but be carefull with this command, if you use it on the wrong map or path, everything in that map or path will be deleted.

a safer way is to 
```

 gksudo nautilus

```

This is what happened:

"zireth@zireth-desktop:~$ sudo -i
[sudo] password for zireth: 
root@zireth-desktop:~# gksudo nautilus
Initializing nautilus-share extension
seahorse nautilus module initialized
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


** (nautilus:6263): WARNING **: Unable to add monitor: Operation not supported
seahorse nautilus module shutdown
root@zireth-desktop:~# sudo rm -rf/home/zireth/Desktop/driver
rm: invalid option -- /
Try `rm --help' for more information.
root@zireth-desktop:~# "

I  used nautilus but couldnt find that folder at Desktop.... so i closed it and used the sudo rm -rf command .. but it says "rm: invalid option -- /"

Now what do I do?
THanks

---

### Post by mhgsys on 2009-04-07
You need to put a space in between.
So
sudo rm -rf/home/zireth/Desktop/driver

becomes```


sudo rm -rf /home/zireth/Desktop/driver

```

anyway, remember that "driver" is replaced by the name of the map.
So if the map is called driver it's gonna be ok, if the map is called 
Blabla or something, it's gonna be sudo rm -rf /home/zireth/Desktop/Blabla

---

### Post by Zireth ZH on 2009-04-07
> **mhgsys said:**
> You need to put a space in between.
So
sudo rm -rf/home/zireth/Desktop/driver

becomes```


sudo rm -rf /home/zireth/Desktop/driver

```

anyway, remember that "driver" is replaced by the name of the map.
So if the map is called driver it's gonna be ok, if the map is called 
Blabla or something, it's gonna be sudo rm -rf /home/zireth/Desktop/Blabla

I copied that and pasted it on terminal.. and finally got rid of it... I thank you so much ... thanks thanks thanks!

---

### Post by mhgsys on 2009-04-07
your welcome. 

enjoy learning ubuntu

---

