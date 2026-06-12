---
title: "Am not able to take printout in windows shared printer from ubuntu 14.04"
date: 2014-05-03
forum: Desktop Environments
---

### Post by sundarrajan2 on 2014-05-03
[COLOR=#333333][FONT=Ubuntu]Am configured USB printer in windows 7 desktop and shared. i am able to take print out from windows desktop and not able to take print out from ubuntu.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Configuiration Details attached PFA,

[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]am installed samba also....[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Please assist me on this............[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Thanks In advance[/FONT][/COLOR]

---

### Post by macachuto on 2014-05-03
Do you know username and password to that share?
Can you print if connect this printer directly to USB on Linux?

---

### Post by deadflowr on 2014-05-03
What are the sharing settings for the windows machine?

You should already have the needed samba client packages on Ubuntu, but the share is on the windows side.

Is file/print sharing enabled on win7?

---

### Post by sundarrajan2 on 2014-05-05
am disabled asking password in windows 7

need to check on direct connection.i'l check and get back to you.
Thank you so much for reply..........

---

### Post by sundarrajan2 on 2014-05-05
am shared printer. am able to take print out from other windows machine.
am installed samba also ?

its  not working....

Please guid me.....

Thank you so much for your reply

---

### Post by deadflowr on 2014-05-05
As I said, I don't really think samba was needed in this case, as samba would give windows access to share on the Ubuntu side.
Ubuntu comes with a samba client already, which will allow you to connect to the Windows printer.

That said, try this:
On Ubuntu open up the program "Printers"
click on Add
In the add windows click on Network Printer > Find Network Printers
Windows via samba should show up in the bottom of the list.
In the right side window where the URI is click on Browse.
This will browse the Network shares.
It should list the shared domain > then the shares computers > then the shared Printers.
Click on the printer you want to connect and then click OK(or enter)
Now the share you want is properly listed, click OK and follow the direction to install the drivers for it.
In the list of drivers scroll down to the HP listing and when it highlights click Ok.
In the HP drivers window, the LaserJet options are somewhere in the middle of the list so you'll have to scroll down to it.
I believe the driver for your printer is listed.
when You highlight you driver click OK, and it will begin to install the driver.
When it is installed, it will bring up a page to either leave as is, or print a test page.
Choose either option and you should be good to go.

Edit: If you have to authenticate the print job, put the username and password in the box that says so when at the first window.(It should have username and password, with a verify button.)
It will probably save you any frustrations down the road.

---

