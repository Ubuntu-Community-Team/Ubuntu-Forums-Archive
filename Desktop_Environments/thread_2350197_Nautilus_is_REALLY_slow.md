---
title: "Nautilus is REALLY slow"
date: 2017-01-22
forum: Desktop Environments
---

### Post by boldas2 on 2017-01-22
Hi everyone (...this is my first post on this forum!!)

I'm experiencing some trouble with Nautilus on Ubuntu 16.04....it has a really weird behavior and I don't know how to fix this!!

Basically what happens:

 when I click on the "Files" icon in the bar (the gray one with drawers..) it takes a LOOOONG time to open a window and most of the times it will NOT open and stay 'idle'... Actually the Files icon will be underlined with blue... but the program won't open. Sometimes I got a message "File Manager is taking a long time to open" and I have to choose between "Quit" or "Wait".... If I quit and then re-open it, most of the times it works.... anyway this is strange!!! If you got what I mean, it seems like Nautilus is "heavy" to open...while I would like it to be so quick anytime I need it!:(

Any hints or help?

Thanks
boldas:guitar:

---

### Post by DuckHook on 2017-01-22
Welcome to the forums boldas2,

What happens when you try opening Nautilus from the command line? When an app is misbehaving, it is useful to try from the command line so that you can see the errors generated. Please post them back to this thread.

---

### Post by boldas2 on 2017-01-23
Okay...! Do you mean something like this?


```
bolda@boldas-lap:~$ nautilus

(nautilus:3561): GLib-GIO-CRITICAL **: g_dbus_interface_skeleton_unexport: assertion 'interface_->priv->connections != NULL' failed

(nautilus:3561): GLib-GIO-CRITICAL **: g_dbus_interface_skeleton_unexport: assertion 'interface_->priv->connections != NULL' failed
Could not register the application: Timeout was reached

(nautilus:3561): Gtk-CRITICAL **: gtk_icon_theme_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(nautilus:3561): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(nautilus:3561): GLib-GObject-CRITICAL **: g_signal_connect_object: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed
```

---

### Post by DuckHook on 2017-01-23
> **boldas2 said:**
> Okay...! Do you mean something like this?
Yes.

They may look alarming, but most of those messages are warnings and not a big deal. They pop up on my nautilus session too and can be ignored.

The one item that isn't right is:
> **boldas2 said:**
> ```

Could not register the application: Timeout was reached
```
This could be the problem. Google produces the following hits:

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1290310](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1290310)
[http://askubuntu.com/questions/618171/nautilus-occasionally-stops-working](http://askubuntu.com/questions/618171/nautilus-occasionally-stops-working)
[https://ubuntuforums.org/showthread.php?t=2319175](https://ubuntuforums.org/showthread.php?t=2319175)

There were more, but the above seem the most relevant. A common element among those experiencing this problem is the use of *gvfs*:

[LIST=1]
[*]Have you installed any FUSE modules? Example: *ftp* or *exfat*?
[*]Do you have Windows shares mounted?
[*]Please post results of:```
ls -laF ~ | grep gvfs
``````
ls -laF ~/.gvfs
```
[/LIST]
In the meantime, as per the above links, there are several workarounds:

[LIST=1]
[*]Some report that logging out then logging back in helps, or
[*]```
killall nautilus
```…then relaunch it
[/LIST]
Let's review your answers to above questions first.

---

### Post by boldas2 on 2017-01-23
Hi DuckHook, so I will try to answer your questions here below...

> **DuckHook said:**
> A common element among those experiencing this problem is the use of *gvfs*:

[LIST=1]
[*]Have you installed any FUSE modules? Example: *ftp* or *exfat*? 
[*]Do you have Windows shares mounted? 
[*]Please post results of:```
ls -laF ~ | grep gvfs
``````
ls -laF ~/.gvfs
``` 
[/LIST]


1) mhm, good question. I guess no...but there is a way to check??

2) I use a virtual machine with Windows installed...

3) i never used that command...anyway this is what I got..

```
bolda@boldas-lap:~$ ls -laF ~ | grep gvfs
bolda@boldas-lap:~$ ls -laF ~/.gvfs
ls: cannot access '/home/bolda/.gvfs': No such file or directory
```

---

### Post by boldas2 on 2017-01-23
> **DuckHook said:**
> Yes.

They may look alarming, but most of those messages are warnings and not a big deal. They pop up on my nautilus session too and can be ignored.

The one item that isn't right is:

This could be the problem.


Sorry in the meanwhile I reinstalled Nautilus and NOW the results in Terminal are different! (there is no more THAT line!!!):

```
bolda@boldas-lap:~$ nautilus

(nautilus:10573): GLib-GIO-CRITICAL **: g_dbus_interface_skeleton_unexport: assertion 'interface_->priv->connections != NULL' failed

(nautilus:10573): GLib-GIO-CRITICAL **: g_dbus_interface_skeleton_unexport: assertion 'interface_->priv->connections != NULL' failed

(nautilus:10573): Gtk-CRITICAL **: gtk_icon_theme_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(nautilus:10573): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(nautilus:10573): GLib-GObject-CRITICAL **: g_signal_connect_object: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed


```

So, maybe the problem.... is solved! Nautilus seems quite responsive but I wait for singing victory....

Anyway, thanks for your help so far =d>

---

### Post by DuckHook on 2017-01-23
I strongly suspect that you may have solved the problem. That was the only line that was problematic. The others aren't a big deal.

If it continues to function well, then you can consider it solved:

*Please mark thread **solved** using *Thread Tools* in the top toolbar for the benefit of others searching for solutions*.

---

### Post by DuckHook on 2017-01-23
&#8230;and allow yourself to sing victory! :guitar:

---

### Post by boldas2 on 2017-01-24
Dear DuckHook... sorry, I'm afraid it was too early....but maybe I solved anyway. Today nautilus was back to being so much idle and slow...and I got this from terminal:

```
bolda@boldas-lap:~$ nautilus
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: mkdir failed on directory /var/run/samba/msg.lock: Permission denied
net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


```

after that, I installed samba (I found also helpful this thread [https://ubuntuforums.org/showthread.php?t=878321](https://ubuntuforums.org/showthread.php?t=878321) )

AND now it seems to be solved... but I will wait a few days before bringing my guitar and sing!!!

If you have any comment please post it, I am still wondering WHAT samba is and why should I get a sharing error from nautilus!

---

### Post by DuckHook on 2017-01-25
Though technically "solved", I can't help feeling that there is something very odd about your system. It should not be necessary to install samba. Samba is only needed if you map Windows shares. However, you do mention that you run Windows in a VM. I don't know what configuration changes you made to accommodate Windows. That may be what was tripping up Nautilus. And by installing Samba, you allowed Nautilus to connect with Windows as per Nautilus's "expectations". I have no idea what created those "expectations", but they are clearly now being fulfilled.

For an explanation of samba: [https://help.ubuntu.com/community/Samba](https://help.ubuntu.com/community/Samba)

Though I think curiosity is wonderful, I should let you know that my Windows knowledge is old and obsolete. Answers dealing with samba will have to come from other forum members.

If you want to chase this down further, you will have to give very detailed explanations of how exactly you installed your host OS, how you installed your Windows VM, what customizations you did, etc.

&#8230;or, you can just be happy that it's now working, play your guitar and sing! ;)

---

### Post by boldas2 on 2017-02-01
For me it's solved! Thanks a lto for your help DuckHook!! :)

boldas

---

