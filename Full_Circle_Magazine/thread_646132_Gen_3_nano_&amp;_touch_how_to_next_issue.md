---
title: "Gen 3 nano &amp; touch how to next issue?"
date: 2007-12-20
forum: Full Circle Magazine
---

### Post by frup on 2007-12-20
With the Christmas season a few Ubuntu members might find themselves with new iPods, my girlfriend included.

As is well known these do not currently work out of the box on 7.10 and it may be good for the next issue to include a little guide on how to get it working.

I bought the fatty believing it was only the ipod touch that was affected, and when going home to preload her favourite music on it discovered that I had serious issues... Neither of our families has windows but hers does have a mac... but ideally she would want linux access.

This thread got everything working
[http://ubuntuforums.org/showthread.php?t=611404&highlight=New+Generation+Ipod](http://ubuntuforums.org/showthread.php?t=611404&highlight=New+Generation+Ipod)

> **paradoxni said:**
> Ok Im getting a new gen ipod soon and have been investigating this myself. I cannot test it as I dont have the thing yet but I can tell you what I have learned so far.

in a terminal:
```
sudo apt-get install libsgutils1 libsgutils1-dev

```

then download libgpod 0.6 if you havent already (if you have you need to recompile it again with the above packages now installed)

[http://sourceforge.net/project/showfiles.php?group_id=67873&package_id=156254&release_id=553119](http://sourceforge.net/project/showfiles.php?group_id=67873&package_id=156254&release_id=553119)

extract the contents of this archive (I downloaded it to my desktop and right clicked and chose 'extract here')

open a terminal and change to the extracted directory
```
cd Desktop/libgpod-0.6.0
./configure
make
sudo make install

```

Now thats done you should have  an 'ipod-read-sysinfo-extended' tool available.

```

ipod-read-sysinfo-extended DEVICE MOUNTPOINT

```
e.g. ipod-read-sysinfo-extended /dev/sda /media/ipod

according to what i have read this will store your firewireID on the ipod so your music will be visible once you add all your music to your ipod again e.g. using rythmbox

> **paradoxni said:**
> Ok I got hold of a new gen IPOD nano to test this out and was getting the same problem as you, empty IPOD even with songs uploaded to it with Rythmbox. I fixed it thou...

Delete the old libgpod libraries:
```
 sudo rm /usr/lib/libgpod.so.2.0.0
sudo rm /usr/lib/libgpod.so.2
```

Create links to the new one:
```

sudo ln -s /usr/local/lib/libgpod.so.3 /usr/lib/libgpod.so.3
sudo ln -s /usr/local/lib/libgpod.so.3 /usr/lib/libgpod.so.2

```

ipod-read-sysinfo-extended is supposed to create SysInfo file on IPOD with FirewireID inside, but it did not work here, so I added it manually:

Connect IPOD to PC, then
```

sudo lsusb -v | grep -i Serial

```

Note down your FirewireID from the list, its the 16 digit one.
```

 iSerial                 1 0000:00:1a.1
  iSerial                 3 000A27001AD21163  <---- IPOD FirewireID
  iSerial                 3 3547160158733600
          line coding and serial state
          line coding and serial state
  iSerial                 0 
  iSerial                 1 0000:00:1d.7
  iSerial                 1 0000:00:1d.1
  iSerial                 1 0000:00:1d.0
  iSerial                 1 0000:00:1a.0
  iSerial                 0 
  iSerial                 0 
  iSerial                 0 
  iSerial                 1 0000:00:1d.2
  iSerial                 0 
  iSerial                 3 060114014271000001
  iSerial                 1 0000:00:1a.7

```

Create SysInfo file on IPOD (assuming IPOD mounted at /media/IPOD):

```

sudo gedit /media/IPOD/iPod_Control/Device/SysInfo

```

SysInfo should only contain:
```

FirewireGuid: 0x<your firewire ID>

e.g. FirewireGuid: 0x000A27001AD21163

```



Now load up Rhythmbox and remove songs from the IPOD, then put songs back on IPOD, then eject IPOD (rhythmbox may freeze for a short while).

Songs should now be visible on IPOD.

Personally I have upgraded libgpod on two 7.10 machines with no problems. My girlfriends machine which will be the primary updater of the ipod has 6.10 currently and within the next few days I will be playing with that, I hope it works but will certainly be upgrading her system if it doesn't (first need for her since 6.10)

I have no idea if there is an easier method than this, apparently updating the libgpod allows gtkpod, rhythmbox and amarok all to work with the new ipods... my ipod 60gb video faced no regressions.

---

### Post by superm1 on 2007-12-25
FYI:

Most of this is automated on the packages available here:
[https://help.ubuntu.com/community/iPhone](https://help.ubuntu.com/community/iPhone)

---

