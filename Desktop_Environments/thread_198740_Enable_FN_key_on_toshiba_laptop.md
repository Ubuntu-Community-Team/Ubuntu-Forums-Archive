---
title: "Enable FN key on toshiba laptop"
date: 2006-06-17
forum: Desktop Environments
---

### Post by stiankarlsen on 2006-06-17
I really need to have the FN key working on my laptop, so that I can dim the screen to save battery power.

Any Idea why the FN key isnt responing at all, is there a way to enable or make it work?

---

### Post by raptros-v76 on 2006-06-17
look though synaptic for the toshiba packages

[edit] the package you want is fnfxd

---

### Post by RavenOfOdin on 2006-06-17
I think the option "Toshiba Laptop Support" exists somewhere in the 2.6.16 kernel config.

---

### Post by stiankarlsen on 2006-06-17
[QUOTE=raptros-v76]look though synaptic for the toshiba packages

[edit] the package you want is fnfxd[/QUOTE]


thanks for the response.

I've installed the fnfxd package, but nothing happened.

I ran it in a shell, and got this.

```
stian@ubuntustian:~$ sudo fnfxd
Password:
FnFX Daemon v0.3 (c) 2003, 2004 Timo Hoenig <thoenig@nouse.net>

fatal error: Could open /proc/acpi/toshiba/keys.

Please make sure that your kernel has enabled the Toshiba option in the ACPI section.
For more information read the documentation and/or http://fnfx.sf.net/index.php?section=doc#kernel.

stian@ubuntustian:~$ sudo fnfxd
FnFX Daemon v0.3 (c) 2003, 2004 Timo Hoenig <thoenig@nouse.net>

fatal error: Could open /proc/acpi/toshiba/keys.

Please make sure that your kernel has enabled the Toshiba option in the ACPI section.
For more information read the documentation and/or http://fnfx.sf.net/index.php?section=doc#kernel.

```

I'm fairly new to linux, so perhaps it kind of obvious, but i dont understand what to do next, further help would be greatly appreciated by anyone!

---

### Post by raptros-v76 on 2006-06-17
install anything in synaptic that comes up with the search for toshiba

---

### Post by stiankarlsen on 2006-06-17
I get nothing when I search for toshiba

---

### Post by raptros-v76 on 2006-06-17
do you have you're universe and multiverse repositories enabled?

---

### Post by stiankarlsen on 2006-06-17
I've enabled all reps in synaptics, and here's my sources

> deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
# The above lines were generated automatically by EasyUbuntu 3.0 Beta Release
# The rest of your sources.list follows

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe
## Uncomment the following two lines to add software from the 'backports'
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe



---

