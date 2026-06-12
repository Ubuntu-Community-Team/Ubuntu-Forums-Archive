---
title: "Gnome refuses to run"
date: 2008-07-28
forum: Desktop Environments
---

### Post by devnull3d on 2008-07-28
I don't remember what I actually did, I just rebooted and after I logged on a popup came up saying;

```


Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace. Try logging in with one of the failsafe sessions to see if you can fix this problem


The ~/.xsession-errors file;

```
```


/etc/gdm/PreSessionDefault: Registring your session with wtmp and utmp
/etc/gdm/PreSessionDefault: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ':0' 'username'
/etc/gdm/Xsession: Beginning session startup

(process:4794): Gtk-WARNING **: This process is currently running setuid or setgid
This is not a supported use for GTK+. You must create a helper program instead. For further detauls, see :

http://www.gtk.org/setuid.html

Refusing to initialize GTK+


```
Apart from that GTK error which I found out it's nothing serious and shouldn't be the issue for gnome to fail to load, there are no other errors.
I have tried removing the .ICEAuthority file in my ~ but it's pointless. Because I added a new user from console and even that user couldn't logged on, with the same error.

I have a gut feeling that this is because of CrossOver as CrossOver applications didn't run before I rebooted which is why I rebooted in the first place.

I can however logon to Gnome Failsafe but it logs on pretty slow, hanging on "Loading windows" but it does load
I also tried reconfiguring X but I believe it's not an X problem but rather Gnome. I can run ratbox and fluxbox with no problem but I really do need Gnome to finish a college assignment due in 2 days.

Any advice in short time manner would be greatly appreciated.

Please refrain from posting links as my bandwidth limit is exceeded, it took a lot of time to even get here and post this message.

Thank you.

---

### Post by Qrikko on 2008-07-28
could you post the result of:
```

cat /var/log/Xorg.0.log | grep EE

```

and 

```

cat /var/log/Xorg.0.log | grep WW

```

---

### Post by devnull3d on 2008-07-28
erros
```

        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER

```
warnings
```

        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) `fonts.dir' not found (or not valid) in "/usr/X11R6/lib/X11/fonts/misc".
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) The directory "/usr/X11R6/lib/X11/fonts/cyrillic" does not exist.
(WW) The directory "/usr/X11R6/lib/X11/fonts/100dpi/" does not exist.
(WW) The directory "/usr/X11R6/lib/X11/fonts/75dpi/" does not exist.
(WW) The directory "/usr/share/fonts/X11/Type1" does not exist.
(WW) The directory "/usr/X11R6/lib/X11/fonts/Type1" does not exist.
(WW) The directory "/usr/X11R6/lib/X11/fonts/100dpi" does not exist.
(WW) The directory "/usr/X11R6/lib/X11/fonts/75dpi" does not exist.
(WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
(WW) NVIDIA(0): No valid modes for "1200x800"; removing.
(WW) NVIDIA(0): No valid modes for "1152x768"; removing.
(WW) NVIDIA(0): Option "UseFBDev" is not used

```
Thank you.
As I see the only issues I have are some fonts, which I highly doubt are the cause of the problem.

Here are the diff's from logs I think are important of before and I after I login to Gnome

```

poobox:/var/log# cat messages > /root/messages_before
poobox:/var/log# cat user.log > /root/user.log_before
poobox:/var/log# cat Xorg.0.log > /root/xorg.log_before
# I logged on here
poobox:/var/log# cat messages > /root/messages_after
poobox:/var/log# cat Xorg.0.log > /root/xorg.log_after
poobox:/var/log# cat user.log > /root/user.log_after
poobox:/var/log# cd
poobox:~# diff xorg.log_after xorg.log_before
439,453d438
< (II) Open ACPI successful (/var/run/acpid.socket)
< (II) APM registered successfully
< (II) NVIDIA(0): Initialized AGP GART.
< (II) NVIDIA(0): Setting mode "1280x800"
< (II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
< (II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
< (**) NVIDIA(0): DPMS enabled
< (==) RandR enabled
< (II) Initializing extension GLX
<     xkb_keycodes             { include "xfree86+aliases(qwerty)" };
<     xkb_types                { include "complete" };
<     xkb_compatibility        { include "complete" };
<     xkb_symbols              { include "pc(pc105)+us" };
<     xkb_geometry             { include "pc(pc104)" };
< (II) Configured Mouse: ps2EnableDataReporting: succeeded
poobox:~# diff user.log_after user.log_before
poobox:~# diff messages_after messages_before
poobox:~#

```

---

