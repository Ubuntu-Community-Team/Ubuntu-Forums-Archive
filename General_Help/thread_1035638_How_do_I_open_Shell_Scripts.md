---
title: "How do I open Shell Scripts?"
date: 2009-01-09
forum: General Help
---

### Post by Mountain Linux on 2009-01-09
In linux ubuntu, how do you open shell scripts?

I downloaded nvidia stuff and google earth. They are both shell scripts and i'm wondering how to open them...

---

### Post by oldos2er on 2009-01-09
> **Mountain Linux said:**
> In linux ubuntu, how do you open shell scripts?

I downloaded nvidia stuff and google earth. They are both shell scripts and i'm wondering how to open them...

 Google Earth should be binary. Anyway, if it's on your desktop, open a terminal and run these commands one at a time:

 cd Desktop

 chmod a+x GoogleEarthLinux.bin

 sudo ./GoogleEarthLinux.bin

 When the installer is finished and asks if you want to run Google Earth or quit, choose quit.

 The easiest way to install Nvidia restricted drivers is to go to System, Administration, Hardware Drivers.

---

### Post by taurus on 2009-01-09
> **oldos2er said:**
> 
 **[COLOR="Blue"]sudo[/COLOR]** ./GoogleEarthLinux.bin

 When the installer is finished and asks if you want to run Google Earth or quit, choose quit.


You don't have to install Google Earth with root privilege.  Just install it in your $HOME and everything should be good too.

---

### Post by oldos2er on 2009-01-10
> **taurus said:**
> You don't have to install Google Earth with root privilege.  Just install it in your $HOME and everything should be good too.

 Installing it with "sudo" puts it in /opt/google-earth as opposed to one's home directory.

---

