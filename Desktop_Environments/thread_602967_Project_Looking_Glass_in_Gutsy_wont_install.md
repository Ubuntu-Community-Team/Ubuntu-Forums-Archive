---
title: "Project Looking Glass in Gutsy wont install"
date: 2007-11-04
forum: Desktop Environments
---

### Post by Mickeysofine1972 on 2007-11-04
Hi

I tried to install Project Looking Glass from the instructions on go2linux.org but get the following errors:

```

Setting up lg3d-core (1.0.0) ...
/usr/share/lg3d/bin/postinstall: line 10: /bin/arch: No such file or directory
/usr/share/lg3d/bin/../bin/add-lg-to-gdm: line 28: /bin/arch: No such file or directory
Success. LG has been added as a gdm session.
/usr/share/lg3d/bin/postinstall: line 43: cd: /usr/share/lg3d/bin/../lib/linux-/lg3d-x11/programs/Xserver: No such file or directory
chown: cannot access `Xorg': No such file or directory
chgrp: cannot access `Xorg': No such file or directory
chmod: cannot access `Xorg': No such file or directory
dpkg: error processing lg3d-core (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 lg3d-core
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

anyone else have this problem? anyone know how to fix it?

Mike

---

### Post by neilengineer on 2007-11-04
> **Mickeysofine1972 said:**
> Hi

/usr/share/lg3d/bin/postinstall: line 10: /bin/arch: No such file or directory
/usr/share/lg3d/bin/../bin/add-lg-to-gdm: line 28: /bin/arch: No such file or directory



No /bin/arch command.   In fedora, the command 'arch' is in a package called 'util-linux'.  But I don't know which package 'arch' is in in Ubuntu.

---

### Post by Mickeysofine1972 on 2007-11-05
Ubuntu has that package but the arch command isn't listed in it :-(

Anyone know where it is in Ubuntu?

Mike

---

### Post by ahmdprog on 2007-11-05
yes, In Ubuntu 7.10

it is very easy.

cd /bin
vi arch
             then type inside the file
uname -m
            then save it
then
chmod +x arch


then, Install Project Looking Glass and Enjoy, it is really very nice.

Regards,
Ahmad

---

### Post by bas1 on 2007-11-05
I too followed the directions @ go2linux.org. After taking the advice in the post above, I got looking glass to install OK, but when I try to launch looking glass through gdm looking glass gives me an error on startup. It's a long error, and I can't copy and paste it. Any solutions? :confused:

---

### Post by telic on 2007-11-06
I used the following installation instructions, using the debian repository method...

[https://lg3d.dev.java.net/lg3d-getting-started.html](https://lg3d.dev.java.net/lg3d-getting-started.html)


I got the "/bin/arch" errors, so I did the "postinstall" edit mentioned on this webpage...

[http://forums.java.net/jive/thread.jspa?messageID=243959](http://forums.java.net/jive/thread.jspa?messageID=243959)

Then I completed the failed install with **sudo apt-get install -f**


When I ran **lg3d-app** from Terminal, there were some errors about fonts, but it eventually launched. *Looking Glass* installed itself in such a way that I can select it as my desktop environment (instead of GNOME) from *Session* at login.

*Looking Glass* needs plenty of CPU and graphics horsepower. Even just moving the mouse pointer around can cause the 3D wallpaper photo to shift its perspective.

---

### Post by Mickeysofine1972 on 2007-11-08
I did the same a telic and thats seems to work fine, although the point about the cpu etc is very true as its not very fast on my 1GHz CPU + 512MB RAM + GF4 MX 440 lol!

Well, not to worry I discovered the compiz configure program and that seems to have a few little extras since last time I messed with it XD

I think I will keep to compiz/beryl as they are written with better performance in mind that that weird thing they call looking glass hehe

Mike

---

### Post by MrSpiffdifilous on 2008-02-18
not sure if you ever got this sorted out or not but if you follow ahmdprog's suggestion it will work im currently using lg3d. It's a cool idea, definetly not all there yet though. Very sluggish if you're used to regular linux speeds.

---

### Post by NikoC on 2008-05-25
Thanks ahmdprog for this quick and easy fix!

---

### Post by SneakyBooBoo on 2008-05-29
oh man. i followed the instruction from the link in one of the posts above about the post install and i must have botched something up terribly. now i dont get the code 1 error. i get all this.

```
E: /var/cache/apt/archives/lg3d-jdk_1.6.0+b104_i386.deb: subprocess pre-installation script returned error exit status 1
E: /var/cache/apt/archives/lg3d-java3d_1.5.0_i386.deb: subprocess pre-installation script returned error exit status 1


```
someone please help. i really wanna get looking glass up on my ubuntu.

*EDIT*

whats a broken dependency? i just checked my synaptics and the lg3d-core package is listed there now after that attempt to install.

---

