---
title: "Compatible with..."
date: 2005-12-31
forum: General Help
---

### Post by aninnocentbystander on 2005-12-31
Hey all...I was wondering if ubuntu is compatible with my Linksys wireless router. 
The model number is WUSB54G. Here is a link for a photo and more info. 



[http://www.bestbuy.com/site/olspage.jsp?skuId=5974065&type=product&id=1061769818475]("http://www.bestbuy.com/site/olspage.jsp?skuId=5974065&type=product&id=1061769818475")

Thanks a bunch,

Keenan "AnInnocentBystander" :smile:

---

### Post by cwaldbieser on 2005-12-31
[QUOTE=aninnocentbystander]Hey all...I was wondering if ubuntu is compatible with my Linksys wireless router. 
The model number is WUSB54G. Here is a link for a photo and more info. 



[http://www.bestbuy.com/site/olspage.jsp?skuId=5974065&type=product&id=1061769818475]("http://www.bestbuy.com/site/olspage.jsp?skuId=5974065&type=product&id=1061769818475")

Thanks a bunch,

Keenan "AnInnocentBystander" :smile:[/QUOTE]

The router is normally not a problem.  If you have networking hardware difficulties, it is more often that Ubuntu doesn't recognize the wireless card/adapter you are using.

---

### Post by Jammy_Stuff on 2005-12-31
If you look [here]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List") yours is number 19 of L. It says it works fine but remember to grab the latest driver.

---

### Post by aninnocentbystander on 2005-12-31
Alright, thanks a bunch, wanted to get that cleared up :D 



                  -Keenan "aninnocentbystander"

---

### Post by aninnocentbystander on 2006-01-01
Hey all,

       OK, so I thought I would take it for a spin. I booted up LiveCD with no problems, and couldn't connect to the network. I'm not really an internet buff, so if it's at all possible step by step would be nice. Thanks again.

  -Keenan "aninnocentbystander"

---

### Post by Jammy_Stuff on 2006-01-01
Okay then. You are setting it up to connect to a wireless network right? Okay then. Ubuntu can't do this by default and it doesn't work on the live CD. It will work on a proper install though.

Once you have installed Ubuntu, connect your wireless thing and open Synaptic package manager. Search for ndiswrapper, mark any results that come up and click apply. 

Make a new directory in your home called windows_drivers and copy the .inf file (get from a PC that you've installed it on) to the directory.

Then open a terminal and type:

```
ndiswrapper -i ~/windows_drivers/(name of inf file).inf
```

Then:

```
ndiswrapper -m
```

Then:

```
modprobe ndiswrapper
```

It should now be installed. To check type:

```
ndiswrapper -l
```

It should say that the drivers and hardware are present.

Then type:

```
sudo gedit /etc/modules
```

and add ndiswrapper to the bottom. Save and close.

Then just follow [this]("https://wiki.ubuntu.com/WiFiHowto") guide.

---

### Post by aninnocentbystander on 2006-01-01
Alright, I guess I'll give that a shot. Thanks a bunch


             -Keenan "aninnocentbystander"

---

