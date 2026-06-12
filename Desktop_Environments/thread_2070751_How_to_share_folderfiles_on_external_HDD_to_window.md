---
title: "How to share folder/files on external HDD to windows 7"
date: 2012-10-13
forum: Desktop Environments
---

### Post by kruget on 2012-10-13
I got 1 external HDD filled with movie, connected via USB to my netbook that using Xubuntu as it OS.

This netbook also connected to internet using an USB CDMA modem, which is already shared to the network using unused adsl modem (set to full bridge), so everyone surfing the internet using my netbook as server.

I want to share this external HDD to network so other pc using windows 7 could watch the movie. 

Please explain how to do that.

---

### Post by kruget on 2012-10-17
Am i posted in the wrong forum :confused:

---

### Post by bart.a on 2012-10-17
you could use samba to setup a shared directory..

You can find a detailed discription on how to do that [here]("http://help.ubuntu.com/12.04/serverguide/samba-fileserver.html")

Please come back to the forum if it did or didn't work.. good luck setting up..

---

### Post by kruget on 2012-10-22
> **bart.a said:**
> you could use samba to setup a shared directory..

You can find a detailed discription on how to do that [here]("http://help.ubuntu.com/12.04/serverguide/samba-fileserver.html")

Please come back to the forum if it did or didn't work.. good luck setting up..

Thank You, Bart

I followed your link, also learning few tricks from a thread in [askubuntu]("http://askubuntu.com/questions/101350/software-similar-to-nautilus-share-in-thunar").
Resulted in partially success: I can watch the movie on external hdd plugged on server from other pc runing ubuntu or android cellphone. By manually go to 10.42.0.1.
 
But still unable to connect from windows pc, although i can surf internet normally using the shared internet.

Will give another try after i got the time and energy to tinker with samba.

---

### Post by bart.a on 2012-10-22
In your samba configuration file [/etc/samba/smb.conf]
you should be able to configure a netbios name, which should allow you to make a permanent network connection in windows..

[here you will find the GUI way..]("http://www.noobslab.com/2012/03/configure-samba-sharing-between-ubuntu.html") maybe you prefer this over the terminal way.. 

I use it all the time.. for a usb drive on win7 shared with ubuntu laptop and at work from ubuntu server to a couple of windows7 workstations and back from one workstation to the server.. works perfectly..

when you find the time, read carefully and take the time to make it work.. And when it doesn't work properly, report back to the forum.. we'll be there..

---

