---
title: "Installing ATI drivers :("
date: 2006-03-19
forum: Desktop Environments
---

### Post by Dark Damo on 2006-03-19
Hello sorry but i formatted my ubuntu install and now i have reinstalled it and i dont know how to install them :( Can anyone help? Do i download the GUI installer or what?


Oh and how can i convert a .rpm to a .deb, And can someone tell me how to update my sources.list too please :)

Is there a AMD Athlon 64 bit version of cedega also :) 



Thanks.

---

### Post by RAOF on 2006-03-19
Check out the "ATI drivers" link in my sig.

To convert a rpm to a deb you can use "alien".  It's in the repositories.  It won't always work, though.

To edit your sources.list, try running "gksudo gedit /etc/apt/sources.list"

There's no 64bit Cedega, although you can (with some effort) get the 32bit version running.

---

### Post by Dark Damo on 2006-03-19
> Check out the "ATI drivers" link in my sig.

To convert a rpm to a deb you can use "alien". It's in the repositories. It won't always work, though.

To edit your sources.list, try running "gksudo gedit /etc/apt/sources.list"

There's no 64bit Cedega, although you can (with some effort) get the 32bit version running.

Thanks mate :)

i get this

damo@ubuntu:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)


IS that what its supposed to display?

It gives me all these things i dont know about on my computer. Can i use the GUI installer?

---

### Post by Dark Damo on 2006-03-19
sorry to double post BUT

(gedit:31894): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

I cant edit my sources.list with the new one?

---

### Post by RAOF on 2006-03-19
[QUOTE=Dark Damo]...
damo@ubuntu:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)


IS that what its supposed to display?

It gives me all these things i dont know about on my computer. Can i use the GUI installer?[/QUOTE]
That's not what it's supposed to say :(.  I don't have any experience with ATI cards in Ubuntu - the ATI driver thread is the place to ask questions about that :).  Oh, and **what** GUI installer?

Secondly, you're trying to run **gksudo gedit /etc/apt/sources.list**, yes?  I get that error, but I can still edit my sources just fine.  Alternatively, you could try one of the command-line editors, like nano - **sudo nano /etc/apt/sources.list**.

---

### Post by Dark Damo on 2006-03-19
Hmm thanks but i dont know how to use that command line one :(

I cant touch anything in that sources.list file when i try to open it with gedit :(

---

### Post by DCJoeDog on 2006-03-20
to edit my list I used this command

```
sudo gedit /etc/apt/sources.list
```

it asks for a password and away I go

and to update my ati 9600 I found this on wiki

```
sudo apt-get install xorg-driver-fglrx
sudo apt-get install linux-restricted-modules-$(uname -r) #Okay if it is already installed
sudo dpkg-reconfigure xserver-xorg #Select the fglrx driver and 64-bit users should deselect int10a
```

hope that helps

---

