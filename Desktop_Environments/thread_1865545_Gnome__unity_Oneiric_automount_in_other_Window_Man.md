---
title: "Gnome / unity Oneiric automount in other Window Manager"
date: 2011-10-20
forum: Desktop Environments
---

### Post by RMKrug on 2011-10-20
Hi

I installed Ubuntu Oneiric, but my main window manager is fluxbox. I used to be able to use the nautilus auto mounter to automount USB devices, but I don't managed after the upgrade. I resorted to installing thunar-volman, but as I have Unity / gnome installed, I would like to use the automounter from unioty or gnome. 

How can I achieve this? gnome-volume-manager does not exist in Oneiric, and nautilus -n does not reslut in automounting. Any suggestions?

Thanks,

Rainer

---

### Post by crdlb on 2011-10-20
GNOME's automounter is a plugin to gnome-settings-daemon now. It was moved out of nautilus since nautilus doesn't manage the desktop by default anymore (upstream).

---

### Post by RMKrug on 2011-10-21
Thanks - that explains.

Cheers,

Rainer

---

### Post by dfacto on 2011-10-23
So what is the preferred way to re-enable automount of USB drives?

---

### Post by crdlb on 2011-10-23
I wasn't completely correct in my previous post. In GNOME Shell, automounting is handled in the Shell process. For fallback mode, there is an automounter bundled with gnome-settings-daemon, but it isn't a plugin. There is an autostart file to run /usr/lib/gnome-settings-daemon/gnome-fallback-mount-helper in "GNOME3 unless-session gnome-shell", i.e. fallback mode and Unity.

So, I suspect you could just run that.

---

### Post by dfacto on 2011-10-24
I'm at work now, but when I get home I'll give something like this a try:
```

cp /etc/xdg/autostart/gnome-fallback-mount-helper.desktop ~/.config/autostart/
sudo service lightdm restart &

```

---

### Post by crdlb on 2011-10-24
> **dfacto said:**
> I'm at work now, but when I get home I'll give something like this a try:
```

cp /etc/xdg/autostart/gnome-fallback-mount-helper.desktop ~/.config/autostart/
sudo service lightdm restart &

```

You'll still need to remove the OnlyShowIn and AutostartCondition lines, and you need something in your session that supports the XDG autostart spec.

---

### Post by dfacto on 2011-10-24
What is the XDG autostart spec?

---

### Post by crdlb on 2011-10-24
> **dfacto said:**
> What is the XDG autostart spec?

[http://standards.freedesktop.org/autostart-spec/autostart-spec-latest.html](http://standards.freedesktop.org/autostart-spec/autostart-spec-latest.html)

It is the specification that makes putting a file in /etc/xdg/autostart/ or ~/.config/autostart/ have meaning.

P.S. It turns out that automounting was a plugin to g-s-d in 3.0, but it was moved to the Shell (and the fallback helper binary) for 3.2.

---

### Post by dfacto on 2011-10-25
Running
```

/usr/lib/gnome-settings-daemon/gnome-fallback-mount-helper

```
didn't do anything.  It also didn't print any events when I inserted the USB flash drive.

---

