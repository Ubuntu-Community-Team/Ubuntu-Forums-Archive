---
title: "Make &quot;Places&quot; on menu use caja"
date: 2012-04-21
forum: Desktop Environments
---

### Post by bob-linux-user on 2012-04-21
Hello. I am running Ubuntu 12.04 with the MATE desktop.

When I scroll along the menu and press the "places" option just above "system" the nautilus file manager opens, whereas I would prefer to use caja.

How can I make places open in caja not Nautilus please?

---

### Post by bob-linux-user on 2012-04-23
bump.

Have I posted this in the right place?

MATE looks nicer than gnome fallback because you can set the theme to what you want. MATE looks nicer than XFCE and does not suffer from the "transport endpoint not connected" problem. Caja is easier to use than Nautilus because it has the up button. Using Unity or Gnome 3 is not an option for me because I prefer easy to use interfaces.

So, can anyone help on my original question please?

---

### Post by pqwoerituytrueiwoq on 2012-04-23
uninstall nautilus/thunar then it will ask you what file browser to use select other and type caja

---

### Post by bob-linux-user on 2012-04-23
Hello pqwoerituytrueiwoq and thanks.

When you uninstall Nautilus, synaptic says to uninstall ubuntu-desktop at the same time- so I did not do. The notes say ubuntu-desktop should not be removed.

if i uninstall using the command line instead :
sudo apt-get remove nautilus
will that uninstall ubuntu-desktop as well?

Regards

bob-linux-user

---

### Post by pqwoerituytrueiwoq on 2012-04-23
forgot about that i removed it when i was tampering with compiz
but if you are using mate it is safe to remove and you can reinstall ubuntu-desktop later, but try removing thunar 1st and see it it ask you for a new one

when it asked me it said it wanted to know the default for the xfce session

---

### Post by bob-linux-user on 2012-04-23
Thanks. I tried just removing Thunar and setting the preffered application for file manager to caja but places still opens with nautilus. I have noticed some minor stability problems with MATE anyway so I am going to use xfce for a bit now. Thanks anyway.

---

### Post by pqwoerituytrueiwoq on 2012-04-23
try this
[https://github.com/mate-desktop/mate-applets/issues/3](https://github.com/mate-desktop/mate-applets/issues/3)
name the issue i may have a fix

---

### Post by marioGJR on 2013-03-05
I had the same problem as you, using ubuntu 12.10 + MATE desktop.
I solved that by editing the '/usr/share/applications/defaults.lists' file. 
I changed the line :
```
inode/directory=nautilus.desktop
```
to:
```
inode/directory=caja.desktop
```
I recommend you to backup the file first.

ps: I believe this won't be a problem to you, but remember: This changes the default application to this type of file, so this will affect your Unity and eventually others DEs.

---

### Post by MiKOTRON on 2013-03-13
=D>  That worked great!  Only its '/usr/share/applications/defaults.list' not [COLOR=#000000] '/usr/share/applications/defaults.lists'

```
sudo pluma /usr/share/applications/defailts.list
```
[/COLOR][COLOR=#000000]
Thanks again marioGJR.[/COLOR]

---

