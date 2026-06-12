---
title: "GKSUDO Error"
date: 2006-06-02
forum: Desktop Environments
---

### Post by R3linquish3r on 2006-06-02
For some reason gksudo has not worked for me at all in dapper. I don't know if it is the fact I'm using fluxbox, or I'm missing some kind of library, but this is the error I get when I try to open a program with gksudo:

```
X Error: BadDevice, invalid or uninitialized input device 170
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 170
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
```

---

### Post by bluevoodoo1 on 2006-06-02
what about sudo? Will that not work as well?

---

### Post by R3linquish3r on 2006-06-02
Sudo works fine. I'de just like to run stuff like firestarter and etherape without having to keep a term open.

---

### Post by bluevoodoo1 on 2006-06-02
hmmm, you could try reinstalling the "gksu" package.

as an alternative (until gksudo is fixed)

```
sudo nohup firestarter
```

"nohup" will let you open an app. from the terminal, then close the window.

---

### Post by stontyro on 2006-06-02
I, too, am having problems with gksu, but my error is that gksu can't resolve my computer's hostname.

Gksu worked yesterday.  I tried to get my wlan running -- I had problems with wep encryption, but that's another topic -- and I did some stuff with the gnome network manager.  I didn't touch anything that had to do with name resolution, though.  I noticed that my /etc/hosts file is blank except for one commented line.  Is it supposed to be that way, or was it destroyed?  What do I need to dpkg-reconfigure to reset it?  I'd rather use dpkg-reconfigure than a text editor, because it seems like the more elegant procedure.

Oh, and I have the same problem with sudo.  If there isn't a way to point sudo to 127.0.0.1 explicitly from the command line, I think my only option here is to boot up into single-user mode -- otherwise, I think I'm locked out of root (no password == can't log-in).

---

### Post by stontyro on 2006-06-02
update:

So, I went single-user and did three things: 1) passwd root, 2) put one line in /etc/hosts pointing localhost and my hostname to 127.0.0.1, and 3) reboot.

I am happy to report that gksu and sudo worked after the reboot.  The first thing I did after logging in is to start up the gnome network manager... and I think I know what happened.

Gnome network manager has so-called locations, or profiles to easily change how your network connection is configured.  Somehow, no location was selected.  I set up two locations yesterday: home and campus.  I selected home and immediately my /etc/hosts was populated with all the ipv4 and ipv6 loopback-related stuff.  I checked that the same information was present for the campus location, and it was.  Is there a way to ensure that a location is actually selected when I boot my computer, instead of nothing?

Edit: This network manager problem is pretty annoying.  I start the manager, select a location, and click ok.  I start the manager again and no location is selected.

---

### Post by R3linquish3r on 2006-06-02
It's looking like this is less of a problem with gksudo and more of a problem with the ubuntu package itself. I'm getting this error with regular gedit and other simple gtk programs.

---

### Post by bluevoodoo1 on 2006-06-02
[QUOTE=R3linquish3r]It's looking like this is less of a problem with gksudo and more of a problem with the ubuntu package itself. I'm getting this error with regular gedit and other simple gtk programs.[/QUOTE]

you could try installing "ubuntu-desktop" (if it isn't already) to see if there are any missing packages.

---

