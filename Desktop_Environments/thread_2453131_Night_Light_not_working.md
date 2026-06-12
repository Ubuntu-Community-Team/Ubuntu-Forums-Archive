---
title: "Night Light not working"
date: 2020-11-03
forum: Desktop Environments
---

### Post by fpsdf2 on 2020-11-03
Light Night simply is not working. 

All is set up, but the display remains white as snow.

Any workaround? Thank you!

---

### Post by ActionParsnip on 2020-11-04
What is the output of
```

lsb_release -a; uname -a; apt-cache policy gnome-shell

```
Thanks

---

### Post by Dennis N on 2020-11-04
For Sunset to Sunrise activation be sure Location Services is ON. Otherwise, Night Light wouldn't know the UTC times for Sunset and Sunrise.

---

### Post by vanadium on 2020-11-04
Location services must not be on for night light to work. The info is taken from the Region settings. Probably you should also provide info on your hardware,i.e., graphical card.

---

### Post by fpsdf2 on 2020-11-05
> **ActionParsnip said:**
> What is the output of
```

lsb_release -a; uname -a; apt-cache policy gnome-shell

```
Thanks

Thanks!

This is the output:

```
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 20.04 LTS
Release:    20.04
Codename:    focal
Linux buntu 5.4.0-52-generic #57-Ubuntu SMP Thu Oct 15 10:57:00 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
gnome-shell:
  Installed: 3.36.4-1ubuntu1~20.04.2
  Candidate: 3.36.4-1ubuntu1~20.04.2
  Version table:
 *** 3.36.4-1ubuntu1~20.04.2 500
        500 http://pt.archive.ubuntu.com/ubuntu focal-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu focal-security/main amd64 Packages
        100 /var/lib/dpkg/status
     3.36.1-5ubuntu1 500
        500 http://pt.archive.ubuntu.com/ubuntu focal/main amd64 Packages
```

---

### Post by fpsdf2 on 2020-11-05
> **Dennis N said:**
> For Sunset to Sunrise activation be sure Location Services is ON. Otherwise, Night Light wouldn't know the UTC times for Sunset and Sunrise.

Thanks! Actually, defining a particular schedule (instead of automatic sunset/sunrise local time), doesn't also help...

---

### Post by ActionParsnip on 2020-11-05
Are there any existing bugs for it reported on Launchpad.net?

---

### Post by fpsdf2 on 2020-11-06
> **ActionParsnip said:**
> Are there any existing bugs for it reported on Launchpad.net?

I honestly don't know...

---

### Post by Dennis N on 2020-11-07
> **fpsdf2 said:**
> Thanks! Actually, defining a particular schedule (instead of automatic sunset/sunrise local time), doesn't also help...

I tried the Night Light in Ubuntu 20.10 last night, and couldn't get it to come on in either mode (Sunrise to Sunset or Manual). Location Services setting had no effect in either mode.  

_Update_: This conclusion may not be correct, because the tested Ubuntu 20.10 was installed as a VM. Some further checking showed that the night light in a VM is actually being controlled by the host. If night light is switched OFF in the host, you can't activate it in the guest. If it's ON and active on the host, the guest display is also be affected. It is not independent. There is no 20.10 here that's a standard install to test. Night Light in sunset-to-sunrise mode set correct times immediately when Location Services was switched ON.

---

### Post by fpsdf2 on 2020-11-15
Thank you! In this case, it's not a VM. It's a regular installation on a mid-2010 Macbook Pro.

---

### Post by gdesilva on 2020-11-17
I am sure this is not the solution you are looking for but redshift-gtk works well for me. If it turns out to be a bug then worth giving redshift-gtk a go.

---

### Post by fpsdf2 on 2020-11-25
Oh god... this has been really frustrating. I don't know how to install/launch this redshift thing. Any help? Thanks

---

### Post by gdesilva on 2020-11-26
OK, simply 

1. open Terminal application. - Ctrl+Alt+T will open one for you
2. type 'sudo apt install redshift-gtk' (without ticks) and press enter - you will be asked to enter your password.
3. this will install redshift-gtk on your system.
4. once the installation is completed type 'redshift-gtk &'      here the '&' will make it run as a background process
5. now you should see a light bulb icon on the notifications tray. 
6. Right click on the light bulb icon and check the Autostart option so that it will be started each time you boot the system.

Redshift-gtk will work out your location and adjust the brightness after dark. Hope this will provide a work around for your problem.

---

### Post by fpsdf2 on 2020-11-28
> **gdesilva said:**
> OK, simply 

1. open Terminal application. - Ctrl+Alt+T will open one for you
2. type 'sudo apt install redshift-gtk' (without ticks) and press enter - you will be asked to enter your password.
3. this will install redshift-gtk on your system.
4. once the installation is completed type 'redshift-gtk &'      here the '&' will make it run as a background process
5. now you should see a light bulb icon on the notifications tray. 
6. Right click on the light bulb icon and check the Autostart option so that it will be started each time you boot the system.

Redshift-gtk will work out your location and adjust the brightness after dark. Hope this will provide a work around for your problem.

Awesome! Thank you so much. I've finally got my screen "warm" again!

Have a nice day!

---

