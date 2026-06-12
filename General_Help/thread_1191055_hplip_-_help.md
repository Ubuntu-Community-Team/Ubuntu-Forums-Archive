---
title: "hplip - help"
date: 2009-06-18
forum: General Help
---

### Post by mrfotheringham on 2009-06-18
I have a HP Deskjet F380 all-in-one and trying to install it.
I have used Synaptic to install hplip 3.9.2-3 ubuntu4.
What do I do now?

Pls help

---

### Post by lindsay7 on 2009-06-18
Go to the menu bar on top of the page and click on system/administration/printing. It may see your printer by itself. If now click on new and see if it finds it. You may have to click on one of the choices if it does not.

---

### Post by The Cog on 2009-06-18
You can alsp install **hplip-gui** and look in System->Preferences->HPLIP Toolbox for a neat little GUI.

---

### Post by mrfotheringham on 2009-06-18
Thanks hplip-gui intalled and used but rely is No installed HP devices found

printers seem impossible with Linux!!! Having also tried ip1900 for a while

Appreciate help though:KS

---

### Post by sgosnell on 2009-06-18
Printers are easier to install in Ubuntu than in Windows.  Open System/Administration/Printing, select Network printer, and it should find your printer and install the drivers for it.  All you have to do is enter your password when prompted.  Make sure the printer is turned on, and connected to the router, and it should be a piece of cake.  If it's a USB printer, connect it, and it's even easier.

---

### Post by mrfotheringham on 2009-06-18
I can't find network printing

---

### Post by mrfotheringham on 2009-06-18
Why such little printer support?

---

### Post by dje on 2009-06-18
umm, with what printer. I have had great support with 4 HP printers on Ubuntu

---

### Post by lisati on 2009-06-18
What sort of printer? My Epson C63 is supported "out of the box", and my Epson CX3900 scanner/printer can be made to work by pretending that it's another model.

---

### Post by t4thfavor on 2009-06-18
I have never had an issue installing any printer on Ubuntu. Including Toshiba, HP, Rico, and a slew of other brands I can't remember.

The key is understanding that the driver may have 100 printers rolled into it, so you may have to use say a Generic Toshiba Driver for some model that is not listed on the support page.


I.E: For a while I used the PSC900 driver for a PSC1210, because the PSC1210 was not on the list, and it worked perfectly

---

### Post by mrfotheringham on 2009-06-18
I've got a HP Deskjet F380 all in one. Been to HP - redirected and visited live and archived forums. I'm not that Terminal savvy etc but would appreciate help.

---

### Post by Sef on 2009-06-18
> I can't find network printing


Are you trying to hook your printer up to a network?  If so, could you please explain the set up.  Thank you.

---

### Post by mrfotheringham on 2009-06-18
mmmr obr so sweet:popcorn:

---

### Post by lisati on 2009-06-18
What happens when you plug in the printer and click on System->Administration->Printing? HP printers are quite well supported.

---

