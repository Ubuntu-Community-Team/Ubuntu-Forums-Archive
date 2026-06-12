---
title: "WLAN+Bluetooth 1.2 PCI Card Installation"
date: 2005-12-07
forum: General Help
---

### Post by soup440 on 2005-12-07
I recently bought [http://www.newegg.com/Product/Product.asp?Item=N82E16833158121]("http://www.newegg.com/Product/Product.asp?Item=N82E16833158121") this card and I was wondering how to install it in linux. It comes in on friday, any help would be appreciated.

Thanks!

---

### Post by Lambert on 2005-12-08
There's not a whole lot of information on this device where it comes to linux. All you can do is intall it, power up and then run this command to check for a driver.

sudo lshw

Look for the device in the list and see if a driver loads. should be in a line starting with configuration: then it will say driver=xxxx

If it has a driver then just go into system>admin>network and configure the device.

I don't know much about bluetooth and linux but you can search the forums as there are posts about it. Or look [here]("http://ubuntuforums.org/showthread.php?t=34740") to see if it will help you. 

If you don't have a driver loaded then the best place to start is contact the manufacture and see what they say about linux support. Or play around with google to see if there is something you can find.

good luck.

---

