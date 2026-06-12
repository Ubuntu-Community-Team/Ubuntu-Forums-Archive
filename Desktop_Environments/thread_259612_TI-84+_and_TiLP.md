---
title: "TI-84+ and TiLP"
date: 2006-09-17
forum: Desktop Environments
---

### Post by 0kehk0dr on 2006-09-17
I'm taking computer networking this year in school, and our teacher talks on and on about nothing of any importance for 42 minutes. So, in an effort to keep myself sane, I wish to install some games on my TI-84+ and maybe make my own. The problem is that TiLP can't find my calculator ](*,)

I'm using a TI-84+ connected with SilverLink (USB). 

Here's what TiLP outputs:
```
Bticables: getting method from resources (automatic):
ticables:   check for tiusb usability:
ticables:     using devfs: no
ticables:     node /dev/tiusb0: exists
ticables:     permissions/user/group: -rw-rw-rw- root root
ticables:     is user can r/w on device: yes
ticables:     module: not loaded
ticables:     => check the module exists (either as module, either as built-in)
ticables:     => add an entry into your modutils file to automatically load it
ticables:   warning: can't use IO_TIUSB
ticables:   check for lib-usb usability:
ticables:     usb filesystem (/proc/bus/usb): mounted
ticables:     node /proc/bus/usb/devices: exists
ticables:     permissions/user/group: -r--r--r-- root root
ticables:     is user can r/w on device: yes
ticables: mapping I/O...
ticables: registering cable...
ticables: list of settings:
ticables:   cable: SilverLink
ticables:   port: USB port #1
ticables:   method: user mode (ioctl)
ticables:   device name: /dev/tiusb0
ticables:   delay value: 10
tifiles : settings:
tifiles :   calc type: TI84+
ticalcs : settings:
ticalcs :   calc type: TI84+
```

I tried
```
mknod /dev/tiusb0 c 115 16 && chmod 666 /dev/tiusb0
```
but to no avail.

Any suggestions?

---

### Post by PWill on 2006-10-10
I have this same issue. Did you ever solve this problem?

---

### Post by Black Sliver on 2007-12-11
Hi there!

I have the same / a similar problem :( 
Solved it once with ```
sudo mknod /dev/tiusb0 c 115 16 && sudo chmod 666 /dev/tiusb0
``` and then ```
gksu tilp
``` Inside the app rightclick onto the calc side and select "select device", now setup your device and click ok.
I had file access (Dirlist) once, next time I tried it, there was no way to get it to work anymore -.- 

Im using TiLP2 installed through ubuntu repos on gusty. TI Voyage 200, Silver Link.

Anyone got the silver link to work? I really need it for school and i dont want to boot to windows just for file access on my ti :( 


[i]so long..
Andy[/i]

---

### Post by Black Sliver on 2007-12-11
Finally - the solution
I've installed the (latest?) packages from [http://repo.calcforge.org/debian/](http://repo.calcforge.org/debian/) and it seems to work now :)

---

### Post by Dekadence on 2007-12-14
Hmm.... all of the packages? or just some? I still can't connect :| I even can't right click on calculator side!

EDIT: Ok, got it working :) uninstalled all of the old packages and installed all the new ones ;) thanks Black Sliver

---

### Post by Black Sliver on 2007-12-19
np ;) 

Short manual:
1. uninstall the ti packages from the ubuntu repos
2. download the tilp2_X.XX package from [http://repo.calcforge.org/debian/](http://repo.calcforge.org/debian/)
3. satisfy the dependencies by installing other packages from the same site (see the dependency information of each package)
4. install the tilp2 package

You can also try to add it as a repo to your sources.list. Anyway, i wont do this because its a debian repo and not made for ubuntu.

---

