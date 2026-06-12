---
title: "OpenVPN help!!"
date: 2006-08-29
forum: Desktop Environments
---

### Post by 1oki on 2006-08-29
Can anyone explain why I might not have a configuration file... or any files for that matter, after I install openvpn from either apt-get or synpatic?

I also cant install openvpn from source, because apparently there is no make file... already ran ./configure ... ](*,) thanks

-l

---

### Post by ebash on 2006-08-29
When you install OpenVPN you should have an very basic configuration file placed in /etc/default/openvpn, that file is used by the OpenVPN startup script.

There should also be an empty folder /etc/openvpn/ where you should place your VPN configuration file and your VPN secret key. This VPN configuration file is specific to each VPN and should be given to you by your sysadmin.

Once you have placed your VPN configuration and your secret key in the folder /etc/openvpn/ you should be able to use the VPN from the command line.

---

### Post by 1oki on 2006-08-29
thanks ebash! i see the config file now :)

---

### Post by ebash on 2006-08-29
No problem. 

PS: If you would like a simple, very simple, GUI to handle your OpenVPN connections you can install a simple application that I created: gtk-openvpn

Add the following line to your /etc/apt/sources.list file:

```
deb http://debian.potyl.com/ custom main
```

Then do:
```
sudo apt-get update; sudo apt-get install gtk-openvpn
```

Start the command with:
```
gtk-openvpn
```

If you like the application you can add it to your session startup programs.


You should see a network icon in the system tray.

---

### Post by 1oki on 2006-08-29
oh man! your a god send! thanks!

---

### Post by JohnW on 2006-09-22
> **ebash said:**
> No problem. 

PS: If you would like a simple, very simple, GUI to handle your OpenVPN connections you can install a simple application that I created: gtk-openvpn


Hi ebash!  Does it work with a bridged vpn?  I'm having a struggle setting up with bridging.

---

### Post by ebash on 2006-09-22
Hi JohnW, 

My application should work with any kind of VPN since it's just a wrapper, a big fancy wrapper, over the commands:

```

sudo /etc/init.d/openvpn start VPN-NAME
sudo /etc/init.d/openvpn stop VPN-NAME

```

I suggest that you trouble shoot your VPN with the commands I listed above.

Saddly, I'm not a VPN expert nor a network expert just a simple VPN user. My VPNs where configured by the admins of their respective networks and everything worked out of the box.

But I can still try to help you.
Can you post your configuration files here? 

**DON'T POST YOUR VPN KEY!**

---

### Post by Fully216 on 2006-10-03
FYI - the repo 'deb [http://debian.potyl.com/](http://debian.potyl.com/) custom main' is not longer working.  Is there another place we could obtain a version of gtk-openvpn?

Failed to fetch [http://debian.potyl.com/dists/custom/main/binary-amd64/Packages.gz](http://debian.potyl.com/dists/custom/main/binary-amd64/Packages.gz)  404 Not Found

---

### Post by NoJock on 2007-01-13
> **ebash said:**
> When you install OpenVPN you should have an very basic configuration file placed in /etc/default/openvpn, that file is used by the OpenVPN startup script.

There should also be an empty folder /etc/openvpn/ where you should place your VPN configuration file and your VPN secret key. This VPN configuration file is specific to each VPN and should be given to you by your sysadmin.

Once you have placed your VPN configuration and your secret key in the folder /etc/openvpn/ you should be able to use the VPN from the command line.

Ok in not to sure what is up but i have no conf file at all and have no idea of how to build on. have verry little exp with linux (few disto installed) Like ubuntu. Is their a step by step guide to help me install vpn that will work with the graphis interface??

---

### Post by Darrena on 2008-02-11
Ebash, your applet was just what I was looking for but it doesn't seem to support passwords on the private keys.   Is this correct or did I do something wrong?

Thanks!

---

### Post by ebash on 2008-03-28
Sorry for the late reply. My VPN GUI is quite limited, it assumes that the VPNs can be started automatically without any end user interaction. Basically it calls "sudo /etc/init.d/openvpn start VPN-NAME" for you, without any end user interaction.

I can't try to add a way to handle private keys or passwords if you show me what command you are using for starting and closing the VPN. Feel free to contact me personally and I will see what I can do.

---

