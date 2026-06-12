---
title: "Customizable 10.04 netbook launcher in 10.10"
date: 2010-10-24
forum: Desktop Environments
---

### Post by Skaarg on 2010-10-24
I know some people have complained about Unity, myself included, well once I found out you could add the old launcher back using the Ubuntu Netbook Edition 2D session on GDM after installing a couple packages. The problem is it's still not configurable, but I found a fix modifying the old guide for 10.04.

Firstly if you haven't installed the packages do so:
sudo apt-get install ubuntu-netbook-efl-default-settings netbook-launcher-efl

Secondly the directories are slightly different from 10.04 since now Unity goes in "xdg-une".
sudo ln -s /etc/xdg/xdg-une-efl/autostart/maximus-autostart.desktop /etc/xdg/autostart/
sudo ln -s /etc/xdg/xdg-une-efl/autostart/netbook-launcher-efl.desktop /etc/xdg/autostart/
sudo ln -s /usr/share/gconf/une-efl/default/20_une-efl-gconf-default /usr/share/gconf/defaults/
sudo ln -s /usr/share/gconf/une-efl/mandatory/20_une-efl-gconf-mandatory /usr/share/gconf/defaults/
sudo update-gconf-defaults

Then logout of your current session or restart. Once at the login screen choose user and change session to Ubuntu Desktop Edition.

Once logged in you will have a mashup of the EFL netbook launcher and regular gnome. First remove the bottom panel to give you more screen space. Then remove the Menu Bar and shortcuts from the top panel and add Go Home and Window Picker to get the normal Netbook Launcher EFL feel, but with the freedom to customise as you wish.

It's not much, but I know I spent a good hour or so trying to find a guide, but ended up figuring things out on my own and learning a bit. :)

---

