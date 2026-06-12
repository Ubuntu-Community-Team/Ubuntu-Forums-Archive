---
title: "Gnome 3 GFX Corruption"
date: 2011-11-11
forum: Desktop Environments
---

### Post by its_jon on 2011-11-11
Hi.

I just installed Gnome 3 from synaptic after upgrading to the latest Ubuntu.

Unfortunately I have corruption of the top bar and text.

Its a Toshiba Satellite with ati

Where to start ?????

---

### Post by sikander3786 on 2011-11-11
I guess you are running Oneiric. Lets make sure by getting to a Terminal (by pressing the <Super> key and searching the Dash) and running this command:

```
lsb_release -a
```

If it says 11.10, you can easily run Gnome 3.

Now the question is did you only install some of the Gnome 3 packages or installed the gnome-shell package also, which is what you probably want to run. From Terminal:

```
dpkg -l gnome-shell
dpkg -l gnome-session*
```

Please post the outputs.

Regarding the corruption of top bar and the text, run this command to find if you can actually run Unity and Gnome Shell:

```
/usr/lib/nux/unity_support_test -p
```

Please post the output of this one also.

---

### Post by typhoon_tip on 2011-11-11
> **its_jon said:**
> Its a Toshiba Satellite with **ati**

Where to start ?????

Well if you installed FGLRX driver, start with using Unity lol

Joking apart, Gnome 3 is not compatible yet with FGLRX (or the opposite, who knows...).

The latest FGLRX driver from AMD website is much better, but the screen still flickers when notification appears.

---

### Post by its_jon on 2011-11-11
```
lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 11.10
Release:	11.10
Codename:	oneiric
evelyn@evelyn-Satellite-L300D:~$ dpkg -l gnome-shell
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  gnome-shell    3.2.1-0ubuntu1 graphical shell for the GNOME desktop
```

```
dpkg -l gnome-session*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  gnome-session  3.2.1-0ubuntu1 GNOME Session Manager - GNOME 3 session
ii  gnome-session- 3.2.1-0ubuntu1 GNOME Session Manager - Minimal runtime
ii  gnome-session- 0.28-0ubuntu11 GNOME session log in and log out sound event
ii  gnome-session- 3.2.1-0ubuntu1 GNOME Session Manager - common files
ii  gnome-session- 3.2.1-0ubuntu1 GNOME Session Manager - GNOME fallback sessi

```

```
Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

```

hope this is what you need....thanks for the support !

---

### Post by typhoon_tip on 2011-11-11
Post the result of this command:
```
update-alternatives --get-selections | grep gl_conf
```

---

### Post by its_jon on 2011-11-14
```
i386-linux-gnu_gl_conf         auto     /usr/lib/fglrx/ld.so.conf
x86_64-linux-gnu_gl_conf       auto     /usr/lib/fglrx/alt_ld.so.conf
```

thank you for the help

---

### Post by its_jon on 2012-01-23
could not get it to work with that chipset.... new laptop now though...and Gnome 3 working very well

---

