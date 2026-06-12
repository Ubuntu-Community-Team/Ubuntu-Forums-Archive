---
title: "[SOLVED] Nautilus and Compiz Fusion"
date: 2008-04-16
forum: Desktop Effects &amp; Customization
---

### Post by geeree on 2008-04-16
I am using Compiz Fusion 0.6.3 and Nautilus 2.20.0 on my Gutsy laptop. I have noticed the following problem recently: Compiz manages all my windows very well, except the ones created for Nautilus. Nautilus windows will not get a border; it will be hard to minimise and maximise them; and they will flicker awfully whenever I'll do Alt+Tab for window selection. These problems vanish if I switch over to Metacity. 

Could someone explain what is happening? How can I correct this? 

Thanks,
Girish.

---

### Post by Zorael on 2008-04-16
Are you using gtk-window-decorator or emerald as your window decorator?

If you don't know what I'm talking about; are your window titlebars and borders themed as normal Ubuntu windows (using the [standard Gnome theme manager](http://geekgirlxx.files.wordpress.com/2007/11/murrina-personal.png)), or are you using the [Emerald Theme Manager](http://www.howtoforge.de/images/beryl_centos5.0/8.jpg) to apply your themes?

To see if things work better with emerald, enter the following in a terminal.
```
$ emerald --replace
```
If it complains about emerald not being installed, you need to install the **emerald** and **emerald-theme-manager** packages, either via the terminal or through Synaptic. The emerald themes that were available via the official repositories were never included in the Gutsy ones, but the [Feisty package](http://packages.ubuntu.com/feisty/emerald-themes) can be downloaded and installed manually.


To revert to gtk-window-decorator, enter the following.
```
$ gtk-window-decorator --replace
```

---

### Post by geeree on 2008-04-16
> **Zorael said:**
> Are you using gtk-window-decorator or emerald as your window decorator?

Thanks, Zorael. I forgot to mention that. I am using Emerald (version 0.3.0-svn). My problem goes away if I change to the gtk-window-decorator. Now can you tell me how I can get Nautilus behave straight? (Also, then, is this a problem with Compiz or Emerald---or Nautilus?)

> The emerald themes that were available via the official repositories were never included in the Gutsy ones, but the [Feisty package](http://packages.ubuntu.com/feisty/emerald-themes) can be downloaded and installed manually.


By the way, thanks for this nugget of information! I'd been wondering about the Emerald themes: [http://ubuntuforums.org/showthread.php?t=588086](http://ubuntuforums.org/showthread.php?t=588086).

Thanks,
Girish.

---

### Post by Zorael on 2008-04-16
> **geeree said:**
> I am using Emerald (version 0.3.0-svn). My problem goes away if I change to the gtk-window-decorator.

This may be a bug in the svn version you're using. Does it disappear if you revert to the one available from the official repositories?

This is a destructive change and the only way to change back to your earlier svn version would be to install it via whatever guide you used.

Disable any third-party repositories from Software Sources (or comment lines in **/etc/apt/sources.list** and relocate files in **/etc/apt/sources.list.d/**). At least temporarily; you can enable them afterwards if you want.

```
$ sudo apt-get autoremove --purge emerald* libemerald*
$ sudo apt-get clean
$ sudo apt-get update
$ sudo apt-get install emerald
```

---

### Post by geeree on 2008-04-16
> **Zorael said:**
> This may be a bug in the svn version you're using. Does it disappear if you revert to the one available from the official repositories?

I don't know, but I reinstalled the svn version using Synaptic---the svn version is available in the universe! I don't have any third-party repositories enabled---and everything's okay now!  

Thanks,
Girish.

---

