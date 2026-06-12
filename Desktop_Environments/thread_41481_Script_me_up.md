---
title: "Script me up"
date: 2005-06-13
forum: Desktop Environments
---

### Post by Dave_is_sexy on 2005-06-13
To get on the net atm I have to go to root terminal and type:

sudo modem_run -k -f /lib/hotplug/firmware/speedtch-1.bin
sudo pppd call speedtch

Can i make a little .sh file or something which i can click on to do that for me, and work on any user account? Is the sudo bit needed?

MY modem (external usb, speedtouch) also doesn't apper in the admin > network bit. Is there a way to put it there? (It does work thankfully)

Thanks

---

### Post by desdinova on 2005-06-13
[QUOTE=Dave_is_sexy]To get on the net atm I have to go to root terminal and type:

sudo modem_run -k -f /lib/hotplug/firmware/speedtch-1.bin
sudo pppd call speedtch

Can i make a little .sh file or something which i can click on to do that for me, and work on any user account? Is the sudo bit needed?

MY modem (external usb, speedtouch) also doesn't apper in the admin > network bit. Is there a way to put it there? (It does work thankfully)

Thanks[/QUOTE]
 My speedtouch doesn't - I'd just leave it - fortunately you don't need to do to much to it

create a file like this

sudo gedit /bin/connect_net

in it put this

#!/bin/sh
 modem_run -k -f /lib/hotplug/firmware/speedtch-1.bin
pppd call speedtch

save this file

sudo chmod 755 /bin/connect_net
sudo chmod +s /bin/connect_net

(this automatically sudo's it)

then you need to make it start automatically

I'd personally 

sudo /etc/init.d/networking

and at the very end put the line

/bin/connect_net

---

### Post by desdinova on 2005-06-13
useful link to bookmark

[www.linuxcommand.org](www.linuxcommand.org)

---

### Post by Dave_is_sexy on 2005-06-13
Awesome, that works great thanks.

Yeah I've read the first few chpters of linuxcammand. I can do ls and cp and a few other basic things. oh cd aswell - very handy that one.

I'm not convinced i like my terminal tho. Sometimes it wont let me go back and edit a line i've pasted in and sometimes it runs what i've pasted before i'd added to the end of it. It's also very touchy about me clicking where i want to type before i can type. slightly defeating the point of a text terminal i think. I'm gonna leave it for now, but will probably change it next week. ^_^

---

### Post by desdinova on 2005-06-13
[QUOTE=Dave_is_sexy]Awesome, that works great thanks.

Yeah I've read the first few chpters of linuxcammand. I can do ls and cp and a few other basic things. oh cd aswell - very handy that one.

I'm not convinced i like my terminal tho. Sometimes it wont let me go back and edit a line i've pasted in and sometimes it runs what i've pasted before i'd added to the end of it. It's also very touchy about me clicking where i want to type before i can type. slightly defeating the point of a text terminal i think. I'm gonna leave it for now, but will probably change it next week. ^_^[/QUOTE]
 Sometimes you can accidently copy a carriage return if you copy a line from elsewhere - it p'es me off too!

---

