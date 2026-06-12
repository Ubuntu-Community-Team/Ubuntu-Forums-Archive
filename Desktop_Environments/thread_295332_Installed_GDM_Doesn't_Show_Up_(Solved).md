---
title: "Installed GDM Doesn't Show Up (Solved)"
date: 2006-11-07
forum: Desktop Environments
---

### Post by Synikk on 2006-11-07
I've done a clean install of 6.10 and installed a GDM theme I was using on 6.06. However, despite that the GDM is in fact installed, it doesn't show up in the logon manager utility, thus I can't select it.

I ran a search on the forum but didn't find any relevant threads.

Help?

---

### Post by aysiu on 2006-11-07
It should show up immediately if you install it.

How did you install it (what steps did you take)?

---

### Post by Synikk on 2006-11-07
> **aysiu said:**
> It should show up immediately if you install it.

How did you install it (what steps did you take)?

I installed it via the Logon Manager utility, as I did in Dapper. It simply doesn't show up in the menu. The first time, I thought it didn't install, so I tried installing it again, but Logon Manager popped up a message saying the GDM theme was installed already!

I've also tried manually installing it in the /usr/var/gdm directory, but no go.

I'll try some other GDM themes and see if I get the same results.

---

### Post by aysiu on 2006-11-07
Mind posting a link to the offending theme?

---

### Post by Synikk on 2006-11-07
> **aysiu said:**
> Mind posting a link to the offending theme?

It's [this one]("http://www.gnome-look.org/content/show.php?content=31267").

---

### Post by aysiu on 2006-11-08
> **Synikk said:**
> It's [this one]("http://www.gnome-look.org/content/show.php?content=31267").
It's working fine for me.

I downloaded the theme.

Then in *gksudo gdmsetup*, I pressed **Add** (boxed in red) and then pressed the circle next to the theme (boxed in green), and it worked.

Maybe it's possible Firefox (or whatever browser you use) is set up to automatically extract .tar files instead of just downloading them? Or maybe you didn't blacken the circle next to the theme?

---

### Post by Synikk on 2006-11-08
> **aysiu said:**
> It's working fine for me.

I downloaded the theme.

Then in *gksudo gdmsetup*, I pressed **Add** (boxed in red) and then pressed the circle next to the theme (boxed in green), and it worked.

Maybe it's possible Firefox (or whatever browser you use) is set up to automatically extract .tar files instead of just downloading them? Or maybe you didn't blacken the circle next to the theme?

Hm, that's weird. See, when I installed the theme, it simply doesn't show up in the list. I'm going to have to go try this again, BRB.

---

### Post by aysiu on 2006-11-08
> **Synikk said:**
> Hm, that's weird. See, when I installed the theme, it simply doesn't show up in the list. I'm going to have to go try this again, BRB.
Since the GUI's not working out for you, how about trying it the command-line way?

Can you paste these commands in and see if it shows up in the list available themes? ```
wget -c http://www.gnome-look.org/content/files/31267-LiNsta-GDM-0.1.tar.gz
tar -xvzf 31267-LiNsta-GDM-0.1.tar.gz
sudo mv LiNsta-0.1 /usr/share/gdm/themes
gksudo gdmsetup
```

---

### Post by Synikk on 2006-11-08
Okay, this time I simply dragged the tarball to the window instead of clicking "Add" etc, and it WORKED. I have no idea why it wouln't install the other way. Strange glitch maybe?

Either way, thanks for prompting me to try it again.

---

