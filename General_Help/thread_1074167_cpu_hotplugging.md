---
title: "cpu hotplugging"
date: 2009-02-18
forum: General Help
---

### Post by raj9786 on 2009-02-18
Can anyone lead me through enabling cpu hotplugging? I read that I need to enable some stuff when doing make defconfig but I'm pretty newb so any help would be appreciated. I'm not sure if hotplugging is enabled on my system already. Is there any way to tell? Here are the results when I try running the following command:

```
raj@rahul-laptop:~$ sudo echo 0 > /sys/devices/system/cpu/cpu1/online
bash: /sys/devices/system/cpu/cpu1/online: Permission denied
```

I would like to temporarily turn off one of the cores of the processor because having multiple cores enabled causes my entire system to crash when connecting to a vpn using the cisco vpn client. I am using 8.10 on a dell 1520 laptop with a dual core intel processor. Thanks for your help.

---

### Post by raj9786 on 2009-02-19
I can confirm that when I turn off multicore support in the BIOS, the vpn client works without a problem. Anyone have any suggestions?

---

### Post by pnutzh4x0r on 2009-02-19
I don't know how CPU hotplugging works, but the error you are getting is because you don't have permissions to write to the file because you are piping the output of a program.  You should try the following instead:

```
$ sudo sh -c 'echo 0 > /sys/devices/system/cpu/cpu1/online'

```

More information about your piping error can be found here: [http://stackoverflow.com/questions/82256/how-do-i-use-sudo-to-redirect-output-to-a-location-i-dont-have-permission-to-wri](http://stackoverflow.com/questions/82256/how-do-i-use-sudo-to-redirect-output-to-a-location-i-dont-have-permission-to-wri)

As for whether or not setting that parameter will work, I don't know, but at least the above command will allow you to set it.  Good luck.

---

### Post by Yellow Pasque on 2009-02-19
CPU hotplugging is enabled by default in Ubuntu 8.10's kernel configuration, so if your system/BIOS is capable of it, you should be able to do it.

---

### Post by heindsight on 2009-02-19
> **pnutzh4x0r said:**
> 
```
$ sudo sh -c 'echo 0 > /sys/devices/system/cpu/cpu1/online'
```


You can also do
```
$ echo 0 | sudo tee /sys/devices/system/cpu/cpu1/online
```

---

