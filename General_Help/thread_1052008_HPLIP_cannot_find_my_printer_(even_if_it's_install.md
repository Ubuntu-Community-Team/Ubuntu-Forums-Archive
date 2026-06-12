---
title: "HPLIP cannot find my printer (even if it's installed)"
date: 2009-01-27
forum: General Help
---

### Post by dodjob on 2009-01-27
Hi Everybody!
I'm not sure to have posted in the right section... if not please don't kick me out I need an answer ;)
Well, It will be the 1000000000th post from a newbie but.. that's what I am :)
I've an HP Photosmart C4340 plugged on a Fritzbox by usb. My Laptop is linked via W-lan to this box.
I've succeeded to install my printer via Cubs or via the original  system-config-printer implemented in MY Kubuntu Intrepid :)
But i don't know why my "HP linux Imaging and Printing" <-- I think it's HPLIP :) keeps me saying that he cannot find it.
I can already print documents with "system-config-printer" but not using the scan nether the fax (I thinks it's anyway not supported yet) or any adanced settings.
Please help :-)
Ooops I've forgot Please be patient, as I'm a newbie (and comming from Windows) I'm very not comfortable with the terminal :)
Hope someone as traduced correctly my script :)
greetings,
Dodjob

---

### Post by timcredible on 2009-01-27
you can check [www.linuxprinting.org](www.linuxprinting.org), but i don't think scanning is available via IP yet.

---

### Post by sandyd on 2009-01-27
Scanning is possible my friend :)

look here. 

[http://hplipopensource.com/hplip-web/models/photosmart/photosmart_c4340_series.html](http://hplipopensource.com/hplip-web/models/photosmart/photosmart_c4340_series.html)

click on the download button and follow the instructions there

hope this helps

---

### Post by wolfen69 on 2009-01-27
download [this]("http://prdownloads.sourceforge.net/hplip/hplip-2.8.12.run") and put it in your home folder. then open a terminal and: ```
sh hplip-2.8.12.run
```
choose automatic install and let it run.
then install HPLIP Toolbox. ```
sudo apt-get install hplip-gui
``` this will give you access to advanced settings and features for your printer. it will show up in system>preferences as HPLIP Toolbox.

you can use Xsane image scanner for scanning. (applications>graphics>xsane)

---

