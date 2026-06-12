---
title: "Gnome Issue with Blue Desktop and No Icons"
date: 2023-11-15
forum: Desktop Environments
---

### Post by giobaxx on 2023-11-15
Hello to everyone

If it is possible i need an help to fix an issue installing a software. The software installation didn't finish properly and is not even able to write the installation log file but mainly it breaks Gnome. I was auble to anything and after a reboot and the new login had a blue wallpaper without any icons like the one in this post: [https://askubuntu.com/questions/1358640/weird-gui-and-blue-desktop-background](https://askubuntu.com/questions/1358640/weird-gui-and-blue-desktop-background) .


I tried to remove ubuntu-desktop and all the gnome packages by 
[I]
[LIST]
[*]apt purge ubuntu-desktop gnome-*
[/LIST]
[/I]
reboot and reinstall them but nothing i still have the blue screen with no icons. what other can i try to fix gnome? 

About the application who generate the issue it was installed on an ubuntu 20.04 where was applied some hardening(i.e umask more restricted ) but as far as i uderstood the installer wrote to /opt/.... and install some icons and mime types.

I was trying to understand what could have happened and what part on the hardening generate this issue during the software installation but still not claire, but for the moment i have no clue

Any help is appreciated

A.

---

