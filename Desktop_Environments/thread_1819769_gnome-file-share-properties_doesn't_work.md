---
title: "gnome-file-share-properties doesn't work"
date: 2011-08-06
forum: Desktop Environments
---

### Post by richardsith on 2011-08-06
Hello everybody,
I need help to configure gnome for sharing directories.
I've configured gnome-file-share-properties on all my Ubuntu's PC for sharing the directory Public to each other. I following some guide found on Internet for the configuration of it, all explain the same procedure but in my case I don't see any Public directory shared with the PC. Following this link

[http://library.gnome.org/users/gnome-user-share/stable/gnome-user-share-getting-started.html.en](http://library.gnome.org/users/gnome-user-share/stable/gnome-user-share-getting-started.html.en)

I'd see the directory Public plus the name of PC that shares its directory on Nautilus Places.

In my case I don't see anything, therefore on the Network place see all the machines 'n if I try to click on one receive this:

"DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)"

note: I don't want to use Samba because I've all Ubuntu PC, and the firewall is disabled on all PC.

Thanks a lot

---

### Post by richardsith on 2011-08-07
is there anyone can help me??

---

### Post by Morbius1 on 2011-08-07
I don't use Personal File Sharing since even when it works it doesn't work consistently but you might want to try starting or restarting avahi:

```
sudo service ahavi-daemon start
```
OR:
```
sudo service avahi-daemon restart
```

---

### Post by richardsith on 2011-08-09
I'm so sorry for my later.
I did it but nothing...I've decided to us Samba!!!
I don't know  why that application is present in Gnome and it doesn't work
:confused:

---

### Post by Morbius1 on 2011-08-09
I think it's there because it's a bundled application that brings with it Bluetooth connectivity. The non bluetooth part ( the part you are trying to use ) is disabled by default and you had to add an apache and avahi package to make it start properly.

For some it works without issue, for some it's sporadic, and for others not at all.

---

### Post by richardsith on 2011-08-10
thanks a lot for your explanation, it's more clear now. I hope Gnome resolve that soon.

---

### Post by PayPaul on 2011-09-23
I also tried to enable file sharing today and was informed that "File sharing cannot be enabled because the required packages are not installed in your system". 

Where do I get these required packages. Perusing the threads today I've discovered it has something to do with Samba. How do I know it's installed or not and if not how do I get it? I tried the applications launcher, searched for Samba and got no response. If not Samba what other packages in Ubuntu 11.04 will allow file sharing and access to my computer network?

---

