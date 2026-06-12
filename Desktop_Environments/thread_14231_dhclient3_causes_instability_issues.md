---
title: "dhclient3 causes instability issues"
date: 2005-02-05
forum: Desktop Environments
---

### Post by ngr2000 on 2005-02-05
Im running Ubuntu Warty 4.10 stock kernel with all updates and patches from apt-get on my Vpr Matrix Laptop vpr 200a5.  

So far  I  love ubuntu, its def my favorite laptop OS, but im not ready to switch my servers to it.

One problem Im having is with the command line tool "dhclient3"  This is the built in dhcp client that is installed.  The reason i use this command is to get a new Ip address when i switch from diff wifi networks.  Now the tools works great and i get a new IP everytime, but there is a side effect.  The whole OS bescomes extremely unbstable and slow.  After invoking the command I can no longer open up nautilus from a shell or even open my home directory from the start menu.  If I kill X and reload it I still have the same problems.  I even swithed to another console and killed gdm and and X stuff.  I then restarted gdm and tried kde instead of gnome and that hung too.  So I  killed it and triend gnome again and that also hung.

This wierdness happens everytime shorty after running the dhclient3 command.

Can anyone help me or suggest another way to renew my ip address.  Ifconfig down and up does not renew my IP for me.

Both my wifi card and nic card work great too so its above and beyond me.

---

### Post by az on 2005-02-05
If your /etc/network/interfaces is properly setup, you should be fine with

sudo ifdown eth0
sudo ifup eth0

You may also do 
sudo dhclient eth0

Perhaps it is your wireless card that is taking up so much cpu?  What driver are you using?  Post the contents of /etc/network/interfaces

---

### Post by hone on 2005-03-12
I think I have tihs problem too, I thought it was nautilus or something before.  I'm going to try using pump.  I'm running on a ibm thinkpad x31.

---

