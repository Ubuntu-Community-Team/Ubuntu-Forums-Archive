---
title: "gtk-update-icon-cache: The generated cache was invalid."
date: 2015-09-20
forum: Desktop Environments
---

### Post by ardouronerous on 2015-09-20
The icon theme I'm trying to install is Wine-Blue-Remix and it can be downloaded here: [http://gnome-look.org/content/show.php/Wine+Blue+Remix?content=158155](http://gnome-look.org/content/show.php/Wine+Blue+Remix?content=158155)

I love this icon theme, but I'm getting a warning from 'Setting -> Appearance -> Icons' that Wine-Blue-Remix-1.1.1 has no cache file, so I went to the Terminal as instructed and here's the results:

gtk-update-icon-cache /home/xxx/.icons/Wine-Blue-Remix-1.1.1/
gtk-update-icon-cache: The generated cache was invalid.

What seems to be the problem? I've installed other icon themes in the past and didn't encounter any problems generating the cache file. Can I use the icon theme even without a cache file?  Thanks.

---

### Post by ajgreeny on 2015-09-20
I have this icon theme installed but from the noobslab ppa repository, not direct from gnome-look.org, and I have exactly the same invalid cache problem.  It does not, however, stop the icon theme from being used, so I have tended to ignore the error without any further problems occurring.

This is not the first time I have seen this cache problem with icon themes, nor the first time the generated cache has been invalid, but the themes previously were not to my taste so I removed them and now can not remember which they were.

---

### Post by ardouronerous on 2015-09-20
Thanks, so there is no problems in just ignoring the 'Warning: this icon theme has no cache file', then?  What does the 'icon-theme.cache' do anyway?

---

### Post by ajgreeny on 2015-09-20
To be honest, I have no idea what it does; it doesn't seem to present a problem if it's missing.

---

### Post by buzzingrobot on 2015-09-20
There's an obscure GTK command, whose name I forget, that will generate the cache. Perhaps the install script didn't call it.

---

### Post by ardouronerous on 2015-09-21
Okay, I just went ahead and I'm now using the icon theme, I'm using this in combination with the **Ambiance-**[B]Xfce-LXDE theme, and my desktop looks great!:D
I just hope ignoring the icon theme no cache file warning doesn't bork my system.
[/B]

---

