---
title: "Unable to get sound working in Openbox on 9.04"
date: 2009-05-16
forum: Desktop Environments
---

### Post by Pixel on 2009-05-16
On a fresh install I went ahead and setup Openbox, from the get go I hadn o sound whatsoever, so I tried to load gnome-settings-daemon to see if that would get it working, and I got this error:

```

kyager@mobilebox:~$ gnome-settings-daemon

(process:3812): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.

** (gnome-settings-daemon:3813): WARNING **: Failed to acquire org.gnome.SettingsDaemon

** (gnome-settings-daemon:3813): WARNING **: Could not acquire name

```I also tried alsamixer and got this:
```

kyager@mobilebox:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such file or directory

```And aplay -l
```

kyager@mobilebox:~$ aplay -l
aplay: device_list:217: no soundcards found...

```However, if I run alsamixer or aply -l as root they run just fine and show everything as it should be.

I'm running this on a Lenovo IdeaPad y430, everything works perfectly in gnome on this same user and machine, but not in openbox.

---

### Post by octobuntu on 2009-06-04
I'm a total openbox noob,

---

### Post by octobuntu on 2009-06-04
:D I'm a total openbox noob, in fact I'm looking for the same answer so forgive me if I sound stupid, but shouldn't you just sudo apt-get install alsa-utils again?

---

### Post by munozga on 2009-07-18
@Pixel: Your command-line usage was on the right track to finding out the problem. I immediately noticed in your output that this was a permissions problem.

I confirmed that I in fact did not have permissions to read or write to the sound card as my normal USER by running ```
ls -l /dev/snd/*
```. I was not part of the `audio' group (```
grep audio /etc/group
```). So here's how to add yourself to the audio group without destroying any of the other group settings for your user. Simply do this as root:
```
# usermod -aG audio USER
```

Now, be sure to include the -a switch, because then this command appends your name to the audio group, otherwise this command would remove you from all of your existing groups and adding only to the audio group (probably unleashing major Ubuntu fu on your system).

You must log out and log back in for group settings to take effect.

This got sound to work with openbox on my system. Enjoy.

---

### Post by ~sHyLoCk~ on 2009-07-18
gnome-settings-daemon isn't there by default in openbox! Are you using it with gnome?

---

### Post by Jose Catre-Vandis on 2010-03-28
> **munozga said:**
> @Pixel: Your command-line usage was on the right track to finding out the problem. I immediately noticed in your output that this was a permissions problem.

I confirmed that I in fact did not have permissions to read or write to the sound card as my normal USER by running ```
ls -l /dev/snd/*
```. I was not part of the `audio' group (```
grep audio /etc/group
```). So here's how to add yourself to the audio group without destroying any of the other group settings for your user. Simply do this as root:
```
# usermod -aG audio USER
```

Now, be sure to include the -a switch, because then this command appends your name to the audio group, otherwise this command would remove you from all of your existing groups and adding only to the audio group (probably unleashing major Ubuntu fu on your system).

You must log out and log back in for group settings to take effect.

This got sound to work with openbox on my system. Enjoy.

Thanks for this, sorted out my openbox sound on Acer Aspire One. it worked fine in CLI mode, though?

---

