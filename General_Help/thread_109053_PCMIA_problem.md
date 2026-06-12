---
title: "PCMIA problem"
date: 2005-12-27
forum: General Help
---

### Post by Skibum on 2005-12-27
Hi, I just installed Ubuntu 5.10 on an old notebook type pentium pc, and i can't get it to talk to the LINKSYS wireless network card installed in the PCMIA port.  Like other posters i've seen I to am a Linux novice and need things explained in small steps.:)

---

### Post by ingo on 2005-12-28
hi,

there are a number of paths for you to take. First, you might want to try and find out which chip your card is using - googling will help.

If you find that your chipset is supported by linux then fine. If not, you will have to use ndiswrapper. 

Easiest thing to do, however, would be to go to the nearest computer shop and try different pcmcia wlan cards until one lights up :D

---

### Post by d11wtq on 2005-12-28
[QUOTE=ingo]hi,

there are a number of paths for you to take. First, you might want to try and find out which chip your card is using - googling will help.

If you find that your chipset is supported by linux then fine. If not, you will have to use ndiswrapper. 

Easiest thing to do, however, would be to go to the nearest computer shop and try different pcmcia wlan cards until one lights up :D[/QUOTE]

Don't buy another card.... that's just silly... you can't run from all hurdles ;)

You'll want to install something called ndiswrapper.  If you can get an internet connection on the wired ethernet do that... then:

```

apt-get install ndiswrapper-utils  #Installs ndiswrapper :)

```

Now you want to get your windows drivers for that network card.... (there will be a .inf file along with come other files) copy these files to linux.

```

ndiswrapper -i /path/to/windows/driver/inf/file.inf  #Install your driver
ndsiwrapper -l #Check it works... it should say driver present, hardware present
# If the lights didnt come up on your card try ejecting it and putting it back

```

If that didn't bring the lights up on your card then check this list to see if your card is listed as known to work then use the drivers they say will work (not always the official ones)

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

You may want to run this command to get the actual chipset of your card while consulting that list too:

```

lspci

```

---

### Post by Skibum on 2005-12-28
Thanks, the card I have now lights up just fine, if what you mean is that the power light comes on.:???:

---

### Post by d11wtq on 2005-12-28
[QUOTE=Skibum]Thanks, the card I have now lights up just fine, if what you mean is that the power light comes on.:???:[/QUOTE]

Yes that's what I meant.

OK next step you can do this one of two ways (using the menu GUI or using the command line).

Command line method:
```

sudo iwconfig wlan0 essid YOUR_ESSID_HERE mode managed enc restricted key ACBDEF1234567 #This may be eth1 or some other devicebut wlan0 is quite usual
# Use mode ad-hoc if not using an access point (and leave the enc and key out if you dont use WEP)
sudo ifconfig wlan0 192.168.1.3  #Your IP
# Or if you use DHCP do this instead of the above line
sudo dhclient wlan0  #Ask for IP address

```

To do it through the menu you would just go to System -> Administration -> Networking ;)

---

### Post by Skibum on 2005-12-28
Thanks, This sounds like what I need to do.  One problem though, I have no direct path to the internet until I get the card configured.  I can download stuff to this pc and use a sneaker net to get it to the notebook.

---

### Post by d11wtq on 2005-12-28
You don't need to be on the internet for any of that.  You only needed to be on the internet to do the apt-get for ndiswrapper if your card wasn't working :)

Just go to System -> Administration -> Networking and it's all there.  You should know the details for your Access point I assume (WEP keys, ESSID name etc).

---

