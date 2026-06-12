---
title: "lubuntu 12.04 cannot disable autologin"
date: 2012-07-11
forum: Desktop Environments
---

### Post by ar2yild on 2012-07-11
Hi All, 

I installed lubuntu 12.04 64 bit and while installing I checked 'autologin" option but now I do not want this feature. I entered this command:
```

update-alternatives --config lxdm.conf

```

the output is:
```

There is only one alternative in link group lxdm.conf: /etc/xdg/lubuntu/lxdm/lxdm.conf
Nothing to configure.

```

So I edited corresponding lxdm.conf file and comment autologin line and then reboot the machine. But again it did not show login screen! What can be the problem? My lxdm file output is:

```

[base]
## uncomment and set autologin username to enable autologin
# autologin=dgod

## uncomment and set timeout to enable timeout autologin,
## the value should >=5
# timeout=10

## default session or desktop used when no systemwide config
session=/usr/bin/startlubuntu

## uncomment and set to set numlock on your keyboard
# numlock=0

## set this if you don't want to put xauth file at ~/.Xauthority
# xauth_path=/tmp

## greeter used to welcome the user
greeter=/usr/lib/lxdm/lxdm-greeter-gtk

[server]
## arg used to start xserver, not fully function
# arg=/usr/bin/X -background vt1

[display]
## gtk theme used by greeter
gtk_theme=Clearlooks

## background of the greeter
bg=/usr/share/lubuntu/wallpapers/lubuntu-default-wallpaper.png

## if show bottom pane
bottom_pane=1

## if show language select control
lang=1

## if show keyboard layout select control
keyboard=0

## the theme of greeter
theme=Lubuntu

[input]

[userlist]
## if disable the user list control at greeter
disable=0

## whitelist user
white=

## blacklist user
black=


```

Thanks guys...

---

### Post by black veils on 2012-07-11
would it help to install ```
gnome-system-tools
``` then change the option in Users and Groups, like in Ubuntu?

---

### Post by kc1di on 2012-07-11
you may find this page of help.
[http://manpages.ubuntu.com/manpages/lucid/man1/lxdm.1.html]("http://manpages.ubuntu.com/manpages/lucid/man1/lxdm.1.html")

Reverse the steps for autologin should work.

---

### Post by ar2yild on 2012-07-11
Anyway, I solved the problem. I noticed lubuntu 12.04 uses lightdm as a display manager so I changed lightdm config file named lightdm.conf located at /etc/lightdm. then I uncommented some lines starting with autologin word. after reboot, it shows login screen. But it is again erroneous that lightdm does not respect lxdm.conf. I think it is also the key point if you want to enable autologin in lubuntu 12.04. So keep in mind guys!

---

### Post by MG&amp;TL on 2012-07-11
> **ar2yild said:**
> Anyway, I solved the problem. I noticed lubuntu 12.04 uses lightdm as a display manager so I changed lightdm config file named lightdm.conf located at /etc/lightdm. then I uncommented some lines starting with autologin word. after reboot, it shows login screen. But it is again erroneous that lightdm does not respect lxdm.conf. I think it is also the key point if you want to enable autologin in lubuntu 12.04. So keep in mind guys!

Why would it respect lxdm.conf? It is a separate program, with different options.

---

