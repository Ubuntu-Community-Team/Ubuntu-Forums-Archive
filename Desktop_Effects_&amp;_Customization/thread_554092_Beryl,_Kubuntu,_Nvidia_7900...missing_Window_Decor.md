---
title: "Beryl, Kubuntu, Nvidia 7900...missing Window Decorations"
date: 2007-09-18
forum: Desktop Effects &amp; Customization
---

### Post by milspec on 2007-09-18
Hello!

Let me preface by saying I'm definately a noob trying to find his way in the linux world.  I've installed kubuntu and beryl before on other computers and it has always been relatively simple.  I followed the same procedure on my laptop and it just won't work properly.  

I installed my nvidia 7900 drivers through envy.  I installed the desktop effects package, beryl,and beryl manager.  When I load beryl manager, everything comes up but I instantly lose my window decorations.  If I click on the beryl manager and change my window manager to KDE then everything comes back but the cube stops working.  

If I load beryl from a console I get some odd messages.  I'm at my wits end!!  I've been pouring through forums and found people that seemed to have similar problems but I haven't found anyone with a solution that worked.  

I tried reinstalling the OS yesterday and downloaded the latest feisty fawn distro.  I also have the latest nvidia drivers courtesy of envy. 

I know I'm new to linux so I very well may be missing something totally obvious.  I'm posting because i've tried everything I can find and nothing seemed to help.

Thanks!!

tcampbell@TC9400:~$ beryl-manager
tcampbell@TC9400:~$ X Error: BadDevice, invalid or uninitialized input device 170
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 170
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

(beryl-manager:7289): Gtk-CRITICAL **: gtk_check_menu_item_set_active: assertion `GTK_IS_CHECK_MENU_ITEM (check_menu_item)' failed
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
X Error: BadDevice, invalid or uninitialized input device 170
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Checking maximum texture size                   : passed (4096x4096)

X Error: BadDevice, invalid or uninitialized input device 170
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Relaunching beryl with __GL_YIELD="NOTHING"
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (4096x4096)

Reloading options
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32

---

### Post by milspec on 2007-09-18
Quick update:

On a co-workers advice I upped my color depth to 32 bit and I now have my window decorations.  I can't get the beryl manager to load on startup though.  I've saved my session and each time I reboot I have to go to console and type beryl-manager.  

I think it has something to do with the errors I get.  Here's what it looks like now:

tcampbell@TC9400:~$ beryl-manager
tcampbell@TC9400:~$ X Error: BadDevice, invalid or uninitialized input device 170
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 170
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

(beryl-manager:6218): Gtk-CRITICAL **: gtk_check_menu_item_set_active: assertion `GTK_IS_CHECK_MENU_ITEM (check_menu_item)' failed

---

### Post by milspec on 2007-09-19
*bump*

---

### Post by cdekter on 2007-09-19
Can you post your xorg.conf?

---

