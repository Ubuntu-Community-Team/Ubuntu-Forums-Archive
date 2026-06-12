---
title: "[SOLVED] Flash plugin will not work!"
date: 2008-12-19
forum: General Help
---

### Post by kelean on 2008-12-19
I installed 8.10 with the wubi exe file.  Everything works really well except for flash in firefox.  I installed the non-free flash plugin for firefox but it will not work.  The drop down saying that additinal plugins required.  I click it and it shows me the three choices, i choose the non-free, click install.  Then it tells me that it is installed.  What am I missing I have never had this before.  I am using 32-bit.

Thanks Kelean

---

### Post by PCessna on 2008-12-19
> **kelean said:**
> I installed 8.10 with the wubi exe file.  Everything works really well except for flash in firefox.  I installed the non-free flash plugin for firefox but it will not work.  The drop down saying that additinal plugins required.  I click it and it shows me the three choices, i choose the non-free, click install.  Then it tells me that it is installed.  What am I missing I have never had this before.  I am using 32-bit.

Thanks Kelean

Go to Synaptic package manager.  (find it in System, and Administration I believe)

Find "no-free flash" or whatever its called, search for it

select it for complete removal, and then close all instances of firefox, and then click apply, after its done, check it for installation, apply it, close synaptic then open firefox back up.

---

### Post by kelean on 2008-12-19
i already did that and it did not work

---

### Post by albinootje on 2008-12-19
> **kelean said:**
> i already did that and it did not work

Please post the output of :
```

ls -la /usr/lib/mozilla/plugins/
ls -la /usr/lib/firefox/plugins/
ls ~/.mozilla/firefox/

```

---

### Post by PCessna on 2008-12-19
> **albinootje said:**
> Please post the output of :
```

ls -la /usr/lib/mozilla/plugins/
ls -la /usr/lib/firefox/plugins/
ls ~/.mozilla/firefox/

```

Actually, Alternatively, You can try completely removing **firefox**. Listen to albinoot's method first though.

---

### Post by kelean on 2008-12-19
here are the outputs of the commands you asked for.

```
klasra@ubuntu:~$ ls -la /usr/lib/mozilla/plugins/
total 8
drwxr-xr-x 2 root root 4096 2008-12-18 20:52 .
drwxr-xr-x 4 root root 4096 2008-10-29 18:02 ..
lrwxrwxrwx 1 root root   39 2008-12-18 20:52 libjavaplugin.so -> /etc/alternatives/mozilla-javaplugin.so
lrwxrwxrwx 1 root root   44 2008-12-18 19:10 libtotem-basic-plugin.so -> ../../totem/default/libtotem-basic-plugin.so
lrwxrwxrwx 1 root root   42 2008-12-18 19:10 libtotem-gmp-plugin.so -> ../../totem/default/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root root   44 2008-12-18 19:10 libtotem-mully-plugin.so -> ../../totem/default/libtotem-mully-plugin.so
lrwxrwxrwx 1 root root   50 2008-12-18 19:10 libtotem-narrowspace-plugin.so -> ../../totem/default/libtotem-narrowspace-plugin.so

```

```
klasra@ubuntu:~$ ls -la /usr/lib/firefox/plugins/
total 8
drwxr-xr-x 2 root root 4096 2008-12-18 20:52 .
drwxr-xr-x 4 root root 4096 2008-12-18 20:49 ..
lrwxrwxrwx 1 root root   39 2008-12-18 20:52 libjavaplugin.so -> /etc/alternatives/firefox-javaplugin.so

```

```
klasra@ubuntu:~$ ls ~/.mozilla/firefox/
nt2dnyq7.default  profiles.ini

```

I do not see any reference to flash player plugins

---

### Post by nordmichael29 on 2008-12-19
Does flash player not work at all? or are you like me and without sound?

---

### Post by kelean on 2008-12-19
Flash player does not work at all.  I have sound but I cannot control it with the volume control on the panel.  I can only change the volume with the speaker volume knob.

---

### Post by albinootje on 2008-12-20
> **kelean said:**
> here are the outputs of the commands you asked for.

```
klasra@ubuntu:~$ ls -la /usr/lib/mozilla/plugins/
total 8
drwxr-xr-x 2 root root 4096 2008-12-18 20:52 .
drwxr-xr-x 4 root root 4096 2008-10-29 18:02 ..
lrwxrwxrwx 1 root root   39 2008-12-18 20:52 libjavaplugin.so -> /etc/alternatives/mozilla-javaplugin.so
lrwxrwxrwx 1 root root   44 2008-12-18 19:10 libtotem-basic-plugin.so -> ../../totem/default/libtotem-basic-plugin.so
lrwxrwxrwx 1 root root   42 2008-12-18 19:10 libtotem-gmp-plugin.so -> ../../totem/default/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root root   44 2008-12-18 19:10 libtotem-mully-plugin.so -> ../../totem/default/libtotem-mully-plugin.so
lrwxrwxrwx 1 root root   50 2008-12-18 19:10 libtotem-narrowspace-plugin.so -> ../../totem/default/libtotem-narrowspace-plugin.so

```

```
klasra@ubuntu:~$ ls -la /usr/lib/firefox/plugins/
total 8
drwxr-xr-x 2 root root 4096 2008-12-18 20:52 .
drwxr-xr-x 4 root root 4096 2008-12-18 20:49 ..
lrwxrwxrwx 1 root root   39 2008-12-18 20:52 libjavaplugin.so -> /etc/alternatives/firefox-javaplugin.so

```


Thanks for posting this.
Indeed there's no flash plugin at all.

Here's the relevant part on my system :
ls -la /usr/lib/mozilla/plugins/
lrwxrwxrwx 1 root root   37 2008-12-19 05:36 flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin

ls -la /etc/alternatives/mozilla-flashplugin 
lrwxrwxrwx 1 root root 46 2008-12-19 05:36 /etc/alternatives/mozilla-flashplugin -> /usr/lib/flashplugin-nonfree/libflashplayer.so

You only need this one file : libflashplayer.so

Can you do this :
```

sudo apt-get install --reinstall flashplugin-nonfree

```
And check whether the flash-plugin gets downloaded properly, without errors.

---

### Post by kelean on 2008-12-20
albinootje, thank you for your help.  I tried what you suggested.

```
sudo apt-get install --reinstall flashplugin-nonfree
```

It said that I had the newest version installed and did nothing.  So I completely removed it.  Went to the adobe sith and downloded the new flash player 10 and installed it with gdebi installer and what do you know it works great.

Thanks for all the help everyone.  Kelean.

---

