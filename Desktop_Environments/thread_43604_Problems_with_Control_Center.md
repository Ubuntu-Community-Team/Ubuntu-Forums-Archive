---
title: "Problems with Control Center"
date: 2005-06-22
forum: Desktop Environments
---

### Post by wizelf on 2005-06-22
Hi folks, whenever I want to use the control center and click on , let's say, font installer and then click on the Administrator mode,  get sent back to the intro blue screen.  At first I thought I needed to create a password for root and I did.  That didn't solve the problem. I get sent back to the blue screen all the time.  I tried using other sections that give me the administrator mode option and I get the same.  

Any help would be appreciated. 

Thanks.

---

### Post by Pcghost on 2005-06-22
I had this problem as well.  The way I fixed it was to type sudo kcontrol in a terminal and give your password.  That way it launches the control center in administrator mode from the get go.

---

### Post by zoon64 on 2005-06-22
I have the same problem.But if logged in as root it works fine. Anyone else have the same problems.

---

### Post by tristian on 2005-06-22
I found a better way of using root (not a cool idea) and I would not reccomend using this unless you "want" to break your system or you don't care about secuirty.

Well at the login screen click on the house icon and click console screen (root password must be enabled - read bottom) login into root and type *startx* and you will be able to do every without problems!

To enable root:
open a konsole and type *sudo passwd root* and input a new root password

---

### Post by IchBin on 2005-06-22
I came here to find an answer to the very problem in this post. Thanks for the temp fix, I hope there's a permanent fix.

---

### Post by elsewhere on 2005-06-22
[QUOTE=tristian]I found a better way of using root (not a cool idea) and I would not reccomend using this unless you "want" to break your system or you don't care about secuirty.

Well at the login screen click on the house icon and click console screen (root password must be enabled - read bottom) login into root and type *startx* and you will be able to do every without problems!

To enable root:
open a konsole and type *sudo passwd root* and input a new root password[/QUOTE]

If you want, you can change AllowRootLogin=false to true in /etc/kde3/kdmrc.  That will allow you to login as root from the login window without using a console.

But as you pointed out, I wouldn't generally recommend it to most people.  Too easy to damage your system if you're not careful.

Cheers,
KV

---

### Post by godzero on 2005-06-22
Preamble:
I'm using kubuntu/kde 3.4.1/linux 2.6.11.1

I had the same prob earlier on kubuntu an another distro (mandriva?)

I believe the way I fixed it was to "sudo adduser...", actually, I think I edited the file by hand (sudo gedit /etc...)

Now works fine.

I'm newish to linux, verry new to (k)ubuntu so I fix things w/o nessesarily remembering the paths/etc.

---

### Post by Copter on 2005-07-26
hi!

i have the same problem. sometimes it just crashes

```

copter@xidge:~$ sudo kcontrol
Error: "/var/tmp/kdecache-copter" is owned by uid 1000 instead of uid 0.
Link points to "/var/tmp/kdecache-root"
ERROR: Communication problem with kcontrol, it probably crashed.

```

with this debug info

```

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
`system-supplied DSO at 0xffffe000' has disappeared; keeping its symbols.
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1229863616 (LWP 7960)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[KCrash handler]
#4  0x00000001 in ?? ()
#5  0xb7d9c5b0 in KCModuleProxy::~KCModuleProxy () from /usr/lib/libkutils.so.1
#6  0xb7017342 in QWidget::~QWidget () from /usr/lib/libqt-mt.so.3
#7  0xb730f4ef in QFrame::~QFrame () from /usr/lib/libqt-mt.so.3
#8  0xb7017342 in QWidget::~QWidget () from /usr/lib/libqt-mt.so.3
#9  0xb791b4a3 in KJanusWidget::~KJanusWidget () from /usr/lib/libkdeui.so.4
#10 0xb7017342 in QWidget::~QWidget () from /usr/lib/libqt-mt.so.3
#11 0xb7162eaa in QDialog::~QDialog () from /usr/lib/libqt-mt.so.3
#12 0xb79142da in KDialogBase::~KDialogBase () from /usr/lib/libkdeui.so.4
#13 0xb7d8f66a in KCMultiDialog::~KCMultiDialog () from /usr/lib/libkutils.so.1
#14 0xb7fda02a in KCMShellMultiDialog::~KCMShellMultiDialog ()
   from /usr/lib/libkdeinit_kcmshell.so
#15 0xb7fd8ab5 in kdemain () from /usr/lib/libkdeinit_kcmshell.so
#16 0x080484bf in ?? ()
#17 0x00000002 in ?? ()
#18 0xbffff854 in ?? ()
#19 0xbffff828 in ?? ()
#20 0xb7dd18c8 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#21 0xb7dd18c8 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#22 0x08048401 in ?? ()

``` 

or it works fine but pops some errors

```

copter@xidge:~$ Error: "/tmp/ksocket-copter" is owned by uid 1000 instead of uid 0.
Link points to "/tmp/ksocket-root"
Error: "/var/tmp/kdecache-copter" is owned by uid 1000 instead of uid 0.
Link points to "/var/tmp/kdecache-root"
Error: "/var/tmp/kdecache-copter" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-copter" is owned by uid 1000 instead of uid 0.
Link points to "/var/tmp/kdecache-root"
Link points to "/var/tmp/kdecache-root"
Error: "/var/tmp/kdecache-copter" is owned by uid 1000 instead of uid 0.
Link points to "/var/tmp/kdecache-root"
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
copter@xidge:~$

``` 

have no idea how to deal with that... anyone?

---

### Post by Xian on 2005-07-26
[QUOTE=Copter]hi!

i have the same problem. sometimes it just crashes

```

copter@xidge:~$ sudo kcontrol

```[/QUOTE]
Try $ kdesu kcontrol
You'll get some scrolling text and then a password window.

---

### Post by Copter on 2005-07-26
hi!

thnx 4 reply but i found what was the problem just a sec ago.

i messed it up while /home dir remounting after kubuntu reinstall. i move files there using _rescue_ boot from cd, thats why they all were owned by root.

i change the owner of ~/.kde/share/config/ files to copter and everything works fine again. i can use control ceneter and enter admin mode now easly.

copter :]

---

### Post by MikeyXX on 2005-07-26
[QUOTE=Pcghost]I had this problem as well.  The way I fixed it was to type sudo kcontrol in a terminal and give your password.  That way it launches the control center in administrator mode from the get go.[/QUOTE]
 Problem with this method, is that if you change the login screen and then log the user out and back in, the ksplashrc file is locked (since it was updated by root privs) and the user gets an error until you manually go in and give the user the rights to that file. That was the first thing I came across. And that was only one change that was saved.

---

