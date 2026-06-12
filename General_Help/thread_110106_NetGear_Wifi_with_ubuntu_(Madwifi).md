---
title: "NetGear Wifi with ubuntu (Madwifi)"
date: 2005-12-30
forum: General Help
---

### Post by ReMuSoMeGa on 2005-12-30
im trying to run a netgear wireless card on my ubuntu box.
I read around on this forum, and learned that I need Madwifi (correct me if im wrong)


anyways, I went to madwifi.org and here is what it says

> 
Ubuntu ships madwifi in the restricted component, which is enabled in the default install. Madwifi chipsets should therefore ‘just work’.

In case you did a manual install, try installing linux-restricted-modules-$(uname -r) and that’s it. 



allright, I have no idea what that means. can someone please explain exactly what I should type into the shell, and exactly what other programs i will be needing to make this work.

Thanks.

-RemusOmega

---

### Post by Mr Frosti on 2005-12-30
Ok, first things first. Lets check and see if the card you are trying to install is one of the supported cards by the MadWifi project. The following is a list of supported Netgear products:

   1. WAG511
   2. WG311
   3. WG311T
   4. WG511T
   5. WG511U
   6. WPN311
   7. WPN511

If your card's product number is listed above, then lets continue. If not, then chances are your card will work, just not with the MadWifi project. In the interest of time, I will assume that you have one of the Netgear cards listed above. The complete list of supported cards can be found at [http://madwifi.org/wiki/Compatibility]("http://madwifi.org/wiki/Compatibility")

Next, lets download the MadWifi files themselves. A look at the Downloads page [http://madwifi.org/wiki/UserDocs/GettingMadwifi]("http://madwifi.org/wiki/UserDocs/GettingMadwifi") shows that the project already has .deb files (files pre packaged especially for Debian based systems, such as Ubuntu). So, lets download our file:

1. [http://debian.isg.ee.ethz.ch/public/pool-sarge/madwifi/madwifi-source_20041023-1_all.deb]("http://debian.isg.ee.ethz.ch/public/pool-sarge/madwifi/madwifi-source_20041023-1_all.deb")

2. Now, lets get a piece of software that is needed for this driver to work. Type the following in a terminal:

```
sudo apt-get install sharutils
```

3; Now that our dependencies are filled, navigate to the directory you downloaded the .deb file to in a terminal, and then install this file by running the following command:

```
sudo dpkg -i madwifi-source_20041023-1_all.deb  
```

This will prompt you for your password (actually root's password) to install the software. 

4. Now that this is installed, we can continue on to the next step, according to the "First Time Howto" instruction on their website:

[http://madwifi.org/wiki/UserDocs/FirstTimeHowTo]("http://madwifi.org/wiki/UserDocs/FirstTimeHowTo")

You can skip "Requirements", "Getting Sources", "Building", "Installing", "Loading" and "Creating" as the .deb file we just installed has taken care of all of this for you. 

You should now be able to scan for Wireless access points using their instructions, or by using the Gnome Network Monitor tool. Make sure that you have lights blinking on your card indicating that it is receiving power. 

I hope that this helps.

---

### Post by dickohead on 2006-01-05
and if there is no blinking lights on my card?

---

### Post by hajk on 2006-01-05
I really don't understand most of the replies to the OP's message... All he needs to be reassured of (IMHO) is that the madwifi driver in the linux-restricted-modules package for his kernel version will get his NetGear card up and running without having to do more than configuring the network (in System-Administration-Network, e.g.)... provided, of course, that his card has the Atheros chip like in the WG511T card. That's the way it worked for me..., just fired up Synaptic and installed that restricted package.:smile:

---

### Post by goreblast on 2006-01-07
I followed  the instructions given by Mr Frosti and it worked a treat. Great work mate.

---

