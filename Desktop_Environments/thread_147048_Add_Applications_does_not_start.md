---
title: "Add Applications does not start"
date: 2006-03-19
forum: Desktop Environments
---

### Post by PPisHere on 2006-03-19
Hi There,

'*Add Applications*' in Applications menu does not start and it does nothing - nothing happens.

Where does it go? :confused:

---

### Post by Sutekh on 2006-03-19
Can you open a terminal window (Applications -> Accessories) and type in
```
sudo gnome-app-install
```Enter your password when requested and if you recieve an error, please post it here.

---

### Post by PPisHere on 2006-03-21
Hi,

Here is result from *sudo gnome-app-install* :

```
Traceback (most recent call last):
  File "/usr/bin/gnome-app-install", line 41, in ?
    from AppInstall import AppInstall
  File "/usr/lib/gnome-app-install/AppInstall.py", line 30, in ?
    import gtkmozembed
ImportError: libgtkembedmoz.so: cannot open shared object file: No such file or directory
```

It seems that something is missing :D

---

### Post by ronmarley1 on 2006-03-21
[QUOTE=PPisHere]Hi There,

'*Add Applications*' in Applications menu does not start and it does nothing - nothing happens.

Where does it go? :confused:[/QUOTE]

Hi PPisHere,
Try this:
```
sudo apt-get install gnome-app-install
```

---

### Post by engla on 2006-03-21
gnome-app-install must already be there..

Have you done anything related to moz/mozembed, such as installing firefox 1.5 _and_ removing the old version?

The component that seems to have trouble is gtkmozembed in the package **python2.4-gnome2-extras**

You could try to mark this for reinstallation in synaptic, or equivalently run 
sudo apt-get --reinstall install python2.4-gnome2-extras

---

### Post by joshuapurcell on 2006-03-22
Not sure if this is the problem, but sometimes you will have weird issues with starting up gnome applications if you have recently changed your computer's hostname without restarting gnome. If this is the case, then you can just **Ctrl-Alt-F1**, then **sudo /etc/init.d/gdm stop**, then **sudo rm -r /tmp/orbit***, then **sudo /etc/init.d/gdm/start**. Restarting the whole computer would also do the trick. This is only if you've changed the hostname though...

---

### Post by PPisHere on 2006-03-22
Hi,

Thanks, but no success  :(

```
x@y:~$ sudo apt-get --reinstall install python2.4-gnome2-extras
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B/274kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y

Preconfiguring packages ...
(Reading database ... 77019 files and directories currently installed.)
Preparing to replace python2.4-gnome2-extras 2.12.0-0ubuntu1.1 (using .../python2.4-gnome2-extras_2.12.0-0ubuntu1.1_i386.deb) ...
Unpacking replacement python2.4-gnome2-extras ...
Setting up python2.4-gnome2-extras (2.12.0-0ubuntu1.1) ...

x@y:~$ sudo gnome-app-install
Traceback (most recent call last):
  File "/usr/bin/gnome-app-install", line 41, in ?
    from AppInstall import AppInstall
  File "/usr/lib/gnome-app-install/AppInstall.py", line 30, in ?
    import gtkmozembed
ImportError: libgtkembedmoz.so: cannot open shared object file: No such file or directory
x@y:~$

```

So, reinstalling does not help ](*,)

---

### Post by PPisHere on 2006-03-22
Forgot to comment:
> 
Not sure if this is the problem, but sometimes you will have weird issues with starting up gnome applications if you have recently changed your computer's hostname without restarting gnome.

No, I have not changed the hostname.

I think (not sure) that I updated to firefox-1.5.0.1, also intalled java etc stuff for firefox. But unfortunatelly I cannot be sure.

All I remenber that **Add Applications** used to work

---

