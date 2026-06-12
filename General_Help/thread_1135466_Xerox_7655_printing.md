---
title: "Xerox 7655 printing"
date: 2009-04-24
forum: General Help
---

### Post by ronin2307 on 2009-04-24
Hi,
pretty new to linux, so I am wondering if there is any special trick to making Ubuntu print color prints. there is no preinstalled driver for 7655 so i used the 7345 driver, set the option to print color ALWAYS, try to print and anywhere on the page where there should be color, i can only see very faded black ink.
any help will be appreciated

---

### Post by slick666 on 2009-05-18
A quick solution is to use the generic PPD file. On Xerox's website you won't find the file under linux you need to follow this route.

[LIST=1]
[*]Go to [www.xerox.com](www.xerox.com).
[*]Support and Drivers.
[*]In the "Enter product name or number" enter **WorkCentre 7655**.
[*]Click **Drivers & Downloads**.
[*]Under **Operating Systems** click **All** then click the go button.
[*]On the long list search for **Generic PPD (Rev 2.0)**. There will be multiple entries but they all point to the same file.
[*] download and extract the zip file.
[*]When installing the printer at the of **Choose Driver** select **Provide PPD file**
[*]Use the dialog to navigate the folder that you downloaded and select the xrx7655.ppd file
[*]Select the options that seem to fit your printer closest
[*]Continue as prompted
[/LIST]

This gets you pretty much all of the functionality but there are some little quirks here and there if you are trying to do something special. There is also a Linux Driver supplied by Xerox but most of the instructions are aimed and Fedora and Suse so I haven't gotten it working just yet.

Additionally if your looking for information on your printer specifically you can go to the machine , press the "Machine Status" button, and from there print a **Configuration Report**. This print will have ALL the information you ever wanted to know about your printer.

Also this should work for 7665 and 7675 according to Xerox.

---

### Post by halitech on 2009-05-19
actually I just checked and the Printer Model Package has a PPD file specific for the WC 7655 that should work better

[http://www.support.xerox.com/go/getfile.asp?Xlang=en_ZA&XCntry=ZAF&objid=74334&EULA=1&prodID=WC7655_WC7665&Family=WorkCentre&ripId=&langs=English&plats=Linux&Xtype=download&uType=](http://www.support.xerox.com/go/getfile.asp?Xlang=en_ZA&XCntry=ZAF&objid=74334&EULA=1&prodID=WC7655_WC7665&Family=WorkCentre&ripId=&langs=English&plats=Linux&Xtype=download&uType=)

the rest of slicks instructions should work though

---

### Post by ronin2307 on 2009-05-20
when i was messing with this problem first I recall using the generic driver/ppd file (can't remember how i found out about it though) and that didn't work either. I will try it again and see if I may have missed a step or something.
thanks for the help anyway

---

### Post by karatedog on 2010-06-03
You guys rock! This just solved my problem not being able to print in color...

---

