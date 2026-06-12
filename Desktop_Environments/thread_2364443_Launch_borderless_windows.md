---
title: "Launch borderless windows"
date: 2017-06-23
forum: Desktop Environments
---

### Post by amivaleo on 2017-06-23
Hi,

How can I launch a borderless window in Gnome? I mean only specific unmaximized programs that do not use gtkheaderbars.
Is there a way to do that? Like adding some command in the program launcher?

I use ubuntu-gnome 16.04, gnome version is 3.20.4.

Thank you! :)

---

### Post by CatKiller on 2017-06-25
I'm on my phone, so I can't check whether this will work for you, but it might point you in the right direction.

[https://bbs.archlinux.org/viewtopic.php?id=192422](https://bbs.archlinux.org/viewtopic.php?id=192422)

---

### Post by yetimon_64 on 2017-06-28
> **amivaleo said:**
> Hi,

How can I launch a borderless window in Gnome? I mean only specific unmaximized programs that do not use gtkheaderbars.
Is there a way to do that? Like adding some command in the program launcher?

I use ubuntu-gnome 16.04, gnome version is 3.20.4.

Thank you! :)

You may want to check out the "gdevilspie" package for that. You can create rules for specific windows and remove window decorations, set geometry etc for such a window with it. The package uses the "devilspie" daemon to monitor for usage of such windows.

On 14.04 with either unity or xfce I use it to create gnome terminal windows without any window decorations. You should be able to do so with a specific window in gnome using it. On 16.04 the gdevilspie package still works here but due to changes in the gnome-terminal package, related to terminal profile naming, I can't do the same "trick" here; though other applications should still be controllable with it.

Good luck, yeti.

---

### Post by again? on 2017-06-30
The devilspie2 method suggested by yetimon should work.
(Tested in Ubuntu-Gnome 17.04)
```
sudo apt install devilspie2
```
Create a lua rule file.
```
gedit ~/.config/devilspie2/undecorate.lua
```
Copy and paste the following into undecorate.lua, replacing **ApplicationName** with your application.
```
if (get_application_name()=="**ApplicationName**") then
   undecorate_window();
end
```
Save and close.
Logout.

---

### Post by yetimon_64 on 2017-07-01
> **guber2 said:**
> The devilspie2 method suggested by yetimon should work...

Does that newer devilspie package (devilspie**2**) also work with the **g**devilspie GUI interface ? I am actually still using the older devilspie package with the GUI interface. May have to try and update a bit here if it does. 
Cheers, yeti.

---

### Post by again? on 2017-07-01
> **yetimon_64 said:**
> Does that newer devilspie package (devilspie**2**) also work with the **g**devilspie GUI interface ? I am actually still using the older devilspie package with the GUI interface. May have to try and update a bit here if it does. 
Cheers, yeti.
No, unfortunately. The config files are written in lua and don't work with gdevilspie/devilspie.
You can find examples in /usr/share/doc/devilspie2/README.gz or [https://github.com/gusnan/devilspie2](https://github.com/gusnan/devilspie2) 
Search online: eg [https://softsolder.com/2013/09/12/devilspie2-lua-scripts/](https://softsolder.com/2013/09/12/devilspie2-lua-scripts/)

Lua gives more config options but for what the OP wants gdevilspie/devilspie may be easier.

---

