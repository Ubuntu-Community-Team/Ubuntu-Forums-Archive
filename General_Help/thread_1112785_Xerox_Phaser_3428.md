---
title: "Xerox Phaser 3428"
date: 2009-04-01
forum: General Help
---

### Post by cjtjamandra on 2009-04-01
Anyone her e have installed this printer?

I have installed this network printer using the Phaser 3425 driver, the job is successfully sent. But nothing happens in the printer, it is not printing and it seems that it's not receiving the print job. The printer is working fine using windows.

---

### Post by halitech on 2009-04-09
it should work fine in windows, it has windows drivers but both the 3428 and the 3425 do not have a linux driver so I would be very surprised if you get it to work.

[http://www.support.xerox.com/go/results.asp?Xlang=en_ZA&XCntry=ZAF&prodID=3428&ripId=&Xtype=download](http://www.support.xerox.com/go/results.asp?Xlang=en_ZA&XCntry=ZAF&prodID=3428&ripId=&Xtype=download)

Edit: not that its practical but you could use drag and drop in the CWIS to print if it has the CWIS feature.

---

### Post by andrecardoso on 2009-07-21
A friend solved this problem installing the printer with the Xerox Phaser 3450 driver.

I tried myself and it works!

---

### Post by mudcat on 2009-07-21
Yea the 3450 driver works. Also note that for some of their products (ie. Xerox Workcentre) they have posted incorrect drivers.

---

### Post by jpfreire on 2010-01-19
> **andrecardoso said:**
> I tried myself and it works!x 2

if printer does not show up in cups, the drivers:
[http://www.support.xerox.com/go/results.asp?Xtype=download&prodID=3450&Xlang=en_ZA&Xcntry=ZAF](http://www.support.xerox.com/go/results.asp?Xtype=download&prodID=3450&Xlang=en_ZA&Xcntry=ZAF)

within "readme" it mentions model folder: i have put files in /usr/share/ppd/splix/xerox

---

