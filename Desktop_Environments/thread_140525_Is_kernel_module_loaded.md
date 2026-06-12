---
title: "Is kernel module loaded?"
date: 2006-03-06
forum: Desktop Environments
---

### Post by jerinjoy on 2006-03-06
I'm trying to get my vpn client to connect to the vpn at office. Its giving me the following error:
Could not attach to driver. Is kernel module loaded?

It looked to me like an OS error? if it is anyone know what I should do? I'm running 5.10.

---

### Post by kuppas on 2006-03-06
Start your VPN service (I don't remember the exact name, something starts with cisco or vpn) and then connect

/etc/init.d/CiscoVPN_init start

-Kuppa

---

### Post by tycarp on 2007-10-19
Thank you.  In my case, the command was

/etc/init.d/vpnclient_init start

It was exactly what I needed, as my corporate instructions didn't include this little piece of information.

---

### Post by kendic on 2007-12-10
Run 
"sudo ln -s /etc/init.d/vpnclient_init /etc/rc2.d/S85vpnclient_init". It will load the kernel modules automatically on reboot.

---

### Post by Ordinary12 on 2008-06-26
Hey Guys:

Thanks for posting this information on here.  It really helped me get this GUI further than before but I'm still having some trouble logging in and would appreciate any help you can give me.  After starting the service as you suggested the GUI presented me with a login terminal but the following was displayed in the command line box:

(gvpndialer:7024): Gtk-CRITICAL **: gtk_entry_set_text: assertion `text != NULL' failed

I'm able to type in my information and hit the login button but it just sits there and says it's trying to login but it never does.  Does anyone in this group know what's wrong with my setup?  I'm using Hardy Heron.

---

### Post by jualin on 2008-06-26
I think you should make a thread on your question so people can help you since this thread is from almost a year ago.

---

