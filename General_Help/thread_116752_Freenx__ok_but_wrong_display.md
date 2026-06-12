---
title: "Freenx : ok but wrong display"
date: 2006-01-13
forum: General Help
---

### Post by bobcam on 2006-01-13
Hello,

What I'm using : Breezy + Freenx (server) + Windows XP and Nomachine client.

For the moment, the thing seems to work pretty good despite some icons problem but it doesn't matter for the moment.

The only thing I worry about is that, sometimes, the window application (for example OpenOffice or any other) opens on the wrong display. For example, I open OpenCalc on the client (XP) and the window opens on the server's display ! 

I'm newbie and your help would be very very very appreciated !!

(Sorry for my english!)

Laurent

---

### Post by Roman27 on 2006-01-13
Hmmm...  That's very odd.  I have the same setup and the "window application opens on the wrong display" problem you describe doesn't exist for me.  However, the other issue you describe "some icons problem", I have as well.  I fix it by restarting the GDM after I logon.

```
sudo /etc/init.d/gdm restart
```Keep in mind that this will probably kick you out of any running programs on the console as well.

---

### Post by bobcam on 2006-01-13
Very often, if I open OpenCalc (for example) on the client and it's already running on the server, the window opens on the server. If then I close OpenCalc on the server and opens it on the client, the window opens now on the client display !

---

### Post by bobcam on 2006-01-14
New information : 
Reading some posts let me think that the problem is linked with a bug reported on gnome and xlib. It seems that starting gnome-settings-daemon would be a workaround.

I tested the thing :
- all icons looks now normally
- windows seems to open on the right display

The only problem I now have is that, after starting gnome-settings-daemon on the client, there no way to start OpenOffice on the server AND on the client.

Could someone help me ? Is there something I do wrong starting gnome-settings-daemon ?

Help me please.

---

