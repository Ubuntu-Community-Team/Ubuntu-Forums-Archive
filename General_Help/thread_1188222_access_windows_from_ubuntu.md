---
title: "access windows from ubuntu"
date: 2009-06-15
forum: General Help
---

### Post by metalmaniac248 on 2009-06-15
hi there, 

does anyone know of a way that i could access the files on a windows machine as if i were logged on as Administrator (like view the other users files) from a Ubuntu machine over a hoe network, 

PS.

id like this to be secure so that this could only be done from my user account.


thanks

---

### Post by mhgsys on 2009-06-15
Well, you could share your windows directory, make a authorized user for that on your windows box and access it true samba on the ubuntu box.
 
But I'm guessing you are looking for something like Remote Desktop, 

Good luck with that.

---

### Post by Amilo1718 on 2009-06-15
> **mhgsys said:**
> But I'm guessing you are looking for something like Remote Desktop
tsclient ?

---

### Post by Cheesemill on 2009-06-15
Go to Places > Connect to Server

Service type - Windows share
Server - IP of Windows machine
Share - c$
User name - Administrator

Click 'Connect', enter the Administrator password and your good to go.

---

### Post by mhgsys on 2009-06-15
> **Amilo1718 said:**
> tsclient ?

Like that indeed.

:-)

Although I don't know if it will work, simply because I don't use windows on my computers that often.
But it sure looks like it,

---

### Post by metalmaniac248 on 2009-06-15
thanks for replies,


tsclient looks good but im having problems, 


when i try to connect i get this

"getaddrinfo: Name or service not known"

---

### Post by Amilo1718 on 2009-06-15
which options did you choose?

---

### Post by mhgsys on 2009-06-15
hmz,
I guess you also have to make sure windows accepts incoming connections, 
Meaning: windows should be set up for remote desktop, also configure all firewalls if any.

---

### Post by Pax-Man on 2009-06-15
I can only recommend you using TightVNC [http://www.tightvnc.com/.]("http://www.tightvnc.com/") Because it works, without making troubles. 

You simply download the file for windows and installs the client. As I can understand you want the Windows computer to be the "host" you do that by open the "Launch TighVNC server" setup your password and the other settings you want.  Then you will see the TighVNC icon in the corner keep your mouse over that write the IP down and put it in the remote control program that follows with Ubuntu.
Good luck :)

---

### Post by metalmaniac248 on 2009-06-16
i have checked on vista, and remote desktop is allowed,


in Ubuntu on TSClient i put "BASKERVILLE-PC" in the computer name, and selected RDPv5



as for vncserver, i cant see how im suposed to install it on ubuntu

---

### Post by Cheesemill on 2009-06-16
> **metalmaniac248 said:**
> in Ubuntu on TSClient i put "BASKERVILLE-PC" in the computer name, and selected RDPv5

This will only work if you're running an internal DNS server. Try using the IP address instead.

> as for vncserver, i cant see how im suposed to install it on ubuntu

You don't. You install the VNC server on your Windows machine and connect to it using Remote Desktop Viewer (which is installed in Ubuntu by default).

Also if you just want to have access to the files rather than take control of the machine have you tried the solution I posted above?

---

### Post by metalmaniac248 on 2009-06-16
ok progress update,


installed vnc server on vista, 

and managed to view desktop from Ubuntu,


however i get disconnected when i try and perform administrative tasks, and is there a way to log on to a user remotely?

---

### Post by egalvan on 2009-06-16
> **Cheesemill said:**
> 
You don't. You install the VNC server on your Windows machine and connect to it **using Remote Desktop Viewer (which is installed in Ubuntu by default**).


How is this launched? 

If GUI, what menu is it under?

If cli, what is the program name?

Thanks.

P.S.
your other info is much appreciated.
Thanks!

---

### Post by Amilo1718 on 2009-06-16
just type tsclient in the terminal :KS

---

### Post by metalmaniac248 on 2009-06-16
i connected using using remote desktop top viewer,

its GUI and is found under Applications -> Internet

---

### Post by mhgsys on 2009-06-17
so it's solved now?

---

### Post by metalmaniac248 on 2009-06-20
well sort of, but it keeps disconnecting me whenever i try to do any administrative tasks, and i wondered if there was a way to log on through this app.

---

