---
title: "Copy and paste in VMware Jaunty Jackalope"
date: 2009-06-21
forum: General Help
---

### Post by Zorrorrorro on 2009-06-21
I think I installed vmware tools properly to allow copy and paste between host and guest OS, but when I type in the command "vmware-toolbox &" I get the following:

edward@edward-desktop:~$ vmware-toolbox &
[1] 12860
edward@edward-desktop:~$ vmware-toolbox &Gtk-Message: Failed to load module "canberra-gtk-module": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory

(vmware-toolbox-gtk:12860): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(vmware-toolbox-gtk:12860): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(vmware-toolbox-gtk:12860): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(vmware-toolbox-gtk:12860): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(vmware-toolbox-gtk:12860): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(vmware-toolbox-gtk:12860): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

I can't seem to copy and paste files and clipboard text entries from WIndows XP Pro 32-bit to the Guest OS Ubuntu Jaunty Jackalope. If I can't get the clipboard working, that's OK, but I really need to be able to share files between the host and Guest OS. 

Any suggetions?

Thank you,

Zorrorrorro

---

### Post by Zorrorrorro on 2009-06-21
Oh, and the "VMWare Tools Properties" window launches properly. But I still can't seem to copy and paste. (see attached screenshot). 

Thanks!

Zorrorroro

---

### Post by cboling on 2009-08-13
Libcanberra relates to sound events, so I wouldn't *think* that it has to do with clipboard operations, but maybe it wants to beep when you do it or something, so its lack is making the whole operation fail. Beats me.

I verified that the libcanberra-gtk-module package was installed, and the module exists in /usr/lib/gtk-2.0/modules

I started the toolbox from that dir, and it eliminated the complaint about not being able to find the module, but added 3 copies of another at the bottom of the "Unable to locate theme engine" messages:

[LIST]
[*]DEBUG: This Gtk version doesn't have the GtkSettings::gtk-* property
[/LIST]where "*" is:
[LIST]
[*]enable-input-feedback-sounds
[*]sound-theme-name
[*]enable-event-sounds
[/LIST]

SOLUTION/WORKAROUND:

I uninstalled the tools that came with workstation, and instead installed the open-vm-toolbox package (and its 21 dependencies) through Synaptic.

Nirvana! Copy & paste works with no hassles.  vmware-guestd and vmware-user automatically run in the background; only run vmware-toolbox if you want to use it for something. And, there shouldn't be any manual re-compiling for new kernels.

---

### Post by Zorrorrorro on 2009-08-13
Wow, I'll definitely try that out! Just curious, is the open-vm-toolbox maintained by VMWare or is it open source? 

But yeah, thanks!!!!

---

