---
title: "What's the problem with my &quot;System&gt;Administration&quot; submenu?"
date: 2006-05-24
forum: Desktop Environments
---

### Post by seatea on 2006-05-24
I have been trying  to find  a fix for this problem for days. I have seen other posts that seem to have a simular problem after searching the  forums, but no solutions. This problem,  started after I did a fsck by creating a "/forcefsck" file from Terminal. It appeared to run ok when I rebooted, but afterwards I couldn't use sudo as my /etc/sudoers file  was corrupted(?). With help from the forums-  thanks to all- I was able to get that straightened out. I have not been able to get any of the programs under System>Administration to start even after repairing /etc/sudoers. I never get prompted  for my password and either nothing will happen  or the prograam appears to be starting, but never opens. All the other menus work. I can start the programs under "Administration"  like  Synaptic  from Terminal, although I get various messages in Terminal when I launch the programs  using it. These messages  have not been  helpful to me in coming up with a solution. Here are the Terminal outputs for Update Manager and Synaptic.

For Update Manager: "/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
/usr/lib/python2.4/site-packages/UpdateManager/MetaRelease.py:169: DeprecationWa rning: Class MetaRelease is already GObject-registered; Please note that classes  containing any of the attributes __gtype_name__, __gproperties__, or __gsignals __ are now automatically registered.
  gobject.type_register(MetaRelease)".

For  Synaptic: "(synaptic:7580): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(synaptic:7580): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed".

I keep thinking  that there is something I need to alter that will restore functionality. I re-installed gsudo as I thought it might  be  damaged, but that didn't help. Today, I had a message from Update Manager in the notification  area that there were updates, ironically Update Manager was one of them, but when I clicked to show updates, nothing  happened. I downloaded the updates by opening Update Manager through Terminal and installed the updates. I still couldn't open update manager from the  menu after the  installation. Can someone tell what is amiss with my gui?

I am using Breezy Gnome.

---

### Post by seatea on 2006-05-24
I had hoped to be able  to pinpoint the file or files that  were damaged. I suspect that  isn't going to  happen. I did the following "sudo apt-get install --reinstall ubuntu-desktop". I can now access the programs in "System> Administration".

I started up synaptic from Terminal and sudo worked too. I still get this  double message:

"(synaptic:12187): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(synaptic:12187): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed".

Maybe the message occurrs because the gui was bypassed to start Synaptic?

---

### Post by GBlin on 2006-06-20
Hello,

A friend of mine installed UBUNTU 6.06 two weeks ago and has the same problem.
Did you find some solution to this ? I did'nt manage to find a related bug in launchpad (I made a really quick search, I must confess...)
As far as I know, errors you mentionned when launching tools from console are only GTK warning (graphic library of GNOME) and are not related to the real problem. 
You said you have seen other thread dealing with this issue, can you post links to them please ?

Best regards, 
Guillaume

---

### Post by seatea on 2006-06-20
No. As I  stated in  my post, I only was able to correct my problem with the  System>Administration submenu by re-installing gnome-desktop. I don't have the links, but searched the forums by looking for the word System in the topic using the advanced search to find similar problems.

---

