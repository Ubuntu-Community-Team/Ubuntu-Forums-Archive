---
title: "Module options ignored at boot"
date: 2006-01-24
forum: Desktop Environments
---

### Post by luisca on 2006-01-24
Hi, I need to specify a parameter for my NIC (3c59x) since I am in a 10BaseT network and the card defaults to 100BaseT, resulting in very poor performance. I added a local file to /etc/modprobe.d containing the line "options 3c59x options=0x200".

At boot the card ignores it at goes to 100BaseT mode. However, I know it should work since if after boot I rmmod and modprobe the module (without parameters at command line), it uses the option and goes to 10BaseT mode. Is this the expected behaviour? How can I fix this? I could make a script to rmmod/modprobe the module at the final stage of booting but I'd like to know the proper way to solve this.

Thanks a lot

---

### Post by dcstar on 2006-01-24
[QUOTE=luisca]Hi, I need to specify a parameter for my NIC (3c59x) since I am in a 10BaseT network and the card defaults to 100BaseT, resulting in very poor performance. I added a local file to /etc/modprobe.d containing the line "options 3c59x options=0x200".

At boot the card ignores it at goes to 100BaseT mode. However, I know it should work since if after boot I rmmod and modprobe the module (without parameters at command line), it uses the option and goes to 10BaseT mode. Is this the expected behaviour? How can I fix this? I could make a script to rmmod/modprobe the module at the final stage of booting but I'd like to know the proper way to solve this.

Thanks a lot[/QUOTE]
I believe you need a file in /etc/modprobe.d containing the options.

Have a look in there for examples (I think each file gets processed in turn at boot-up).

---

### Post by luisca on 2006-01-25
[QUOTE=dcstar]I believe you need a file in /etc/modprobe.d containing the options.

Have a look in there for examples (I think each file gets processed in turn at boot-up).[/QUOTE]

As I said in my first post, I already added it, and indeed when after booting I load the module without parameters, it gets loaded with the options from the file , but this options are not used at boot, I do not know why.

---

