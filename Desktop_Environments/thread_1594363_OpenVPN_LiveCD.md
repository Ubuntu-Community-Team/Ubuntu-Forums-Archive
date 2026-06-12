---
title: "OpenVPN LiveCD"
date: 2010-10-12
forum: Desktop Environments
---

### Post by Ctorpor on 2010-10-12
Hi everyone. I'm putting this LiveCD together as a side-project. If anyone else is interested I'd be glad to put the results here when I'm done.

[SIZE="4"]_background_[/SIZE]
I'm fairly new to the whole Linux thing, but I am liking the whole customization aspect of things. Raised on Windows I could use some help. :)

I'm trying to set up a Ubuntu LiveCD that serves two functions and two functions only:

1. Pre-configured OpenVPN connection
2. Internet access to only 1 other IP

I've been working on this for a few weeks before stumbling here in defeat.
Using the Reconstructor ([here](https://reconstructor.apphosted.com/)) I have been able to use gconf settings to effectively lock down the desktop and panel and get the aesthetics side of things to work.

[SIZE="4"]_problems_[/SIZE]
[SIZE="2"][COLOR="DarkRed"]1. OpenVPN Settings[/COLOR][/SIZE]
I've been using kvpnc to connect to the openVPN server, but cannot find a way to import the configurations into a liveCD via chroot. In fact, I cannot find the kvpnc configuration files at all..
Does anyone else know where they are located in the file system?

[COLOR="DarkRed"][SIZE="2"]2. Firefox Lockdown[/SIZE][/COLOR]
At first I was going to try locking down the resolvable IPs by using a Firefox extension. However, it seems the -install-global-extension command tag no longer works. The next idea was to reconfigure the resolv.conf file to resolve all traffic to 127.0.0.1 and set the homepage of Firefox to the IP of the desired website. This would be sufficient for the know-how level of the 30 or so users by whom this LiveCD would be used. The problem is that resolv.conf is rewritten by NetworkManager on each connect. Is there any way to prevent this?


As I said before, I've been working on this for a few weeks as it is also my first foray into the wilds of the Linux distros. If you read all of that. Thank you already.
Am I going about this all wrong? If there is an easier method of doing this I am all ears.

---

### Post by Ctorpor on 2010-10-14
1. For the first issue, now that I don't have the [COLOR="DarkRed"]kvpnc configuration files[/COLOR] i've gone a different route and tried to set up openvpn to connect on startup from the terminal. 

I used
```
echo "nameserver 127.0.0.1" >> /etc/resolv.conf
firstline='#!/bin/sh -e'
echo "$firstline" > /etc/rc.local
echo "sleep 2" >> /etc/rc.local
echo "/etc/init.d/openvpn start" >> rc.local
```
to add the "openvpn start" command to the rc.local file for launch at GNOME startup. This does not seem to be working.


2. For the [COLOR="DarkRed"]connection lockdown[/COLOR] I tried setting the resolv.conf file to use:
```
echo "make_resolv_conf() {" > /etc/dhclient-enter-hooks
echo "echo \"Do nothing\"" >> /etc/dhclient-enter-hooks
echo "}" >> /etc/dhclient-enter-hooks
chmod 644 /etc/dhclient-enter-hooks
``` which is a snippet I found online to supposedly lock resolv.conf to a no-write state so that NetworkManager couldn't change it. This too has failed me.

Onward and upward :)

---

### Post by Ctorpor on 2010-10-22
[SIZE="5"]I've made more progress![/SIZE] :D

[SIZE="4"]1.[/SIZE] For the [COLOR="DarkRed"]VPN connection[/COLOR] I decided to place a VPN Connect icon on the desktop instead of having it auto-launch, so the user can connect at will. The desktop launcher runs a simple bash script to offer the user a terminal to connect. After 20 seconds this terminal closes, but keeps the connection if it was made.

[SIZE="4"]2. [/SIZE]For the [COLOR="DarkRed"]connection lockdown[/COLOR] I went back and added ```
echo "prepend domain-name-servers 127.0.0.1;" >> /etc/dhcp3/dhclient.conf
``` This seems to have done the trick. Now a user can only connect to a website by IP, so the homepage is now set by IP.

[SIZE="5"]Also[/SIZE]
I've used gconf-editor to lock down the gnome panels and to relocate all of the top_panel applets to the bottom_panel as well as limiting to one desktop screen using:
```
gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.defaults --type list --list-type string --set /apps/panel/default_setup/general/object_id_list [browser_launcher]

gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.defaults --type list --list-type string --set /apps/panel/default_setup/general/applet_id_list [notification_area,window_list,clock]

gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.defaults --type integer --set /apps/panel/default_setup/toplevels/top_panel/size 0

gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.defaults --type string --set /apps/panel/default_setup/applets/notification_area/toplevel_id bottom_panel

gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.defaults --type string --set /apps/panel/default_setup/objects/browser_launcher/toplevel_id bottom_panel

gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.defaults --type string --set /apps/panel/default_setup/applets/clock/toplevel_id bottom_panel

gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.defaults --type boolean --set /apps/panel/global/locked_down true

gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.defaults --type boolean --set /apps/nautilus/preferences/show_desktop true

gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.defaults --type boolean --set /apps/panel/default_setup/toplevels/top_panel/auto_hide true

gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.defaults --type string --set /desktop/gnome/font_rendering/antialiasing "rgba"

gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.defaults --type integer --set /apps/metacity/general/num_workspaces 1
```I'm sure some of these are superfluous or unnecessary, but I'm making progress so I don't want to break anything just yet. :)

I then wrote a couple of bash scripts. One launches OpenVPN in a terminal, then gives the user 20 seconds to log on before closing. This is with the help of a separate devilspie script. The other script places a "shutdown machine/Are you sure?" launcher on the bottom panel since I removed the menu for users. This was done using this line in terminal:```
/usr/lib/gnome-panel/gnome-panel-add --launcher=/etc/skel/Shutdown.desktop --panel=bottom_panel_screen0 --right-stick --position=0
``` Where /etc/skel/Shutdown.desktop is a file I created for my script.
Users can still use keyboard shortcuts to pull up the menu, but most users wouldn't understand this, and even if they did, it is a LiveCD so they will not be able to permanently damage the underlying OS.

If anyone is interested I can post the scripts I created:
- Shutdown.sh
- Minimize.ds
- VPN-Connect.sh


If anyone is interested in [COLOR="DarkRed"]_[SIZE="4"]helping[/SIZE]_[/COLOR] I'm still trying to use terminal commands to:

a. Remove the top panel entirely
b. Remove wubi installer
c. Launch a terminal command on GNOME startup

Any help is greatly appreciated!

---

