---
title: "Hamachi-GUI in 9.04??"
date: 2009-05-31
forum: General Help
---

### Post by BrandonBan6 on 2009-05-31
Hey All,

Not finding a lot of luck here in searching, so I thought I'd try a post... 

I've installed Hamachi & Hamachi-GUI on my Ubuntu 9.04 installation. I can connect to networks, pull an IP just fine.....but then the app just hangs with the status "Retrieving Nicks..."

Any initial thoughts? Let me know what info you need for troubleshooting!

Thanks for reading

---

### Post by BrandonBan6 on 2009-06-01
bump

---

### Post by Turpin on 2009-12-27
Bump!  Anybody have this?  I have four different computers running Ubuntu Jaunty with lxde desktop that I set up with hamachi and hamachi-gui and only one of them has this problem.  I've seen this before about a year ago with a couple other computers and all I remember is that it was a pain in the ars and I think I may have ended up REINSTALLING Xubuntu!  Not an option this time.  Hamachi seems to work, logs in, etc.  I have connectivity with everyone on the network.  Command line hamachi works fine.  But hamachi-gui stubbornly sits there spinning its wheels showing only " Retrieving nicks... "  Since no names or networks appear, I can't do anything using the hamachi-gui interface.  It makes me so very, very angry.  Tomorrow I shall totally destroy hamachi, hamachi-gui, and their profile folders, and reinstall them.  Maybe it will work?

And contrary to what you may see near my name, this is certainly not my first cup of Ubuntu.  I just don't speak unless I have something intelligent to say.  And that is very rare.  :D

---

### Post by infinitejones on 2009-12-27
There has to be **something** different about the one machine that it won't work on. Any ideas what that might be?

---

### Post by Turpin on 2009-12-27
Hmm, software-wise, I imagine there may be subtle differences in configuration, even though I've made it a point to keep all my systems as close to identical as possible.  It's running a custom "lxubuntu" jaunty, obtainable from some ftp sites. (I had to uninstall all "jap" packages that were found in synaptic search and change the default language and sources to english/US).
Hardware-wise, it's very similar to two of the other systems I've set up with the same configuration.  It's a home-built with an Elitegroup k7s5a Pro motherboard (cheap, low on features, but dependable), with an Athlon Thoroughbred 2400 cpu if I remember right. For some reason unknown to me, it won't run the CPU with its intended front-side bus of 133, and 138 seems unstable, but it's happy at 143, so... okay. It seems to run cool and it's stable, even doing heavy work, so I don't argue with it.  It has an add-on PCI nic card, accesses the internet just fine, sees all other computers fine, has its own IP assigned by the router etc.  
Based on my experience, even something subtle can cause problems like the one I described, but so far I can't figure what's causing this one.

---

### Post by infinitejones on 2009-12-27
In my experience, if there's no huge differences software-wise (eg. one machine running Ubuntu and another running Kubuntu), your first step might as well be to completely uninstall Hamachi from the problem machine, and then re-install it. 

By completely uninstall, I mean including deleting all the config files etc - find them all using

```
locate hamachi
locate hamachi-gui
```
after you've uninstalled using aptitude or dpkg -r or similar.

---

### Post by Turpin on 2009-12-27
I did uninstall hamachi (which I had originally installed using the following steps) and all its files including as well its profile folder, then uninstalled hamachi-gui using apt-get remove.  Reinstalled hamachi using the following steps, but still the same problem.

Installing Hamachi (these are notes of possible steps to take in approximate order in case something might not be working right)
$ sudo aptitude install build-essential upx-ucl
sudo modprobe tun (optional)
sudo gedit /etc/modules (optional)
add tun to modules
ls /dev/net/tun  (optional)
sudo mkdir /dev/net  (optional)
sudo mknod /dev/net/tun c 10 200  (optional)
ls /dev/net/tun  (optional)
reboot  (not necessary usually)
Download the newest hamachi version from [http://files.hamachi.cc/linux/](http://files.hamachi.cc/linux/) or
wget [http://files.hamachi.cc/linux/hamachi-0.9.9.9-20-lnx.tar.gz](http://files.hamachi.cc/linux/hamachi-0.9.9.9-20-lnx.tar.gz)
tar -zxvf hamachi-0.9.9.9-20-lnx.tar.gz
cd hamachi-0.9.9.9-20-lnx/
sudo make install
cd /usr/bin
sudo upx -d hamachi
sudo /sbin/tuncfg
sudo groupadd hamachi
sudo gpasswd -a [user] hamachi
sudo gpasswd -a root hamachi
sudo chmod 760 /var/run/tuncfg.sock
sudo chgrp hamachi /var/run/tuncfg.sock
hamachi-init
sudo hamachi start
sudo hamachi set-nick [nickname]
sudo hamachi login
sudo hamachi join [network name]
install hamachi-gui using the deb file.
sudo chown -R $USER:$USER ~/.hamachi   (IMPORTANT STEP)
If you started hamachi with root, sudo hamachi stop  (may not have any effect/be necessary to run this, but can't hurt)
reboot
(And I have a script to start Hamachi and login to my network at system startup, which does fine once you properly edit the /etc/sudoers file to allow tuncfg without a sudo password)

#!/bin/sh
gksu /sbin/tuncfg
hamachi start
hamachi login
sleep 2s
hamachi go-online [network]

So here's my temporary workaround:  I have a .desktop button I put in the menu called "Hamachi list" that fires up a bash script that runs my hamachilist script that I put in /usr/bin and allowed permisions for to show the computers on the hamachi network for easy copy/pasting. I'll come back and post here if I ever figure out a solution to this pain in the butt we've been discussing.

#!/bin/bash
for (( ; ; ))
do
clear
hamachi list
read -p "Press enter to refresh" nothing
done

And the "Hamachi List" desktop file to launch it:
[Desktop Entry]
Encoding=UTF-8
Name=Hamachi List
GenericName=Terminal
Comment=List Hamachi IPs
Exec=lxterminal -e hamachilist
TryExec=lxterminal
Icon=/usr/share/pixmaps/lxterminal.png
Type=Application
Categories=Network;

---

### Post by Turpin on 2009-12-28
Solved!  And it was so obvious!  I had forgotten to give my laptop on the network a nickname a while back when I set it up, so it could see all the other nicknames fine, but the only other computer I have online right now couldn't resolve the network nicknames because of that.  I bonk my head for the suffering I have caused others.  Thanks for the attempt at helping me through this even though I hadnt given you much to go on.

---

### Post by infinitejones on 2009-12-28
Glad you solved it! It's always that one little "insignificant" difference that causes the problems... ;)

---

