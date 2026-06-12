---
title: "making fluxbox act like it does in DamnSmall"
date: 2008-01-02
forum: Desktop Environments
---

### Post by Tyke91 on 2008-01-02
Hey, I was looking for something new and decided to give fluxbox another try. I was previously used to using the "Damn Small Linux" version of it, which comes with:
[LIST]
[*]nice Icons[/LIST][LIST]
[*] a cool app that gives you system stats as part of your desktop (kinda like a widget, but much more basic and minimal.[/LIST][LIST]
[*]and a simple way to change your desktop background[/LIST]
 How can I go about doing that with a fresh install of fluxbox from the repos (I've already read the howto on tweaking the menus, and it's turned out great).

---

### Post by rjmdomingo2003 on 2008-01-02
> **Tyke91 said:**
> Hey, I was looking for something new and decided to give fluxbox another try. I was previously used to using the "Damn Small Linux" version of it, which comes with:
[LIST]
[*]nice Icons[/LIST][LIST]
[*] a cool app that gives you system stats as part of your desktop (kinda like a widget, but much more basic and minimal.[/LIST][LIST]
[*]and a simple way to change your desktop background[/LIST]
 How can I go about doing that with a fresh install of fluxbox from the repos (I've already read the howto on tweaking the menus, and it's turned out great).
For icons, you can try idesk: [http://idesk.sourceforge.net/wiki/index.php/Main_Page](http://idesk.sourceforge.net/wiki/index.php/Main_Page)

For system stats, maybe conky: [http://ubuntuforums.org/showthread.php?t=205865&highlight=conkyrc](http://ubuntuforums.org/showthread.php?t=205865&highlight=conkyrc)

For changing desktop backgrounds, install feh & modify the flux menu for background change.

---

### Post by urukrama on 2008-01-02
If you like a graphical tool to change wallpapers, you can use Cwallpaper or Nitrogen. Have a look at your options [here]("http://urukrama.wordpress.com/2007/12/05/desktop-backgrounds-in-window-managers/").

---

### Post by Tyke91 on 2008-01-02
the wallpaper thing was not really the big issue, I've learned how to do it in the command line way, But I really miss the desktop Icons and the cool conky thing.
 I've tried conky, but I haven't gotten it to work yet.

---

### Post by p_quarles on 2008-01-02
Conky uses a script in your home folder to determine how it displays. You can load the sample script (comes with the Ubuntu package) by running this:
```
zcat /usr/share/doc/conky/examples/conkyrc.sample.gz > ~/.conkyrc
```
And, like rjdomingo said, you can get desktop icons with idesk. It's in the repositories. The configuration file for this is:
```
~/.ideskrc
```
Individual icons are defined by *foo*.lnk files in the ~/.idesktop directory.

---

### Post by mcduck on 2008-01-03
> **Tyke91 said:**
> 
[*] a cool app that gives you system stats as part of your desktop (kinda like a widget, but much more basic and minimal.

That's Gkrellm: [http://members.dslextreme.com/users/billw/gkrellm/gkrellm.html]("http://members.dslextreme.com/users/billw/gkrellm/gkrellm.html")

It's in Ubuntu repositories, so simple "sudo apt-get install gkrellm" is enough to get it installed :)

---

### Post by mojoman on 2008-01-03
> **Tyke91 said:**
> the wallpaper thing was not really the big issue, I've learned how to do it in the command line way, But I really miss the desktop Icons and the cool conky thing.
 I've tried conky, but I haven't gotten it to work yet.

Have a look at _[this thread]("http://ubuntuforums.org/showthread.php?t=281865&highlight=post+your+conky")_ for some tips on conky.

---

