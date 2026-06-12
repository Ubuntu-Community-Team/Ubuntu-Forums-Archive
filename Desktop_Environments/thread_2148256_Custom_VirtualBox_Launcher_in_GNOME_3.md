---
title: "Custom VirtualBox Launcher in GNOME 3"
date: 2013-05-24
forum: Desktop Environments
---

### Post by warnellg on 2013-05-24
I'm using Ubuntu 13.04 with GNOME 3.  My goal is to create a custom launcher that will launch a VirtualBox virtual machine, and I'd like it to have it's own icon.

From a purely functional standpoint, I've been successful.  [This article]("http://www.webupd8.org/2009/07/create-shortcut-to-launch-virtual.html") (webupd8.org) gave me a command that directly launches a virtual machine.  So I created a new .desktop file in ~/.local/share/applications that uses that command for the 'Exec' portion.  When I click the launcher, the machine successfully launches.

My problem is with the icon behavior.  I specified a custom icon in the .desktop file, and it shows up beautifully in my favorites bar.  However, when I click the icon and the virtual machine starts up, the newly-opened window isn't associate with my custom launcher (i.e., my custom icon isn't "highlighted").  Instead, the window becomes associated with a newly-created VirtualBox icon.

Does anyone know if there's a way to indicate to GNOME 3 that I want to associate the new window with my custom icon?  I remember having a similar issue with Matlab and specifying something called "StartupWMClass" in the .desktop file, but I don't know what I should set the value to in this case (or if that even applies for a non-Matlab launcher).

Here's my .desktop file in case anyone thinks it might prove useful:

```
[Desktop Entry]
Name=Windows 8
GenericName=Windows 8 Virtual Machine
Comment=Windows 8 in VirtualBox
Exec=VBoxManage startvm 'Windows 8'
Icon=/home/warnellg/Pictures/Icons/Windows8.png
Terminal=false
Type=Application
Categories=Office;

```
Thanks!

---

### Post by deadflowr on 2013-05-24
Instead of "vboxmanage startvm" in the exec command, try simply "virtualbox --startvm".

---

### Post by warnellg on 2013-05-25
I'm not sure what the reasoning was behind that suggestion, but replacing the Exec command didn't help.  Remember, the issue isn't that I can't get the virtual machine to start, it's that I don't have the desired behavior with the icon association.  As far as I can tell, only one application is launched with either Exec command.

Still, I have made a little bit of progress since my last post.  I tried adding ```
StartupWMClass=VirtualBox
``` to the .desktop file, but that doesn't appear to have any affect.  If I rename the .desktop file to ```
virtualbox.desktop
```, I do get the behavior I want.  I think that just amounts to overwriting the "standard" VirtualBox launcher, though, because now it no longer appears in GNOME.

Ideally, I'd like to have both launchers, so I'm still in search of a complete solution.  Does anyone have any other suggestions?

Thanks!

---

### Post by deadflowr on 2013-05-25
It seems the behavior is in gnome-shell only.
I can't replicate it in other desktops.
Unity runs as you would want it, as does classic gnome.

I'll look further to see what's causing the issue.

---

### Post by markbl on 2013-05-25
wernellg, I remember trying to do exactly this some time ago but I never worked it out. If you find a solution then please come back here and tell us.

---

### Post by Julian_Seewald on 2013-08-23
im stil strugling wiht this

playing a little bit, I found a workaround, maybe it's not the best option for u, as it's not for me, but it's the best i could found.

i did as [COLOR=#000000]warnellg suggested and renamed the .desktop file to virtualbox.desktop, overriding the original VirtualBox UI launcher, with my own icon. 

now the original Virtualbox launcher launches my prefered VBM with my own icon, and not the VirtualBox UI.

i added the following lines to the bottom of the .desktop file:

[/COLOR]> Actions = VirtualBoxUI;


[Desktop Action VirtualBoxUI]
Name = Start VirtualBox UI
Exec = virtualbox
OnlyShowIn = Unity;



adding this lines allow you to right click on the launcher icon and the "Start VirtualBox UI" option will appear (similar to the "Start Incognito" option in Chrome/Chromium), allowing you to launch the VB UI, from the same icon u launch your prefered VBM. You can do the same with another VBM and add as many as u want.

The only undesired behavior from this is that u only have ONE icon for all the VBMs / VB UI (What i ideally wanted is each VBM to have it's own launcher and stay there, still couldn find it)

hope it helps

sory about my english

---

