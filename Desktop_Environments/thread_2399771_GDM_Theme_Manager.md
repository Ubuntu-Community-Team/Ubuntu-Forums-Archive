---
title: "GDM Theme Manager"
date: 2018-08-29
forum: Desktop Environments
---

### Post by the++abe on 2018-08-29
Hey guys, hopefully you are doing well :) I want to change my login screen and lock screen "the greeter" from what Ubuntu is forcing me to use to something else more specifically to my preferred theme, which is Equilex-Compact, but so far I have found no application for doing this task and it sounds like there is no way for doing this.
It be great if you guys get this problem solved for me :)
Thanks

---

### Post by Frogs Hair on 2018-08-29
Hello and Welcome !

I've not tested this, but it may be worth a try. See the screen-shots. There is a .deb package link.  

 [https://github.com/juhaku/loginized](https://github.com/juhaku/loginized)

---

### Post by the++abe on 2018-08-29
Thanks dude, I've tried this, it does not change the theme, this only has the "default" option in theme section, I was hoping for some option for my preferred theme..But nothing, I see the files "gnome-shell.css" and "gnome-shell-theme.gresource.xml" in the folder of Equilex theme but I have no idea where should I move these files to..In order to get rid of this Ubuntu greeter :)
Thanks a lot man for trying to help .

---

### Post by Frogs Hair on 2018-08-29
The panel is auto started with a script in usr/share/gdm/ greeter/applications though I have no idea how to change the default .

---

### Post by logix2 on 2018-08-29
It works fine for me, here's a screenshot with a list of themes displayed by Loginized: [https://i.imgur.com/1SyPmGD.png](https://i.imgur.com/1SyPmGD.png) Not all themes support theming GDM - you may want to read the Loginized [wiki]("https://github.com/juhaku/loginized/wiki/Help") for more about that.

---

### Post by the++abe on 2018-08-29
It does not work, after a fresh installation of Ubuntu, I tried this, what the wiki says about compiling the folder "gnome-shell" and the folder "gnome-shell" does exist in Equilux Theme, but I would only receive error.
this was the command line which I used
[COLOR=#24292E][FONT=-apple-system]loginized-cli compile /usr/share/themes/Equilux-compact/gnome-shell/ /usr/share/themes/Equilux-compact/gnome-shell/
[/FONT][/COLOR]
and this is the error which I received.

/usr/bin/loginized-cli:line 162:/usr/share/themes/Equilux/gnome-shell/gnome-shell-theme.gresource.xml:Permission denied
/usr/bin/loginized-cli:line 164: glib-compile-resources: command not found
cp: cannot stat'/usr/share/themes/Equilux/gnome-shell/gnome-shell-theme.gresource':No such file or directory


 and yeah I ran the app from Terminal to check and see of there is any dependency required, there were 3 and I downloaded them before doing this..But nothing worked.

---

### Post by Frogs Hair on 2018-08-29
You need elevated permission to create the gnome shell folder in usr/share/themes/Equilux. You can use ```
sudo-H nautilus
``` and navigate to the theme folder to add the new directory.

---

### Post by the++abe on 2018-08-30
Okay I should have added that "gnome-shell" folder does indeed exist in the theme's folder, so there is no need for creating a new folder there, but that was a good command line for a noob like me :D I could do anything after running it, thanks a lot, but it could not do much since the folder already existed, then I got grumpy and changed gnome-shell-theme.gresource.xml" file which already existed that folder to gnome-shell-theme.gresource" and after that restarted the machine and opened Loginized and Loginized recognized the them...I chose the theme and restarted and the system never came up :)

---

### Post by the++abe on 2018-08-30
I have found the way
[COLOR=#1C1C1C][FONT=&amp]sudo apt install libglib2.0-dev libxml2-utils (needed packages)[/FONT][/COLOR]
[COLOR=#1C1C1C][FONT=&amp]sudo cp -av /usr/share/gnome-shell/gnome-shell-theme.gresource{,~} (backup previous)[/FONT][/COLOR]
[COLOR=#1C1C1C][FONT=&amp]sudo cp -av /usr/share/gnome-shell/theme/ubuntu.css{,~} (backup previous)[/FONT][/COLOR]
[COLOR=#1C1C1C][FONT=&amp]Select a [FONT=inherit]GTK+[/FONT] theme to decide which variant to install. (gnome tweaks)[/FONT][/COLOR]
[COLOR=#1C1C1C][FONT=&amp]GTK_THEME=$(gsettings get org.gnome.desktop.interface gtk-theme | sed "s/'//g")[/FONT][/COLOR]
[COLOR=#1C1C1C][FONT=&amp]cd /usr/share/themes/${GTK_THEME}/gnome-shell[/FONT][/COLOR]
[COLOR=#1C1C1C][FONT=&amp]sudo glib-compile-resources --target=/usr/share/gnome-shell/gnome-shell-theme.gresource gnome-shell-theme.gresource.xml[/FONT][/COLOR]
[COLOR=#1C1C1C][FONT=&amp]sudo cp -v gnome-shell.css /usr/share/gnome-shell/theme/ubuntu.css (all the above to compile and replace current theme)[/FONT][/COLOR]
[COLOR=#1C1C1C][FONT=&amp]Press *ALT+F2* and type *rt,* and press *ENTER*, or simply *reboot*.[/FONT][/COLOR]
[COLOR=#1C1C1C][FONT=&amp]If you want to revert changes, refer to the above link.[/FONT][/COLOR]
[COLOR=#1C1C1C][FONT=&amp]EDIT: Extra info. Every time the *gdm* package is updated, you must repeat the above procedure.[/FONT][/COLOR]

---

