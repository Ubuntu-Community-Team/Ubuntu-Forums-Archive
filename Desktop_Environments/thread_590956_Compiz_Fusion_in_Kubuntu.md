---
title: "Compiz Fusion in Kubuntu"
date: 2007-10-25
forum: Desktop Environments
---

### Post by kaiwan on 2007-10-25
Hi! 
I have installed ubuntu gutsy, and then KDE environment.
I know how to enable/disable compiz in Gnome, but where can
I do that in KDE?
Thanks

---

### Post by Shimmy on 2007-10-25
> **kaiwan said:**
> Hi! 
I have installed ubuntu gutsy, and then KDE environment.
I know how to enable/disable compiz in Gnome, but where can
I do that in KDE?
Thanks

I'm not sure, but you might try to install the compiz-kde package "sudo apt-get install compiz-kde".

---

### Post by bruno666 on 2007-10-25
You need at least these packages :

compiz-kde
compiz-settings-manager
emerald

Once they installed, you could launch compiz with the following command:

compiz --replace

---

### Post by kaiwan on 2007-10-25
I have installed emerald and compiz-kde, however I cant find package called compiz-settings-manager, but I have some settings manager for compiz that I installed in Gnome, it is called Advanced Desktop Effects Setting and it works fine in gnome. When I run compiz command I get 3D, but not all changes I do using  Advanced Desktop Effects Setting work like they do in gnome. In Gnome one can set the compiz effects level: none, normal, custom .. what I have now is normal level, but I cant fine where to set level to custom so I can change and add some effects

---

### Post by Luis Santos on 2007-10-25
I think the package is [FONT="Fixedsys"]compizconfig-settings-manager[/FONT] and not [FONT="Fixedsys"]compiz-settings-manager[/FONT].

---

### Post by magikx21 on 2007-10-25
I have it installed and to enable and disable it i use compiz --replace and kwin --replace but this seems to cause some issues. Is there a cleaner way to go about this?

---

### Post by mindtrick on 2007-10-25
Did you install video drivers ? It won't run without 3d acceleration enabled.

---

### Post by magikx21 on 2007-10-25
No I have it installed and it works fine but I disable it in order to play games. When I try reenable it I typically end up having to restart a time or two to get my titlebar back and everything running proper again.

---

### Post by mindtrick on 2007-10-27
Search for Compiz fusion icon, it's an icon that sits on the tray gives you options to do those things in right click menu.

---

### Post by Sain on 2007-10-27
I can't understand why Kubuntu didn't get  "Desktop effects"  properties like Ubuntu did.....

I understand that it hasn't made it into Fiesty,  but Gutsy? Ubuntu and Kubuntu should be projects of the same importance (and  it is always stated that they are). How's Xubuntu? I imagine it has just reached Ubuntu Dapper era... :-/

---

### Post by magikx21 on 2007-10-27
I haven't got a compiz fusion icon.

Sain, just wait till Hardy I'm sure Kubuntu will be even further behind since it wil be busy working with KDE4.

---

### Post by usp8riot on 2007-10-27
It's dependent upon funding. They do a well enough job with Kubuntu considering the resources, imho. 

When you install the Compiz settings, they should be in settings....advanced desktop effects settings. KDE has just as much eye candy as gnome.

---

