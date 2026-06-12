---
title: "PowerEdge 2900 Server Internet Trouble"
date: 2007-08-19
forum: Dell  Ubuntu Support
---

### Post by dastardly on 2007-08-19
I recently acquired a Dell PowerEdge 2900 server computer and so I attempted to install ubuntu 7.04 server on it. The setup went fine, up until DHCP. The computer has 2 ethernet ports, labelled NIC1 and NIC2, the internet is connected to NIC1. It asked me if I wanted to attempt to configure eth0 or eth1 with DHCP, so I took a guess and choose 1. This didnt work, so I went back and tried 0 also. Neither worked, so I decided to continue setup without internet.

Now I am finished the setup, and I still have no internet access with the computer. I have seen another post which said :
> 
And networking is now up too... Once you get the install done and it boots, log in and do the following:

sudo nano /etc/network/interfaces

(add the following to the file)

iface eth0 inet dhcp
auto eth0

iface eth1 inet dhcp
auto eth1

(press Ctrl+X, hit Y to save)

Then you can do:

sudo ifup ethX

(X is either 0 or 1 depending on which you want to activate, or you can do them both individually)

Hope that helps! My server is doing well now... now to continue configuring it...
-Josh

But that didnt do anything. This server is running off of my private network, and the laptop I am posting from now uses DHCP (though wifi). I have other computers connected directly through ethernet also which work fine, and previously this cable was connected to a computer that had been able to access the internet, so it is not a connection issue.

Any help would be appreciated, thanks!

---

