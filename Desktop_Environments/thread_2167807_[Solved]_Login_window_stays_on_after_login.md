---
title: "[Solved] Login window stays on after login"
date: 2013-08-15
forum: Desktop Environments
---

### Post by lelol-0 on 2013-08-15
Hi there,

Following an update yesterday, everytime I login, the login screen + dots picture stay on over desktop.

I tried to restore to previous date, but, no chance !! (Note that everything works perfectly, though, apart from right click on desktop and / or changing wallpaper)

Hints anybody ??

Thanks !

[IMG]http://ismayotte.lautre.net/ubuntu.png[/IMG]

---

### Post by lelol-0 on 2013-08-15
Solved !

The desktop display was managed by Nemo which, for whatever reason, went berzek. So I went to use Nautilus as "default desktop manager". 

For that, I had to revert the modifications made &#8203;&#8203;when [installing]("http://linuxg.net/how-to-install-nemo-and-set-it-as-the-default-file-manager/")[ Nemo]("http://linuxg.net/how-to-install-nemo-and-set-it-as-the-default-file-manager/"). These mods were..:
```

$ xdg-mime default nemo.desktop inode/directory application/x-gnome-saved-search
$ gsettings set org.gnome.desktop.background show-desktop-icons false
$ gsettings set org.nemo.desktop show-desktop-icons true
```


Here is what I entered :
```

xdg-mime default nautilus.desktop inode/directory application/x-gnome-saved-search
gsettings reset org.gnome.desktop.background show-desktop-icons
```

Not sure it'll help, but I thought an explanation was a polite way to close the thread ! ;)

---

