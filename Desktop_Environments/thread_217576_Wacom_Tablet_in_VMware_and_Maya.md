---
title: "Wacom Tablet in VMware and Maya"
date: 2006-07-17
forum: Desktop Environments
---

### Post by jujoje on 2006-07-17
Hi,

I've got a couple problems with my intuos 3 wacom tablet and I was hoping someone could point me in the right direction. 

The tablet works fine in dapper (pressure sensitivity in the gimp etc) However there are programmes which are giving me grief:

vmware:
I really want to get the tablet working in vmware (running windows 2K). I've added the usb devices, and my external hard drive shows up, but not the tablet. I read somewhere in the forums that this is due to vmware removing and then adding the devices to get them to show up in the virtual machine. Had a fiddle but not much luck yet.

maya:
Maya does not recognise the tablet and the stylus options in the paint tools are grayed out. I've done a search and apparently adding
```
Option "Mode" "Relative"
```
to xorg should get it working. It got relative mode working but still no luck with maya.

Has anyone had any luck getting either of these working? Any help would be apprecieted: having to use Zbrush in windows is the only thing keeping windows on my system, it's be nice to finally totally ditch windows :-)

---

### Post by jujoje on 2006-07-18
Doesn't anyone have any ideas?

Don't make me install windows (^_^)

---

### Post by genzo on 2006-08-13
*bump*

dont really use my wacom in maya, but i would like to have it working under vmware server tho..

edit: forgot to add that im using windows xp pro in vmware

edit2: k.. i've made some progress :)

remove the wacom entries in your xorg.conf and restart X
commented out the wacom udev rule in /etc/udev/rules.d/65-wacom.rules
did a modprobe -r wacom 
and plugged the tablet out and back in
edit your vmware image config file mine is called **Windows XP Professional.vmx** and add this line at the end:

> usb.generic.allowHID = "TRUE" 

reboot the vmware machine and enable the usb device.. it should be picked up... although it doesnt work perfectly for me.. in photoshop you can paint with pressure sensitivity but as soon as you go off the canvas the cursor jumps back to the mouse position ](*,)

---

