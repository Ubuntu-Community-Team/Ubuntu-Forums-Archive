---
title: "bluemon, does anyone know how to get it to work?"
date: 2006-06-29
forum: Desktop Environments
---

### Post by Anolis on 2006-06-29
Pretty much just as the title suggests, I've tried many various combinations of options with this program and programs that come along with it, in an attempt to lock my computer when I leave my room. It outputs no data whatsoever even with the verbose option selected. I cant even tell if it is recognizing my bluetooth phone. has anyone had any success with this program:confused: 

                          Best Regards, 
                                          Anolis

--RECENT DEVELOPEMENT--
------------------------------------------------------------------------------------------------------------------------------------------
anolis@SlayerofLife:~$ bluemon -t 50 -a -v -s -b 00:16:75:97:F4:E5
Bluetooth monitoring system startup, version 1.2
#anolis@SlayerofLife:~$ DBUS Name Error (Connection ":1.35" is not allowed to own the service #"cx.ath.matthew.bluemon.server" due to security policies in the configuration file)
------------------------------------------------------------------------------------------------------------------------------------------
im going to try this in root now... seems kinda dumb you would need root privs to run this program..

------------------------------------------------------------------------------------------------------------------------------------------
darn.... that didnt work...

#root@SlayerofLife:/home/anolis# DBUS Name Error (Connection ":1.43" is not allowed to own the service #"cx.ath.matthew.bluemon.server" due to security policies in the configuration file)

maybe someone knows what these warning messages mean...

---

### Post by Anolis on 2006-06-29
oops how do i delete this...

---

### Post by kooskakebeen on 2006-07-11
Installed the upstream version 1.3.1 from
[http://packages.debian.org/unstable/net/bluemon](http://packages.debian.org/unstable/net/bluemon)

and that solved the problem

---

### Post by myoldryn on 2006-11-01
Hi... I have problems running bluemon... The server goes up properly (i think). When i do bluemon-query, then only output i get is "nothing connected" and when i try to assign command --upcmd= smth...(anything) then i get "bluemon-client: option `--upcmd' doesn't allow an argument". Can anybody help me on that?

---