### Post by lisati on 2009-06-18
Why two threads about the same problem?
[http://ubuntuforums.org/showthread.php?t=1191055](http://ubuntuforums.org/showthread.php?t=1191055)

---

### Post by dje on 2009-06-18
I'm not sure of the exact process in Xubuntu (in GNOME it is under System >> Administration >> Printing). You should be able to find the printer configuration somewhere in the xfce menus. You will then be able to add a new printer and use the Deskjet F300 driver which should work

---

### Post by mrfotheringham on 2009-06-18
I'm desperate. Sorry for double post. Patience is a virtue. But still my printer lonely bleeds....not

---

### Post by bobnutfield on 2009-06-18
> **mrfotheringham said:**
> I'm desperate. Sorry for double post. Patience is a virtue. But still my printer lonely bleeds....not

When adding your printer, simply choose the Deskject_F300_series and your printer will be detected and work just fine.  I have that printer and know that it will work out of the box.

---

### Post by mrfotheringham on 2009-06-18
It's not there by the way in on  ubutnu if that makes a differnce?

More help advice gateful

---

### Post by mrfotheringham on 2009-06-18
Will try now !!!!!

---

### Post by mrfotheringham on 2009-06-18
I have default printers set on preferences to remove first, although no printers installed.
Please advise

---

### Post by mrfotheringham on 2009-06-18
ubuntu remove default printer ?

---

### Post by Amilo1718 on 2009-06-18
euhm?
what did you say?

---

### Post by ZackM on 2009-06-18
Yes... That was poorly phrased..

---

### Post by Vunutus on 2009-06-18
You're going to have to type coherently if you want an answer.

---

### Post by t4thfavor on 2009-06-18
[http://ubuntuforums.org/showthread.php?t=1191055](http://ubuntuforums.org/showthread.php?t=1191055)

---

### Post by kuja on 2009-06-18
Well, if you have hplip installed and you don't see your printer listed, then you probably need to install hpijs and foomatic-db-hpijs.

---

### Post by mrfotheringham on 2009-06-22
Thanks all for the advice I have now installed HPLIP Status Service in the system tray. It is running on the foomatic driver. Device manager allows me to scan and shows ink level etc. However doesn't print a test page, the little black notification box pops up from the top right advising me that test page has been printed but nothing from the printer. Any suggestions much appreciated.

---

### Post by Vhann on 2009-06-22
> **mrfotheringham said:**
> I have a HP Deskjet F380 all-in-one and trying to install it.
I have used Synaptic to install hplip 3.9.2-3 ubuntu4.
What do I do now?

Pls help

Ok, so assuming this is the All-in-One printer we are talking about: [http://h10010.www1.hp.com/wwpc/sg/en/ho/WF06b/18972-18972-238444-410635-410635-1129389-1129382.html](http://h10010.www1.hp.com/wwpc/sg/en/ho/WF06b/18972-18972-238444-410635-410635-1129389-1129382.html)
it can only be USB-connected, so forget everything anyone said about network, router and such.

Also, I believe the easiest and best way to configure a printer under GNU/Linux is via CUPS, so here's how to do it:
1- Open a web browser (Mozilla Firefox for example)
2- Enter "localhost:631" in the address bar (without the double quotes)
3- If asked for login credentials, supply your superuser credentials (should be the same as what you type when booting the computer)
4- Assuming you entered the good credentials, you should now be in CUPS. In the 'Home' tab, click on the 'Add Printer' button.
5- The tab should now read 'Add New Printer' with blank fields to fill. Fill in the blanks with whatever you want to and hit 'Continue' button.
6- As I was to continue this, I hit 'CUPS USB printer' in Google and found this: [http://osr600doc.sco.com/en/PR_gimpprint/x456.html](http://osr600doc.sco.com/en/PR_gimpprint/x456.html) ... no reason to continue this howto post then...

Regards,
Vhann

---

### Post by mrfotheringham on 2009-06-22
> **Vhann said:**
> Ok, so assuming this is the All-in-One printer we are talking about: [http://h10010.www1.hp.com/wwpc/sg/en/ho/WF06b/18972-18972-238444-410635-410635-1129389-1129382.html](http://h10010.www1.hp.com/wwpc/sg/en/ho/WF06b/18972-18972-238444-410635-410635-1129389-1129382.html)
it can only be USB-connected, so forget everything anyone said about network, router and such.

Also, I believe the easiest and best way to configure a printer under GNU/Linux is via CUPS, so here's how to do it:
1- Open a web browser (Mozilla Firefox for example)
2- Enter "localhost:631" in the address bar (without the double quotes)
3- If asked for login credentials, supply your superuser credentials (should be the same as what you type when booting the computer)
4- Assuming you entered the good credentials, you should now be in CUPS. In the 'Home' tab, click on the 'Add Printer' button.
5- The tab should now read 'Add New Printer' with blank fields to fill. Fill in the blanks with whatever you want to and hit 'Continue' button.
6- As I was to continue this, I hit 'CUPS USB printer' in Google and found this: [http://osr600doc.sco.com/en/PR_gimpprint/x456.html](http://osr600doc.sco.com/en/PR_gimpprint/x456.html) ... no reason to continue this howto post then...

Regards,
Vhann
In CUPS

Printer driver: HP Deskjet 320 Foomatic/pc13 (recommended)
Printer state : idle, accepting jobs, published.
Device URI : hp:/usb/Deskjet_F300_series?serial=CN69CG632F04KH

In HPLIP Device Manager

Printer is set to default

In advanced settings Commands 

Print: [COLOR=Red][blank no information]   [/COLOR]
Scan: /usr/bin/xsane_V%SANE_URI5

Is it correct for printer field to be blank?
With info I have provided should printer work?

More help appreciated

---

### Post by mrfotheringham on 2009-06-22
Thankyou everyones help. I think printer is kaput so I am ending this posting

Cheers

---

