---
title: "Can anyone help with &quot;ChromeBuntu&quot; for some netbooks?"
date: 2011-08-23
forum: Desktop Environments
---

### Post by ajmctaggart on 2011-08-23
So...here's the deal.

30 Netbooks are going to be used solely for Academic Tutoring (1 Website that students will go to).

That's it - no LibreOffice, no Learning Games, nothing...

I would love to buy Chromebooks for this function, but in reality (unless Google responds to me soon with discounted netbooks) I need another solution.

I've got 1 netbook out and open for testing running Ubuntu Natty completely updated with 2 accounts.

Administrator
Student

I need to figure out how to mimic a Chromebook as much as possible.  Meaning:

1.  Hiding Unity, applications, anything but the browser.
2.  Minimize all services running to only those absolutely necessary.
3.  Have very little that a 5-10 year old could screw up - meaning when that netbook gets turned on it goes straight to Chrome with the site needed for the HomePage.
4.  Students can only use browser - no access to downloads, no option to open other programs.

Any suggestions?

---

### Post by theplatapi on 2011-08-23
Have you looked into Chromebooks for education? You can get them for $20 a month. Details here:[http://www.google.com/chromebook/business-education.html#business-education-pricing](http://www.google.com/chromebook/business-education.html#business-education-pricing).

---

### Post by dave01945 on 2011-08-23
this might be able to achieve what you are after

[http://tombuntu.com/index.php/2008/05/27/how-to-lock-down-gnome/](http://tombuntu.com/index.php/2008/05/27/how-to-lock-down-gnome/)

there are a few different post on goolgle but i think what your looking for is an ubuntu web kiosk

---

### Post by ojdon on 2011-08-23
[http://chromeos.hexxeh.net/vanilla.php]("http://chromeos.hexxeh.net/vanilla.php")

???

---

### Post by drawkcab on 2011-08-24
openbox with only chromium in the menu?

---

### Post by aeiah on 2011-08-24
> **drawkcab said:**
> openbox with only chromium in the menu?

openbox with no menu and a startup script that, in pseudo code:

```

while true;
if chromium-browser is not running:
    start chromium-browser (in kiosk mode)
sleep 5

```

then set a rule in openbox to always open chromium in fullscreen, set chromium to use system window decorations, and then set openbox to remove window borders from chromium.

or you could use a browser like uzbl, which is webkit based like chromium but can be locked down to get rid of the right-click menu and all sorts

---

### Post by ajmctaggart on 2011-08-24
Thanks for your awesome suggestions!

theplatapi
> Have you looked into Chromebooks for education? You can get them for $20 a month. Details here:[http://www.google.com/chromebook/bus...cation-pricing](http://www.google.com/chromebook/bus...cation-pricing).
30 netbooks @ $20 = $600 per month, $7200 per year - The netbooks were $198 per unit, so we own the equipment for much less.

dave01945
> this might be able to achieve what you are after

[http://tombuntu.com/index.php/2008/0...ck-down-gnome/](http://tombuntu.com/index.php/2008/0...ck-down-gnome/)

there are a few different post on goolgle but i think what your looking for is an ubuntu web kiosk
Agree! This may be a nice solution that I will have to spend some time on this morning.

ojdon
> [http://chromeos.hexxeh.net/vanilla.php](http://chromeos.hexxeh.net/vanilla.php)

???
Actually made a usb stick yesterday :)  It looks promising - but I've got issues connecting to Hidden SSIDs and I'm not sure how the whole "Login with you Google Acct." will work - not ruling it out, but I haven't spent enough time with it quite yet.

drawkcab
> openbox with only chromium in the menu?

aeiah
> openbox with no menu and a startup script that, in pseudo code:

Code:
while true;
if chromium-browser is not running:
    start chromium-browser (in kiosk mode)
sleep 5
then set a rule in openbox to always open chromium in fullscreen, set chromium to use system window decorations, and then set openbox to remove window borders from chromium.

or you could use a browser like uzbl, which is webkit based like chromium but can be locked down to get rid of the right-click menu and all sorts
__________________

This seems like a great idea! Openbox would also give some performance gains (I believe) since I don't have to run Compiz/Unity/etc...

Question:  Do I build this from a server install?  And do you still suggest Natty or do I go with Debian/another option?

You guys are awesome!  I was starting to get a little sad, but all these great options will keep me really busy today.

---

### Post by ajmctaggart on 2011-09-08
Just to let everyone know - I have successfully gotten my "ChromeBuntu," books up and going!

This is by no means an actual Chrome OS.  I started out trying Openbox - and while I had a great system up and running - it was frankly buggy and did not exhibit the results of "just works," that I needed for the field.  Also, I didn't like the idea that there was all this great hardware recognition found in standard Ubuntu (webcams, mics, battery acpi, etc) that I just wasn't getting (easily) out of building my own install - even if we would never use the features, I didn't like the idea that we COULDN'T without a ton of configuration with the minimal install & Openbox.

So, I ended up going with Ubuntu 10.04-3 LTS.  Here's the gist of how to get a "ChromeBuntu" install (at least the way I did it).

[LIST]
[*]Admin User with a "Student" user that had basic privileges
[*]Student user no password for login/auto-login/ no password when waking from sleep
[*]Removed all Panel buttons except a Chrome Shortcut, Time & Date, Wifi/Battery/Volume (one can still access all the standard Gnome menus by Alt+F1)
[*]Locked Panel and made it impossible to add new panels
[*]Killed off startup items such as File Sharing, Bluetooth, etc.
[*]Press Power button for Shutdown menu
[*]Created a desktop Environment choice that loads Chrome first and then gnome-desktop with a rule that says if Chrome is closed it reopens in 5 seconds. (Thanks aeiah)
[*]Changed the permissions on Google Chrome, so that at every reboot all History, Settings, are cleared "Since the beginning of time" by default, but yet not lost if Browser closes during session.
[*]Wrote a script so that anything downloaded to ~/Desktop or ~/Downloads is removed at shutdown.
[*]Used Compiz to create some very interesting Window Rules
[LIST]
[*]Don't allow Chrome Window to be moved
[*]Don't allow Chrome Window to be minimized
[*]Maximize Chrome Window at all times
[/LIST]
[/LIST]

And there you have it - this is by no means a ChromeBook as Google would sell - but it does give you hardware recognition, access to standard Gnome, with minimal distractions to kids.

1 mistake I did make was that I built one netbook first and used Clonezilla for the other 30, without putting in the 6 different SSIDs and WPA passwords - meaning that I'll now have to do this ~180 times...oops...

BTW, Google did call me back!  But, were unwilling to budge from their education pricing, therefore making it far too expensive for our usage.

If anyone is interested in any more detail, just PM me, hopefully it helps someone.

Thanks to all the suggestions and help you guys gave!  Couldn't have gotten to this point without you all.

---

