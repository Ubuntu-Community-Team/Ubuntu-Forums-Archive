---
title: "CISCO VPN Client  gvpndialer problems."
date: 2008-06-26
forum: Desktop Environments
---

### Post by Ordinary12 on 2008-06-26
Hello Everyone:

I downloaded the CISCO Client GUI,gvpndialer and finally got the thing to come up correctly by following the instructions here: [http://ubuntuforums.org/showthread.php?p=5268037#post5268037](http://ubuntuforums.org/showthread.php?p=5268037#post5268037)

Now after starting the service as suggested the GUI presented me with a login terminal but the following was displayed in the command line box:

(gvpndialer:7024): Gtk-CRITICAL **: gtk_entry_set_text: assertion `text != NULL' failed

I'm able to type in my information and hit the login button but it just sits there and says it's trying to login but it never does. Does anyone in this group know what's wrong with my setup? I'm using Hardy Heron.

---

### Post by hackmeister on 2008-07-01
The first message is ok, ignore it:
(gvpndialer:15990): Gtk-CRITICAL **: gtk_entry_set_text: assertion `text != NULL' failed

You still need to have the ciscovpn application installed and running. The second message says you don't have the cisco kernel module running. To get the kernel module running type the following from the commandline:
sudo /etc/init.d/vpnclient_init start

FYI, I didn't write the app. I just packaged it. In the future I'd like to setup the installer to automatically make an entry in the menu along with an icon. If I have time I'll try to get that done.

---

