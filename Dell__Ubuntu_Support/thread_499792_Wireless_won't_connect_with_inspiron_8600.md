---
title: "Wireless won't connect with inspiron 8600"
date: 2007-07-13
forum: Dell  Ubuntu Support
---

### Post by Hybrid86 on 2007-07-13
Hi, I'm new to ubuntu and just installed it on my dell laptop. I was really psyched at first, but when I tried to connect to the internet wirelessly, my heart sank. Apparently, it appears that it's decting signal strength from my router, but sites still won't load :confused: Wired internet seems to work fine though...
I am not using an inserted card; my laptop has a built in intel centrino.

Can someone help me? I'm really excited to get started with ubuntu (and beryl in particular :P)

---

### Post by NilsE on 2007-07-13
In ubuntu 7.04 and Gutsy the following steps worked for me which I culled from a few other posts. This also added the capability to use WPA
```
In Synaptic package manager:

1) Make sure network-manager-gnome  is installed
2) Make sure wpasupplicant is installed
3) Install libpam-keyring

```
```
In System Administration:

Make sure the restricted driver for the chip is there, enabled and in use.
```


```
In terminal:

sudo echo "@include common-pamkeyring" | sudo tee -a /etc/pam.d/gdm

NOTE: This will allow you to remember connection passwords/keys in the keyring
and not get prompted by the keyring manager every time. This is not mandatory.
```


```
In System/Preferences/Session:

Add gksudo nm-applet (if the network manager is not there) as the command 
line to a new start programs. You can name it whatever you want. It may 
work without the gksudo.
```
```
You may also have to clean out the /etc/network/interfaces file if you have
 configured any devices manually. Just leave these 2 lines. (back it up first)

auto lo
iface lo inet loopback
```

SHUTDOWN AND RESTART

NOTE: The applet may not show up in the upper panel so you can right click 
on the top panel, select add to panel then add the notification applet.

NOTE: After the first time you try to connect to a new available network in the pulldown it will ask for the SSID and key etc. but should remember it after that.

NOTE: Make sure that in the manual settings for the configuration that all devices are set to roaming.

---

### Post by Hybrid86 on 2007-07-13
> In System Administration:

Make sure the restricted driver for the chip is there, enabled and in use.
The only thing listed there is my nivida driver. Should there be more there?

EDIT: Okay, this is just bizarre: it just spontaneously connected. No clue why or how, I just hope it keeps working...

---

