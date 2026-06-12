---
title: "Can't shutdown from KDE"
date: 2005-07-08
forum: Desktop Environments
---

### Post by PiTT on 2005-07-08
Hi all,

I've installed Ubuntu Hoary, and then I did:
```
sudo apt-get install kubuntu-desktop
```

All went fine (expect for the kde i8n package for Brazilian Portuguese, I had to install it manually). However, I can't shutdown or reboot the computer from KDE! When I tell to exit, on the K menu, the only option there is to 'close session'... it them closes KDE and goes back to gdm, and only then I can shutdown or reboot the computer...

I went to the KDE control center, and the configuration there is correct, it says to offer shutdown and reboot options on that screen. But it doesn't.

Does this happen to anyone else?
Thanks a lot!

---

### Post by SGC on 2005-07-08
Its a normal thing, since youu are using GDM, you will not see restart/shutdown options in KDE

If you want those options you have to enable KDM, using the following command:
dpkg-reconfigure kdm

But then you will not have restart/shutdown options in gnome!

---

### Post by JPatrick on 2005-07-08
[QUOTE=SGC]But then you will not have restart/shutdown options in gnome![/QUOTE]

Is there anyway to set it so it's both?

---

### Post by PiTT on 2005-07-08
[QUOTE=SGC]
If you want those options you have to enable KDM, using the following command:
dpkg-reconfigure kdm
[/QUOTE]

Ok, I'll try that. I'm thining of switching to KDE for good anyway. But if I change my mind, how do I enable the use of gdm again? Is it as easy as dpkg-reconfigure gdm ?

Thanks!

---

### Post by apollo2011 on 2005-07-08
No you can't have it set to be able to shutdown from both Gnome and KDE.  The way it works, is that you have the Desktop Environment (Gnome, KDE, etc.) that controls the windows and the window decorations and the menus and everything.  Then you have a Desktop Manager (DM, as in *G*DM or *K*DM that controls the Desktop Environment, Login Screen, etc.  Because Gnome allows inegration with GDM and KDE allows integration with KDM, you can only have one Desktop Environment control the Desktop Manager because Gnome doesn't know how to talk to KDM and KDE doesn't know how to control GDM. 

Yes, it is very easy to switch between GDM and KDM as the default Desktop Manager.  any command of "dpkg-reconfigure <name odf desktop manager>" will invoke the same dialog.  If you run "dpkg-reconfigure kdm" or "dpkg-reconfigure gdm", you get the same screen that allows you to switch between either GDM or KDM or any other DM you have installed.  You can run the command again to swtich it back.

---

### Post by razor7 on 2005-08-20
Hello i get this problem...
 * Reloading K Display Manager configuration...                          [fail]
invoke-rc.d: initscript kdm, action "reload" failed.

Any help?

---

