---
title: "Sharing a printer on an 11.04 Unity home network"
date: 2011-08-31
forum: Desktop Environments
---

### Post by gwm on 2011-08-31
Hi,
I want to share a printer that is connected to my 11.04 box running under the default unity interface, with another pc running Ubuntu 10.04 using the Gnome interface.

I have a problem because the GUI applications for controlling networking, printers and things have moved, disappeared etc.

Sharing could not be enabled because of missing secret software. Eventually I found what installs were needed (two apache systems).

I couldn't find a simple way of setting the work group. I had to edit the samba configuration file directly.

To get the 10.04 client to see the shared printer, it must first be published on the 11.04 server. I can't find a way of doing this. All the tutorials are based on the Gnome interface. I tried [http://localhost:631](http://localhost:631). That uses a very different "speak", so I'm not sure if I guessed right. At any rate, the client still can't see the printer on 11.04.

Please can someone tell me how to publish the shared printer using the Unity interface.:confused:

---

### Post by gwm on 2011-09-01
Hi,
While I was submitting the above post, enough time elapsed and the client was able to see the printer.

In summary, the **steps needed to share the printer** were something like this:
[LIST=1]
[*]Install Samba if it isn't already installed
[*]Install **apache2.2-bin** and **libapache2-mod-dnssd**
[*]Restart the computer
[*]In the properties of the printer, mark it as shared over the network
[*]In the browser, go to **[http://localhost:631](http://localhost:631)**
[*]Find the tab and  check box that allows others to see your printer
[*]Check it and apply the changes
[*]Restart the computer again
[/LIST]
Now the client computer should be able to find the shared network printer.

**To set the work group in Unity UI**, click the Shut Down icon in the task bar (top right corner of the screen) and a menu drops down. Just below the shut down menu item is an item for system settings. Click that item and a display of many icons appears. Near the bottom double click the Samba configuration icon. The configuration program opens and offers three items in the main menu bar. I can't remember the labeling, but the middle one has two sub menu items. The one we want is the top one, and there is where one can specify the work group name.

:guitar:

---

