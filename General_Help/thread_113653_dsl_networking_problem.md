---
title: "dsl networking problem"
date: 2006-01-06
forum: General Help
---

### Post by xaos5 on 2006-01-06
I have a problem I can't seem to figure out, eth0 and ppp0 aren't loading on boot. If I do this:
```
sudo ifconfig eth0 up
pon dsl-provider
```
It works, but this is annoying having to do it at every boot.

---

### Post by adwait on 2006-01-06
I don't really know why this happening, but I can give you a stop gap solution. Put those commands in a text file. Make the file executabe with
```
chmod +x <filename>
```

Put it in /etc/init.d/
```
sudo mv <file> /etc/init.d/
```

Now run
```
sudo rcconf
```

Scroll down to find you filename in the list and check the box against it using the space bar and okay your way out.

---

### Post by xaos5 on 2006-01-07
```
#/bin/bash
ifconfig eth0 up
pon dsl-provider
```

seem fine to you or does it need sudo in front of them?

---

### Post by adwait on 2006-01-07
Actually, its fine, since it will be executed by root anyway.

---

### Post by xaos5 on 2006-01-08
ok that script worked fine, however it wouldn't let gnome boot at all, I figured it could have been something wrong with the de so I tryed fluxbox and it worked, just took a while. I googled it but seems the only thing similar was a date problem gnome seems to act funny, which wasn't my problem. I disabled the script and everything started working again. Have anyother suggestions?

---

### Post by pietro_spina on 2006-01-10
[QUOTE=xaos5]Have anyother suggestions?[/QUOTE]

try
```
sudo pppoeconf
```

and be sure to select 'connect on boot' in the options....

-p

---

