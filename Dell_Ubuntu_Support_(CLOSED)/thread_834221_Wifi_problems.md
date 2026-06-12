---
title: "Wifi problems"
date: 2008-06-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by bearbigears on 2008-06-19
i purchased a dell precision m4300, i installed the new ubuntu, as a dual boot with xp. i am having trouble with the wifi. i cannot get online. i have a dell wireless 1390 mini card. any help will be appreciated
thanks

---

### Post by pytheas22 on 2008-06-19
Please try following these instructions, which I am adapting from [https://help.ubuntu.com/community/WifiDocs/Driver/1390](https://help.ubuntu.com/community/WifiDocs/Driver/1390) to make them work on Hardy (if you're not using Hardy please let me know):

```
sudo rmmod ndiswrapper
sudo apt-get remove ndiswrapper-utils
sudo su
echo 'blacklist b43' >> /etc/modprobe.d/blacklist
echo 'blacklist b43legacy' >> /etc/modprobe.d/blacklist
echo 'blacklist b43 ssb' >> /etc/modprobe.d/blacklist
echo 'blacklist ssb' >> /etc/modprobe.d/blacklist
rmmod ndiswrapper
wget http://nchc.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.42.tar.gz
sudo apt-get update
sudo apt-get install build-essential linux-headers-`uname -r`
tar -zxvf ndiswrapper-1.42.tar.gz
cd ndiswrapper-1.42
sudo make uninstall
make
sudo make install
cd ..
mkdir dell-driver
cd dell-driver
wget http://ftp.us.dell.com/network/R140747.EXE
unzip -a r129832.EXE      # or $unzip -a R140747.EXE
sudo ndiswrapper -i DRIVER/bcmwl5.inf
sudo ndiswrapper -l
sudo ndiswrapper -m
sudo modprobe ndiswrapper

```

now reboot and see if you can connect.

Let me know how this goes.  There are a lot of steps and if I missed something I apologize in advance.  If this doesn't work, please post the output of:
```

lspci
cat /etc/modprobe.d/blacklist
iwconfig
```

as well as any errors you get while running the code above (some of the commands will probably produce errors and this is expected so don't worry about that, just run them all).

---

### Post by StefAndrew on 2008-06-19
> **bearbigears said:**
> i purchased a dell precision m4300, i installed the new ubuntu, as a dual boot with xp. i am having trouble with the wifi. i cannot get online. i have a dell wireless 1390 mini card. any help will be appreciated
thanks

Did you install the restricted drivers for wireless yet?  Make sure the laptop is plugged in with a LAN cable first.  Then go to System > Administration > Hardware Drivers.  Then enable the broadcom driver and make sure that you check the box to get the firmware automatically, which is why you need to be connected with cable.  This should setup wifi for you.  I have the same card in my Vostro and this resolved my issue.

Let me know how that works out.

---

### Post by pytheas22 on 2008-06-19
> Did you install the restricted drivers for wireless yet? Make sure the laptop is plugged in with a LAN cable first. Then go to System > Administration > Hardware Drivers. Then enable the broadcom driver and make sure that you check the box to get the firmware automatically, which is why you need to be connected with cable. This should setup wifi for you. I have the same card in my Vostro and this resolved my issue.


Yeah, this would probably work too and might be a better solution.  I recommended the ndiswrapper approach above because I don't know whether the native drivers work with Dell 1390 wireless, as I've never owned that kind of card and don't know which chipset it uses (probably Broadcom of some kind but not all Broadcom chips work with the b43 driver).  But if StefAndrew says it works, then go for that first; it's always better to use the native drivers, although either solution should work.

I just wanted to point this out so that the original poster wouldn't be confused as to why two completely different solutions are being offered.

---

### Post by StefAndrew on 2008-06-19
The thing I have run into so far with the b43-fwcutter I have noticed it does occasionally drop the connection.  But that's only happened once so far.  I had tried the ndiswrapper one time myself, and ran into problems, I may have messed up the steps though.  I have read that others get this card working with both b43-fwcutter and with ndiswrapper.

---

### Post by Mordac85 on 2008-06-19
I have the 1390 on my D430 and ran into the problem of it not working after running through all the ndiswrapper steps above.  Thanks to **StefAndrew** I found the missing checkbox on the firmware.  Now I'm up and running just fine.  Thanks for the head's up

---

### Post by pytheas22 on 2008-06-19
> The thing I have run into so far with the b43-fwcutter I have noticed it does occasionally drop the connection. But that's only happened once so far. I had tried the ndiswrapper one time myself, and ran into problems, I may have messed up the steps though. I have read that others get this card working with both b43-fwcutter and with ndiswrapper.

Yes, either way should work.  And actually there's a third way, bcm43xx-fwcutter, that might be more stable than b43...bcm43xx is the older version of the Broadcom driver and tends to be more reliable for most chipsets.

But for the original poster, I would recommend trying the b43 method first and hopefully that will just work.

---

### Post by Mordac85 on 2008-06-19
That's the thing, on Gutsy the ndiswrapper worked fine for me.  Now that I have a fresh build of Hardy I had to go with the fwcutter.  Odd, but it's working!

---

### Post by bearbigears on 2008-06-20
success StefAndrew it is working thank you so much. sorry it took so long to get back. had problem with my internet provider. again thanks alot
b

---

### Post by StefAndrew on 2008-06-20
> **pytheas22 said:**
> Yes, either way should work.  And actually there's a third way, bcm43xx-fwcutter, that might be more stable than b43...bcm43xx is the older version of the Broadcom driver and tends to be more reliable for most chipsets.

But for the original poster, I would recommend trying the b43 method first and hopefully that will just work.

Hmm, I wonder if I should try the older driver, because mine times out a lot now I've noticed, especially when trying to install packages.  It just hangs up while downloading packages, even though I can go to Firefox and everything works fine.  It's mostly when downloading something that the connection just stops downloading.  It's really weird.

So, should I remove the b43-fwcutter and then install the bcm43xx-fwcutter?  Like

sudo aptitude remove b43-fwcutter
sudo aptitude install bcm43xx-fwcutter

Would that work just fine?  I'll have to wait until I get home after work tonight.

I assume this might be the driver that was used in Edgy?  Because that was when my wireless worked flawlessly, but since then, I've had trouble with wifi.

Thanks for pointing this out.

Oh, and I'm glad this got both of you guys up and running.  I'll keep you posted on how the other driver works for me.

---

### Post by pytheas22 on 2008-06-20
I know that Ubuntu used the bcm43xx driver at least since Feisty, when I first switched over from Fedora, and possibly earlier.  So if your card worked in Edgy and you weren't using ndiswrapper, you must have been on bcm43xx.

Yes, removing b43-fwcutter and installing bcm43xx-fwcutter is what you need to do.  You'll be asked if the firmware should be automatically fetched; say yes.

You also have to blacklist b43 and unblacklist bcm43xx for it to work, so open /etc/modprobe.d/blacklist in a text editor and delete the line that says "blacklist bcm43xx," and then add to the file these lines:

```
blacklist b43
blacklist b43legacy
blacklist b43 ssb
blacklist ssb
```

then install bcm43xx-fwcutter, and reboot and hopefully you'll be back to where you were with Edgy.  If at first you can't connect, try running the command "sudo modprobe bcm43xx" and try again.

If for some reason this doesn't work and you want to go back to b43, just add bcm43xx back to the blacklist and remove the lines related to b43, and install b43-fwcutter again.  b43 is supposed to provide more features than bcm43xx, but unfortunately b43 is not really as mature as it should be and can be unreliable.  I wish they'd waited a little longer before pushing it into Ubuntu.  Fedora pushed it into the stable release a year ago, when it was a real disaster, which was my main reason for switching to Ubuntu to begin with.

---

