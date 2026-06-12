---
title: "Can't login to X"
date: 2011-01-31
forum: Desktop Environments
---

### Post by Lorem on 2011-01-31
Hi,

i have a problem with a 10.10 machine running on 64bit.
Since today I can't login via gdm (other ttys work fine)
When I enter the password, gdm disappears but after a second or so, it reappears without a reason being given.

Graphics cars is an ATI with fglrx running.
The disk isn't full.
I have copied xorg.conf.failsafe to xorg.conf; didn't help.
dpkg-reconfigure xserver-xorg didn't help, either.

Which logfiles should I read / post?

Thanks!

---

### Post by Forlong on 2011-01-31
Can you log into another session (I think there's a failsafe GNOME session)?

The logfile you are looking for is located at **/var/log/Xorg.0.log**

---

### Post by Lorem on 2011-02-01
No, I installed LXDE but that doesn't work either; will try Gnome Failsafe.

Logs are coming soon.

---

### Post by Lorem on 2011-02-01
$ grep -e EE -e WW /var/log/Xorg.0.log

    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  1544.827] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  1544.830] (II) Loading extension MIT-SCREEN-SAVER
[  1545.061] (WW) VESA(0): Unable to estimate virtual size
[  1545.365] (EE) GLX error: Can not get required symbols.
[  1545.574] (WW) SilverCrest MTS2219-SL: ignoring absolute axes.


Do you need the whole file?

---

### Post by Forlong on 2011-02-01
I can only guess there's some kind of problem with the fglrx driver.

Try uninstalling it for now:
```
sudo apt-get remove fglrx
```
and afterwards:
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
then reboot.

---

### Post by Lorem on 2011-02-02
Hi Forlong,

thanks for your help, but that doesn't help either.
Resolutions changed, but I still can't start a graphical session (neither gnome nor lxde).

Xorg.0.log changed a bit:

```
$ grep -e EE -e WW /var/log/Xorg.0.log
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    33.091] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    33.093] (II) Loading extension MIT-SCREEN-SAVER
[    33.129] (WW) Falling back to old probe method for vesa
[    33.129] (WW) Falling back to old probe method for fbdev
[    34.326] (WW) SilverCrest MTS2219-SL: ignoring absolute axes.
```

---

### Post by Forlong on 2011-02-02
Are you at least able to log into the "Recovery Console" session?

Another log to check would be **~/.xsession-errors** after the login failed.

---

### Post by Lorem on 2011-02-03
If you mean "Recovery Console" in GRUB, I then selected FailsafeX - didn't work, same procedure as every year. TIME! Sorry. Same procedure as every time.
But as you know, non-graphical terminal logins (such as TTY2 after CTRL+ALT+F2) do work.

This is .xsession-error after trying to login after a normal boot:
```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=de_DE.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
/home/elias/.gnupg/gpg-agent-info-elias-desktop: 1: Syntax error: word unexpected (expecting ")")
```

---

### Post by Forlong on 2011-02-04
No, I meant the recovery console session in GDM. But I have to tell you, this doesn't look like a trivial problem to me. You should file a bugreport about this and don't forget to add all the info you provided here.

Best of luck.

---

### Post by Lorem on 2011-02-06
Thanks!
But I reinstalled Maverick; Now everything works perfect again.

Thanks again for your help!

See you

---

