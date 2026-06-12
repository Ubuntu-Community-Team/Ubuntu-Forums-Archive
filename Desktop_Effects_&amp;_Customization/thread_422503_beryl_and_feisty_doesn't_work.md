---
title: "beryl and feisty doesn't work"
date: 2007-04-25
forum: Desktop Effects &amp; Customization
---

### Post by mitjab on 2007-04-25
i use this howto
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL)

i use beryl-core=0.2.0~0beryl1 like it said there!

but beryl doesn't work.

I try with both methods but neither one work. 
If i add

0=Xgl
[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo
flexible=true

to

/etc/gdm/gdm.conf-custom

i can not see login screen anymore.

direct rendering is set to yes.

What to do?

Thx

---

### Post by Jaxilian on 2007-04-25
try this guide instead. it worked for me and I am quite a noob at this.

[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

---

### Post by mitjab on 2007-04-25
the same, any idea why

---

### Post by djpinger on 2007-04-25
In feisty, all I did was install the restricted drivers, reboot, then run:

```
sudo aptitude install beryl emerald-themes
```

It installed all the necesary dependancies.  Then, I put beryl-manager in the sessions and \\:D/

I would give that a shot and see how it works.

---

### Post by mitjab on 2007-04-25
hm i did that but not working.

I try this howto now
[https://wiki.ubuntu.com/BerylOnFeisty?highlight=%28beryl%29](https://wiki.ubuntu.com/BerylOnFeisty?highlight=%28beryl%29)

i get red cristal but beryl not working, no efects.

---

### Post by txhellkat138 on 2007-04-26
I have had beryl working since forever and nopw it wont work with nvidia aiglx at all I have the restricted drivers setup and everythijng and still nothing also when I try to enable desktop effects that fails as well

I had it working with beta just fine I dont know wtf the issue is

EDIT: Well now I have it working. I did an sudo apt-get remove nvidia-glx then I installed the driver form tjhe nvidia site. ANd it just worked only issue now is no beryl setting manager

---

### Post by mitjab on 2007-04-29
hm does anyone know if i need svn drivers of beryl?

---

### Post by conjur3r on 2007-04-29
Does System > Preferences > Desktop Effects work?  Maybe it's not a Beryl thing.

---

### Post by mitjab on 2007-05-03
no it doesn't work. It said that composite extension is not avaliable!

What must install that this will work?

Thx

---

### Post by txhellkat138 on 2007-05-17
the only difference im seeing between the driver in the feisty repo and hte one from the site is that the one from nvidia is making sure there is a symlink to the libgl.so file or whatever as soon as the driver from nvidia made that everything was back to normal

---

