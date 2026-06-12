---
title: "vnc to ubuntu 10.4 with vmware guest keyboard problem"
date: 2011-11-21
forum: Desktop Environments
---

### Post by charcosa on 2011-11-21
My '(' and ')', shift 9 and shift 0, keys do not function from within a vmware guest when I vnc into the ubuntu host. All other keys work.
 
I have an Ubuntu 10.4 desktop that hosts two vmware machines, one running ubuntu 10.4 and one running Windows 7. The desktop has an x11vncserver running. Both Ubuntu boxes use Gnome.
 
If I attach to the desktop via vnc, either UltraVnc from a Windows desktop or Remote Desktop Viewer from another Ubuntu box, the keys all work on the desktop host. I cannot type those two keys from within either vmware guest operating system. All other keys work in the guest operating systems.

---

### Post by charcosa on 2011-11-22
I did some additional searching and some experimentation. I found a couple of threads on a vmware thread which led to a solution.

[http://nthrbldyblg.blogspot.com/2008/06/vmware-and-fubar-keyboard-effect.html](http://nthrbldyblg.blogspot.com/2008/06/vmware-and-fubar-keyboard-effect.html)
[http://www.vmware.com/support/ws55/doc/ws_devices_keymap_linux_longer.html](http://www.vmware.com/support/ws55/doc/ws_devices_keymap_linux_longer.html)

The nthrbldyblg article led me to the information I needed. The solution for me was to use xev to find keycode events, to read about them in the vmware link, and to add the following lines in my ubuntu host  /etc/vmware/config file. That said, this solution worked completely for my Ubuntu guest and for the () on my Windows 7 guest. I found that it did not resolve the < key in my Windows 7 guest that was also unresolved in the blog listed above. I tried the commented line with keycode 94 but no help. I will continue with the windows issue as time permits.

xkeymap.usekeycodeMapIfXFree86 = true 
xkeymap.keycode.187 = 0x00a
xkeymap.keycode.188 = 0x00b
#xkeymap.keycode.94 = 0x033

---

