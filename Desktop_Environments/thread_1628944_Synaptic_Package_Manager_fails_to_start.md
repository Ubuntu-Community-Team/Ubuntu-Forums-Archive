---
title: "Synaptic Package Manager fails to start"
date: 2010-11-23
forum: Desktop Environments
---

### Post by Roy M Cooper on 2010-11-23
Hi all
 I have Ubuntu 10.10 AMD64 installed.
When I try to start the Synaptic Package Manager it attempts to start and then quits.
I have tried running it through terminal and get the following output.

roy@Bastard:~$ sudo synaptic
sudo: /etc/sudoers is mode 0640, should be 0440
sudo: no valid sudoers sources found, quitting

I get the same output for sudo apt-get update & sudo apt-get upgrade

I have looked at some of the threads on this problem but none seem to provide a solution.

Thanks in advance

Roy

---

### Post by surfer on 2010-11-23
try:
```
$ sudo chmod 0440 /etc/sudoers
```

and never ever edit this file with anything but
```
$ sudo visudo
```

---

### Post by surfer on 2010-11-23
oh, you probably will not be able to do that, as sudo will probably fail...

you will have to boot with a live cd, mount your root directory and chmod the file from there.

---

### Post by Roy M Cooper on 2010-11-24
Many thanks for the help,
However I am an Ubuntu newb. 
I can boot up of the live cd and mount the file system disk, but I am not familiar enough with terminal commands to change to that disk and run the operation.
If its not too much trouble I would really appreciate a walkthrough.

Sorry to be a pain

Cheers

Roy

---

### Post by surfer on 2010-11-24
ok, then you are almost there.

1. boot with a live cd (or usb stick ;) )
2. mount / 
```
$ sudo mount -t ext4 /dev/sd.. /mnt
```
(you found your root system already, so there is probably no confusion here, right? i mounted it on /mnt, but you are of course free to mount it whereever you want)
3. start a shell and enter
```
sudo chmod 0440 /mnt/etc/sudoers
```
again, you may have to edit the mountpoint (/mnt) addording to your needs here.

good luck & hope that works...

---

### Post by surfer on 2010-11-24
oh, then:
4. reboot into your real system and try
```
$ sudo -s
```
this should give you a root shell...

---

### Post by Roy M Cooper on 2010-11-24
Many Many Thanks.

Job Done

Roy

---

### Post by surfer on 2010-11-24
you're very welcome!

---

