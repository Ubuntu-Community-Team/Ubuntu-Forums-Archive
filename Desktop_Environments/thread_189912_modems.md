---
title: "modems"
date: 2006-06-05
forum: Desktop Environments
---

### Post by manic on 2006-06-05
hi people can anyone tell me how to get a zoom adsl usb broadbandband modem working on ubuntu?, im running microgrot and hate , wanting to change to linux but i do desperately need the drivers for this modem in linux (yes i have them in windows),iv checked the zoom official site but to no avail
can anyone help or advise? it would be much appreciated
thanks:-k

---

### Post by temcat on 2006-06-06
[QUOTE=manic]hi people can anyone tell me how to get a zoom adsl usb broadbandband modem working on ubuntu?, im running microgrot and hate , wanting to change to linux but i do desperately need the drivers for this modem in linux (yes i have them in windows),iv checked the zoom official site but to no avail
can anyone help or advise? it would be much appreciated
thanks:-k[/QUOTE]

Your modem may be supported by eciadsl driver ([http://eciadsl.flashtux.org](http://eciadsl.flashtux.org)), if it's Zoom 5510 ADSL model. The Zoom 5510 - 72 -00 ADSL version is specifically listed as NOT supported on the website. The version of the driver that is in Dapper repositories didn't work for me, but a kind soul sent me a working .deb which I attach here. If your modem is supported, do the following. 

First unzip the archive:

```
gunzip eciadsl-usermode_0.11-1+dapper+alv01_i386.deb.gz
```

Then install it with the following command:

```
sudo dpkg -i eciadsl-usermode_0.11-1+dapper+alv01_i386.deb
```

To configure the driver, run:

```
sudo eciadsl-config-text
```

Answer to the questions of the script. When done, try to connect:

```
sudo eciadsl-start
```

If it doesn't work, check the settings. if they are correct, you may need to get additional synch files (see download links and istallation instructions at [http://eciadsl.flashtux.org/download.php](http://eciadsl.flashtux.org/download.php)).

---

### Post by Malac on 2006-06-11
Okay I have posted a full "walkthrough" for Zoom 5510-72 USB Modem in the General Howto Section of the Forums for "Dapper".

The link is here:
[http://www.ubuntuforums.org/showthread.php?t=194237]("http://www.ubuntuforums.org/showthread.php?t=194237")

Hope this helps any problems let me know.

---

