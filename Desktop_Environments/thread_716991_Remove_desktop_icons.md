---
title: "Remove desktop icons?"
date: 2008-03-06
forum: Desktop Environments
---

### Post by Freddy on 2008-03-06
Greeting all.

Please read the entire post before replaying 'search!' :)

I used the 'gconf-editor' to remove my mounted volumes desktop icons but they are still showing up, even after a reboot. Do Gnome/Nautilus use some other way of configuring this now a days?

Any help? I hate having them on my desktop.

/Thanks

---

### Post by logos34 on 2008-03-06
so, you have apps>nautilus>desktop>volumes_visible **unchecked **and the they still show up?

---

### Post by Bruce M. on 2008-03-06
> **logos34 said:**
> so, you have apps>nautilus>desktop>volumes_visible **unchecked **and the they still show up?

I asked the same thing, and was [told this]("http://ubuntuforums.org/showpost.php?p=4015338&postcount=1201") which matches what you said logos34, and it worked.

Strange.

---

### Post by Freddy on 2008-03-06
> **logos34 said:**
> so, you have apps>nautilus>desktop>volumes_visible **unchecked **and the they still show up?
Yup, I don't have a clue whats going on. Where is the text configuration file that you configure though gconf? Seems that something is wrong with my gconf.

---

### Post by Freddy on 2008-03-06
> **Bruce M. said:**
> I asked the same thing, and was [told]("http://ubuntuforums.org/showpost.php?p=4015338&postcount=1201") which matches what you said logos34, and it worked.

Strange.
Yeah I already knew that but somethings up with my gconf it seems :(.

---

### Post by jryprt on 2008-03-06
In a terminal type:

    gconf-editor

  Browse to apps > nautilus > preferences > show_desktop and unselect it.
  It removes all icons on the desktop

---

### Post by mdebusk on 2008-03-07
> **Freddy said:**
> Any help? I hate having them on my desktop.

What I did instead was mount the hard drive partitions under /mnt instead of /media . This keeps them from showing up on the desktop but still lets removable drives put an icon where I can see it.

---

### Post by Bruce M. on 2008-03-07
[CENTER]**I found this [post]("http://ubuntuforums.org/showpost.php?p=4444558&postcount=12") but I [B][COLOR="Red"]warn[/COLOR]** you:
It is for Xubuntu.[/B][/CENTER]

That post for Xubuntu says:
```

The file icon view by default shows 'special' icons for the root of your
filesystem, your home directory, and the trash. Removable volumes (such as
USB flash drives) are also shown when they are plugged in. If you'd like to
configure which of these are shown, edit (or create) the file
~/.config/xfce4/desktop/xfdesktoprc to look something like this:

[file-icons]
show-filesystem=true
show-home=true
show-trash=true
show-removable=true

The defaults are all 'true', but you can set ones you want hidden to 'false'.
If an entry is omitted, it defaults to 'true'. You will need to restart
xfdesktop to make the settings take effect.

```


However saying that, since your Config Editor isn't doing this for you maybe there is a GNOME file similar to this somewhere that someone might know about and will come to your aid. I recently switched to Xubuntu due to an older PC.

What we need in Xubuntu is a Config Editor like Gnome.  :)

Also try using this [Custom Google Search Engine]("http://crunchbang.org/ubuntu-search-engine/") for Ubuntu related sites.

Good luck in your quest, I'll be watching the thread.
Bruce

---

### Post by Freddy on 2008-03-07
> **mdebusk said:**
> What I did instead was mount the hard drive partitions under /mnt instead of /media . This keeps them from showing up on the desktop but still lets removable drives put an icon where I can see it.
Yeah I choose this solution too but I want to know what the heck is going on with my gconf editor :).

---

