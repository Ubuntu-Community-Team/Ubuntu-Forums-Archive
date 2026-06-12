---
title: "Xerox C3545 WorkCenter Pro"
date: 2006-06-13
forum: Desktop Environments
---

### Post by soop on 2006-06-13
Has anyone managed to get this to work? I've downloaded the driver from xerox Linuxi386XPXX_4.00.25.tar but every time I run it I get the following:


................ERROR: No such file or directory


Any ideas?

Thanks

---

### Post by rbalfour on 2006-06-13
Did you un-tar it first?
It's in an archive format.

---

### Post by soop on 2006-06-13
Yup ... it was untarred which created the following:

Linuxi386XpxxInstall:
disks         isize       pkg_tar.z2  pkg_tar.z4  pkg_tar.z6  pkg_tar.z8  setup
installf.rom  pkg_tar.z1  pkg_tar.z3  pkg_tar.z5  pkg_tar.z7  readme      tsize


Setup being the install file .... you run sudo ./setup and you get the error

---

### Post by soop on 2006-06-19
FOund out that if i install the generic ppd file and then install a docucentre 400 and then change the driver to the c3545 ppd file it seems to work, not sure about advanced feature set yet though.


cheers

---

### Post by Georgie-o on 2006-08-29
I am having the same problem you had.  I followed your suggestion and installed the Document Centre 400.  But I still don't see a way to install the .tar or the unpacked file.  The printer setup says it needs a ppd file, but none are in the folder.  Any help?

---

### Post by nserdinsky on 2006-09-08
I downloaded the Printer Model Package from Zerox:
[http://www.support.xerox.com/go/getfile.asp?Xlang=en_US&XCntry=USA&objid=49943&EULA=1&prodID=WCPC2128_WCPC2636_WCPC3545&Family=WorkCentre%20Pro&ripId=&langs=English%20(US)&plats=Linux&Xtype=download&uType=](http://www.support.xerox.com/go/getfile.asp?Xlang=en_US&XCntry=USA&objid=49943&EULA=1&prodID=WCPC2128_WCPC2636_WCPC3545&Family=WorkCentre%20Pro&ripId=&langs=English%20(US)&plats=Linux&Xtype=download&uType=)

Then untarred it in my home dir. The setup script does not function, but if you then open the New Printer dialog and add driver. The driver is the xr_WorkCentreProC2128.ppd file. Once I did that, the printer worked fine.

---

### Post by tworkemon on 2006-10-18
I tried the above and it kept giving me syntax error... Using Edgy, KDE. Any ideas ??

---

### Post by dwanders on 2006-12-19
> **nserdinsky said:**
> I downloaded the Printer Model Package from Zerox:
[http://www.support.xerox.com/go/getfile.asp?Xlang=en_US&XCntry=USA&objid=49943&EULA=1&prodID=WCPC2128_WCPC2636_WCPC3545&Family=WorkCentre%20Pro&ripId=&langs=English%20(US)&plats=Linux&Xtype=download&uType=](http://www.support.xerox.com/go/getfile.asp?Xlang=en_US&XCntry=USA&objid=49943&EULA=1&prodID=WCPC2128_WCPC2636_WCPC3545&Family=WorkCentre%20Pro&ripId=&langs=English%20(US)&plats=Linux&Xtype=download&uType=)

Then untarred it in my home dir. The setup script does not function, but if you then open the New Printer dialog and add driver. The driver is the xr_WorkCentreProC2128.ppd file. Once I did that, the printer worked fine.
This worked fine for me, but there are no options to access other paper trays. Dont suppose anyone found some nifty steps to access other paper trays?

---

### Post by tworkemon on 2007-02-07
> **nserdinsky said:**
> I downloaded the Printer Model Package from Zerox:
[http://www.support.xerox.com/go/getfile.asp?Xlang=en_US&XCntry=USA&objid=49943&EULA=1&prodID=WCPC2128_WCPC2636_WCPC3545&Family=WorkCentre%20Pro&ripId=&langs=English%20(US)&plats=Linux&Xtype=download&uType=](http://www.support.xerox.com/go/getfile.asp?Xlang=en_US&XCntry=USA&objid=49943&EULA=1&prodID=WCPC2128_WCPC2636_WCPC3545&Family=WorkCentre%20Pro&ripId=&langs=English%20(US)&plats=Linux&Xtype=download&uType=)

Then untarred it in my home dir. The setup script does not function, but if you then open the New Printer dialog and add driver. The driver is the xr_WorkCentreProC2128.ppd file. Once I did that, the printer worked fine.

The above did not work for me using Feisty.

---

### Post by ken_fallon on 2007-06-05
You need to run the command ```
cat pkg_tar.z* >> pkg.tar
```  to create a tarfile that you can then extract with the command ```
tar xvf pkg.tar
```

---

### Post by vapore0n on 2007-10-04
What I did was:
download the XP drivers
extract only the PPD file corresponding to the 3545 printer (xw45cp5q.ppd)
install the printer specifiying the ppd file

done

---

