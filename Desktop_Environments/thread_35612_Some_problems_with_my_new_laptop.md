---
title: "Some problems with my new laptop"
date: 2005-05-19
forum: Desktop Environments
---

### Post by thelaughingman on 2005-05-19
I set up my new Averatec 3250 to dual boot XP and Kubuntu and I am having a few issues; the XP side works great, but the linux side needs some help:

Freezing (most important)
After a random amount of time on the linux side my computer will randomly freeze and is unresponsive to anything except holding the power button to shut off. I think its a cooling issue, has anyone else had this problem? and how did you solve it.  I tried the noinotify option when I boot and that didn't really seem to help, unless I did it wrong somehow.

WiFi (less important)
I installed the Ralink driver through the guide in the wiki, and I can use Raconfig or Kwifimanager to look for networks and I get a strong signal but I can never actually join it and get an IP. I just want to know if anyone has any experience getting thier laptop on a network with a linksys router using WEP. I have tried most of the options and I can't get it to be givin an ip. Any ideas? Also, on the windows side you need to press the wifi button on the case to activate the wireless card, is there a way to do this on the linux side so i dont have to sudo/login as root to activate the card everytime?

Thanks.

---

### Post by NTolerance on 2005-05-19
About WiFi:

It's generally regarded that Linux doesn't really have any good GUI tools for WiFi.  kwirelessmanager needs a lot of work, and so do the rest.  Right now it's best to use the command-line tool "iwconfig" to handle your wireless card.  Let's pretend your wireless card is named "eth1", the SSID of your wireless access point is "linksys", and the WEP key is "stuff":

```
sudo iwconfig eth1 essid "linksys" key 's:stuff' mode Managed
sudo dhclient eth1
```

Obviously replace "eth1", "linksys" and "stuff" with the appropriate names for your setup.

---

### Post by thelaughingman on 2005-05-19
Thank you  :grin: , that worked; you are now a personal hero of mine.  While I'm still in need of help, is there a way to turn those commands into something that I can have as a shortcus on my Desktop too?  I'm skill pretty new to linux and I haven't even done some of the things you guys find easy.  Thanks in advance.

ALso, does anyone else have any ideas about the strange freezing or the wifi power button (this one is probably wont happen anywhere except a dream, but I would still like to have it functional if possible)?

---

### Post by NTolerance on 2005-05-19
[QUOTE=thelaughingman]Thank you  :grin: , that worked; you are now a personal hero of mine.  While I'm still in need of help, is there a way to turn those commands into something that I can have as a shortcus on my Desktop too?  I'm skill pretty new to linux and I haven't even done some of the things you guys find easy.  Thanks in advance.

ALso, does anyone else have any ideas about the strange freezing or the wifi power button (this one is probably wont happen anywhere except a dream, but I would still like to have it functional if possible)?[/QUOTE]

Copy this to a new text file and change the values as before:

```
#!/bin/sh
iwconfig eth1 essid "linksys" key 's:stuff' mode Managed
dhclient eth1
```

Then cd to the directory where you saved the file and run

```
chmod +x filename
```

If you haven't done so already, set up a root account:

```
sudo passwd root
```

Now, log in as root and copy the script you made to your /bin directory:

```
cp filename /bin
```

Now, as root, you can run your connection script no matter what directory you may be in.  It should automatically connect to your access point and get an IP address.  As far as a shortcut, I'm not so sure about how to do that in Gnome.  I use KDE, and most apps/scripts that require root access such as this one will pop up with a window asking for your root password.  You can always try creating a new shortcut in Gnome containing the filename of your new shell script and then clicking on it to see if it will run.  

I'm not sure about the button on your WiFi card, but I do know that you can try doing a software card reset using this command:

```
iwpriv eth1 card_reset
```

---

### Post by bdmp on 2005-05-19
I have the same comp with the same problems.  But I always get the  freezing thing in windows not linux.  I even sent it back to have it repaired. Didn't work.

---

### Post by bdmp on 2005-05-19
[QUOTE=NTolerance]About WiFi:

I

```
sudo iwconfig eth1 essid "linksys" key 's:stuff' mode Managed
sudo dhclient eth1
```

Obviously replace "eth1", "linksys" and "stuff" with the appropriate names for your setup.[/QUOTE]

Does the "linksys" represent the network name? And is the  "s:stuff" for the key?  If you don't have one do you leave it out?

---

### Post by NTolerance on 2005-05-19
[QUOTE=bdmp]Does the "linksys" represent the network name? And is the  "s:stuff" for the key?  If you don't have one do you leave it out?[/QUOTE]

"linksys" is the SSID of the wireless network.  "s:stuff" is the WEP key.  Replace the "stuff" with your key.  If you don't have a particular network name or a WEP key, the command would be this:

```
iwconfig eth1 essid any key off mode Managed
dhclient eth1
```

---

### Post by thelaughingman on 2005-05-19
Thanks a bunch NTolerance, I'm sure I'll use this on other commands in the future as well.

---

