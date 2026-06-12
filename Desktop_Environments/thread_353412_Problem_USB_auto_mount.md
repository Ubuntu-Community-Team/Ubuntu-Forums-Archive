---
title: "Problem: USB auto mount"
date: 2007-02-04
forum: Desktop Environments
---

### Post by geco on 2007-02-04
Hello, I have some problems when I plug in my usb keys.
I can mount them as normal user only if I write manually the fstab file. Otherwise KDE isn't able to write fstab and mount the usb keys. It doesn't recognize it.
Does anyone know something about it?

Thanks.

byebye

Geco

EDIT:
Actually, when I pug in my usb key I can find it in media:/n konqueror.
When I click on it to mount the device a window opens saying:

[i]A security policy place in prevents this sender from sending this message to this recipient, see message bus 
configuration file (rejected message had interface "org.freedesktop.Hal.Device.Volume" member "Mount" error name "(unset)"
destination "org.freedesktop.Hal")
[/i]

I searched around the forum but I didn't find a solution. My normal user is member of *plugdev* group, so I could be able to mount USB automatically.

---

### Post by dcstar on 2007-02-04
> **geco said:**
> Hello, I have some problems when I plug in my usb keys.
I can mount them as normal user only if I write manually the fstab file. Otherwise KDE isn't able to write fstab and mount the usb keys. It doesn't recognize it.
Does anyone know something about it?

Thanks.

byebye

Geco

EDIT:
Actually, when I pug in my usb key I can find it in media:/n konqueror.
When I click on it to mount the device a window opens saying:

[i]A security policy place in prevents this sender from sending this message to this recipient, see message bus 
configuration file (rejected message had interface "org.freedesktop.Hal.Device.Volume" member "Mount" error name "(unset)"
destination "org.freedesktop.Hal")
[/i]

I searched around the forum but I didn't find a solution. My normal user is member of *plugdev* group, so I could be able to mount USB automatically.

Does this problem occur after you logout your session and then log back in again?

If it starts working correctly after a subsequent login, disable any autologin after booting and wait a little while before logging in - this fixes my automount issue in Gnome (I use a timed login instead of autologin now).

---

### Post by geco on 2007-02-05
> **dcstar said:**
> Does this problem occur after you logout your session and then log back in again?

If it starts working correctly after a subsequent login, disable any autologin after booting and wait a little while before logging in - this fixes my automount issue in Gnome (I use a timed login instead of autologin now).

No, it doesn't. Actually I log in with text mode and then I start an X session.
Anyway I have this issue also at my first login.

---

### Post by geco on 2007-02-07
> **geco said:**
> Hello, I have some problems when I plug in my usb keys.
I can mount them as normal user only if I write manually the fstab file. Otherwise KDE isn't able to write fstab and mount the usb keys. It doesn't recognize it.
Does anyone know something about it?

Thanks.

byebye

Geco

EDIT:
Actually, when I pug in my usb key I can find it in media:/n konqueror.
When I click on it to mount the device a window opens saying:

[i]A security policy place in prevents this sender from sending this message to this recipient, see message bus 
configuration file (rejected message had interface "org.freedesktop.Hal.Device.Volume" member "Mount" error name "(unset)"
destination "org.freedesktop.Hal")
[/i]

I searched around the forum but I didn't find a solution. My normal user is member of *plugdev* group, so I could be able to mount USB automatically.

up... no one knows??????

---

### Post by yemu on 2007-02-08
i don't wan't to steal your post, but i'd like to ask a question the other way round: is it possible to disable automounting of a particulat usb device? i have a pendrive with two partitions (and a stupid windows software on one which is read-only), and everytime i plug it in nautilus opens two windows with two partition, and only one is usable, so i want to disable the other one.
thanks for help, and sorry for being a little OT

---

### Post by geco on 2007-02-08
I am on KDE, but I think that yours is a general question.
I found an answer here:
[http://ubuntuforums.org/showthread.php?t=81885&highlight=kde+autoplay](http://ubuntuforums.org/showthread.php?t=81885&highlight=kde+autoplay)

byebye

(please help me for my problem!)

---

### Post by geco on 2007-02-09
problem solved.

I searched around the web and found a useful suggestion.

the key file for automount is 
```

/etc/dbus-1/system.d/hal.conf

```

where, provided that your normal user belongs to **plugdev** group, you should add these lines:

```


 <!-- modification in order to KDE users can mount -->
    <policy group="plugdev">
            <allow send_interface="org.freedesktop.Hal.Device.Volume"/>
            <allow send_interface="org.freedesktop.Hal.Device.Volume.Crypto"/>
     </policy>

```

(actually the first line is a comment)

I also solved another problem I posted some days ago [here]("http://ubuntuforums.org/showthread.php?t=352648") and so I don't know if the two problems were linked

---

### Post by ashrack on 2007-02-13
GECO
tanx this actually worked 4M.

But I still find this weird because usb automount has worked for me eversince I installed Edgy. And yesterday it just stopped working.

---

### Post by rsea on 2007-02-13
Same happened with me but I use debian etch.

The solution didn't worked because I already have that expression on my hal.conf

I would preciate any help. I know is not Ubuntu but I looked all around and didn't find any solution

Thank you.
Rodolfo.

---

### Post by gefenm11 on 2007-03-17
> **rsea said:**
> Same happened with me but I use debian etch.

The solution didn't worked because I already have that expression on my hal.conf

I would preciate any help. I know is not Ubuntu but I looked all around and didn't find any solution

Thank you.
Rodolfo.

i have the same problem....
any help will be appreciated

---

