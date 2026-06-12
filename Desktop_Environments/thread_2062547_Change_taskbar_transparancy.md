---
title: "Change taskbar transparancy"
date: 2012-09-25
forum: Desktop Environments
---

### Post by DeceptiveHornet on 2012-09-25
Hello,

I've just made a permanent migration to the Kubuntu flavour of Linux and have to say that i love it. There's just one thing that i can't figure out how to do and that is how to remove the transparancy of the Taskbar. The text of open programs blends to well in with the wallpaper that is visible through and it's a strain on the eyes. I just want it to be ... well, non-transparent LOL.

Any idea on how to go about making this happen?

Edit: I am using the default KDE of Kubuntu 12.04.1 download.

---

### Post by bra|10n on 2012-09-25
You could address this issue a number of ways, as you say by decreasing the transparency of the panel or by changing the colour of the text. 
You might even consider changing plasma themes altogether also. 
Another way is to remove *task-manager* from the panel and add *icon-only-task-manager* for a more windows like approach without any text.
To change the transparency you would need to edit the *panel-background.svgz* image found within the theme, (/usr/share/kde4/apps/desktopthemes/default/widgets/transparent). 
You might check if another panel-background.svgz image exists in .../default/widgets/*opaque*, and if so you could copy that image to .../widgets/transparent thus replacing the original. 
If you wanted to darken the text, the file containing colour settings is the .colors file, (/usr/share/kde4/apps/desktopthemes/default).

Feel free to ask if you need any more help...

---

### Post by Erik1984 on 2012-09-25
This is an issue for me as well, 'solved' it by using Androbit as my desktop theme. It colors your widgets dark too but that's not a problem for me. On Androbit (and other dark themes like Caledonia) I find text remains readable regardless of the background.

---

### Post by kio_http on 2012-09-25
System Settings > Workspace Appearance > Desktop Theme > Get hot new stuff

Download a theme with a non transparent taskbar.

Note: In System settings > Desktop effects > Enable and Disable blur in case it is not working properly. It is supposed to blur the transparent taskbar like in Windows 7.

---

