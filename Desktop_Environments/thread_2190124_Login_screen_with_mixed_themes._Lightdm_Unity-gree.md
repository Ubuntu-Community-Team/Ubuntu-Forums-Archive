---
title: "Login screen with mixed themes. Lightdm? Unity-greeter?"
date: 2013-11-25
forum: Desktop Environments
---

### Post by papibe on 2013-11-25
Hi all

My login screen on my laptop running 12.04 got this ugly login screen where mostly looks OK, except it has parts that looks like 'High Contrast Inverse' theme.

Also, no matter what wallpaper I set, only the default background shows at login.

I'm using the Nvidia driver 319.32.

I appreciate any help.
Thanks in advance.

---

### Post by mc4man on 2013-11-26
there was a time that the inability to see a custom greeter bg could be affected by not having read permission for 'others' on a certain folder/file(s) within but I don't think that's the case in 12.04.3
So per usual if you create a new user does that user get a custom greeter?

If so then check that for your user if the gnome.settings-daemon background plugin is set to active
(in dconf-editor it's org.gnome.settings-daemon.plugins.background
or
gsettings set org.gnome.settings-daemon.plugins.background active true

---

### Post by papibe on 2013-11-26
Thanks mc4man, I appreciate your help.
> **mc4man said:**
> if you create a new user does that user get a custom greeter?
Yes. All new users get the same mismatched greeter, and no effect when they change their background.

> **mc4man said:**
> If so then check that for your user if the gnome.settings-daemon background plugin is set to active
(in dconf-editor it's org.gnome.settings-daemon.plugins.background
or
gsettings set org.gnome.settings-daemon.plugins.background active true
It is active with priority=97  :(

I've also ran:
```
sudo dpkg-reconfigure lightdm

sudo dpkg-reconfigure unity-greeter
```
with no effect.

Any other ideas?
Thanks.

---

### Post by mc4man on 2013-11-26
I mainly use 14.04 which isn't all that different (other than the gnome-setting-daemon plugin isn't used anymore.

Anyway have a 12.04 install on another machine so tried to break getting a custom greeter bg to no avail. (other than disabling that g-s-d plugin.
So maybe both of your issues are interrelated - have you tried returning to nouveau to see if either or both disappear. (if so I'd switch bg's after 1st login

Otherwise you could ck. a few places though I'd think they're ok - 
.cache/wallpaper should have an image of current bg
.config/gnome-control-center/backgrounds should have an xml listing current bg
gsettings get org.gnome.desktop.background picture-uri  # should list current bg

Have you read thru /var/log/lightdm/x-0-greeter.log, it usually will show an initial set to ../warty-final-ubuntu.png then switching to actual bg image
(that log can only be read as root

---

### Post by papibe on 2013-11-26
> **mc4man said:**
> 
.cache/wallpaper should have an image of current bg
.config/gnome-control-center/backgrounds should have an xml listing current bg
gsettings get org.gnome.desktop.background picture-uri  # should list current bg
All of those are showing the current desktop background (which is the correct one).

> **mc4man said:**
> Have you read thru /var/log/lightdm/x-0-greeter.log, it usually will show an initial set to ../warty-final-ubuntu.png then switching to actual bg image
(that log can only be read as root

Here's my [x-0-greeter.log]("http://paste.ubuntu.com/6482506/"). There are several errors, but I check on my main desktop (greeter is fine), and there also several errors. I wouldn't know which would point me in the right direction. Although, there's no mention of the current background after the default one (warty something).

Thanks for your time.
Regards

---

### Post by papibe on 2013-11-26
> **mc4man said:**
> have you tried returning to nouveau to see if either or both disappear. (if so I'd switch bg's after 1st login
Just did. Same frankestein greeter even after change bg and restart :(

Regards.

---

### Post by mc4man on 2013-11-27
Atm, basically no clue.
My log is quite similar to a point. After  that here the  custom greeter bg is eventually set, yours never revisits the bg 
If curious - [http://paste.ubuntu.com/6482682/](http://paste.ubuntu.com/6482682/)
mid 40 thru line 65 quite similar, then not so thru finishing user auth..

The only other diff I see is you have XBMC, could that somehow be affecting?
Also the blue in your screenshot seems out of place & not ubuntu-like, any idea why you have that?

---

### Post by papibe on 2013-11-30
Thanks for your thoughts.

The problem presented itself before I installed XBMC.

Regards.

---

### Post by steeldriver on 2013-12-01
For the high contrast problem, have you played with the accessibility settings (the little stick man indicator in the greeter screen top bar)? What does

```
sudo su -s /bin/sh lightdm -c 'dbus-launch --exit-with-session gsettings get com.canonical.unity-greeter high-contrast'
```

say?

---

### Post by papibe on 2013-12-07
```
$ sudo su -s /bin/sh lightdm -c 'dbus-launch --exit-with-session gsettings get com.canonical.unity-greeter high-contrast'
No protocol specified
No protocol specified
true

```
Thanks steeldriver for your help.

Regards.

---

### Post by papibe on 2013-12-07
> **steeldriver said:**
> have you played with the accessibility settings (the little stick man indicator in the greeter screen top bar)?
Holy Moly!! That was it, high contrast was selected in there :rolleyes:

Thank you :D steeldriver.
Kind Regards.

---

