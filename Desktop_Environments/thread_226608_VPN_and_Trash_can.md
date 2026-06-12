---
title: "VPN and Trash can"
date: 2006-07-31
forum: Desktop Environments
---

### Post by denisvj on 2006-07-31
just 2 questions :

1. How to add the recycle bin to the desktop ( like windows ) in gnome.

2. I use VPN to connect to my job, what is the equivalent app for linux ?

Thanks :) Have a nice day :)

---

### Post by tgentry on 2006-07-31
Well as far as vpn you can install the PPTPClient. Then you will need PPTPConfig you can download the config file here [http://pptpclient.sourceforge.net/howto-ubuntu.phtml]("http://pptpclient.sourceforge.net/howto-ubuntu.phtml")

Now for the Trash can. I dont know how to get it on the Desktop itself but you can add it to the panel by right clicking on the panel and choose Applet to panel

---

### Post by jordilin on 2006-07-31
To see the Trash icon in the desktop do the following:
Type:
```
gconf-editor
```
a window will pop up, with the gnome registry:
There will be a panel in the left side.
Go to apps->nautilus->desktop and click on the variable trash_icon_visible and you'll get the Trash in your desktop. See the screenshot below:

[IMG]http://personal.telefonica.terra.es/web/personalinfo/trashicon.png[/IMG]

---

### Post by misha680 on 2006-08-01
I recommend the NetworkManager plug-ins for VPN, they are quite convenient (as is NetworkManager). However, the NetworkManager plug-ins are not available on the default repositories, you have to do

```
sudo gedit /etc/apt/sources.list
```

scroll to the bottom and add the following line:

```
deb http://www.linux2go.dk/ubuntu dapper main
```

Now go to synaptic, refresh your package list, and search for network-manager packages. You need network-manager, network-manager-gnome, and then there are network-manager packages for PPTP and VPNC as well which are the VPN protocols that you can use. Once you install the plug-ins, the only other trick is to do

```
sudo gedit /etc/network/interfaces
```

and just leave in 

```
auto lo
iface lo inet loopback
```

which means network manager will manager all your network devices (wired, wireless, etc.). If you do not want this, you are going to have to leave in the lines that you do not want network manager to manage.

After that, I think if you reboot and login you should see the network manager icon pop up in your panel and you can left click on it and see the VPN options. If not, you can always run:

```
nm-applet
```

Hope that helps.

Misha

---

