---
title: "disable password for network setup?"
date: 2005-08-29
forum: Desktop Environments
---

### Post by usererror on 2005-08-29
I cannot find the thread for the life of me...

How do i disable the need to enter my root password everytime I want to connect to a wireless network or release and renew my IP address?

thanks!  I read the thread once before and i must not be using the right search keywords. :(

---

### Post by arnieboy on 2005-08-29
[QUOTE=usererror]I cannot find the thread for the life of me...

How do i disable the need to enter my root password everytime I want to connect to a wireless network or release and renew my IP address?

thanks!  I read the thread once before and i must not be using the right search keywords. :([/QUOTE]
what is the application that you are using to connect to the network? is it your sudo password or root password that u need?

---

### Post by usererror on 2005-08-29
i use the gtk wifi tool, and also the gnome network applet, if i need to.

when i start the gtk wifi tool, it wont do anything *unless* i go into the gnome network applet, i enter my root password, and start configuring the wifi that way.

there was a post here, somewhere that you could make a change somewhere on the system so that gnome wouldn't prompt you for your root password everytime you wanted to reconfigure your network settings.

hopefully that makes sense.

thanks!

---

### Post by arnieboy on 2005-08-29
[QUOTE=usererror]i use the gtk wifi tool, and also the gnome network applet, if i need to.

when i start the gtk wifi tool, it wont do anything *unless* i go into the gnome network applet, i enter my root password, and start configuring the wifi that way.

there was a post here, somewhere that you could make a change somewhere on the system so that gnome wouldn't prompt you for your root password everytime you wanted to reconfigure your network settings.

hopefully that makes sense.

thanks![/QUOTE]

please paste the contents of /etc/sudoers

---

### Post by arnieboy on 2005-08-29
[QUOTE=usererror]i use the gtk wifi tool, and also the gnome network applet, if i need to.

when i start the gtk wifi tool, it wont do anything *unless* i go into the gnome network applet, i enter my root password, and start configuring the wifi that way.

there was a post here, somewhere that you could make a change somewhere on the system so that gnome wouldn't prompt you for your root password everytime you wanted to reconfigure your network settings.

hopefully that makes sense.

thanks![/QUOTE]

please paste the contents of /etc/sudoers
so, the gnome network applet is the only thing which asks for your root password eh?

---

### Post by usererror on 2005-08-29
of those two items, yes that's the only thing that asks for root.  but if i try to make any changes to any other system items, date, time, etc, it asks for the root password, as it should...  i just want the network items to not ask for it :)

> # /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults	!lecture,tty_tickets,!fqdn

# User privilege specification
root	ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin	ALL=(ALL) ALL
ALL     ALL=(root) NOPASSWD: /usr/bin/gtkwifi-settings-client


well THAT is interesting...it looks like, the gtkwifi tool already is set to not need an admin password...BUT...it never associates unless i start the gnome network tool...

3rd edit:  now that i've looked at that file i've solved my problem, with your help, in pointing me to that /etc/sudoer file!  

i added a line: > ALL     ALL=(root) NOPASSWD: /usr/bin/network-admin

and it no longer asks me for my root password to make network changes!  i'll see how this works now!

---

### Post by arnieboy on 2005-08-29
[QUOTE=usererror]of those two items, yes that's the only thing that asks for root.  but if i try to make any changes to any other system items, date, time, etc, it asks for the root password, as it should...  i just want the network items to not ask for it :)



well THAT is interesting...it looks like, the gtkwifi tool already is set to not need an admin password...BUT...it never associates unless i start the gnome network tool...

3rd edit:  now that i've looked at that file i've solved my problem, with your help, in pointing me to that /etc/sudoer file!  

i added a line: 

and it no longer asks me for my root password to make network changes!  i'll see how this works now![/QUOTE]
nice that u figured it out urself. enjoy :)

---

### Post by usererror on 2005-08-29
well i owe you for pointing me in the right direction.  

now to get this gtk wifi applet to see that my wifi card DOES support scanning.  :mad:

---

