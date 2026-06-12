---
title: "all browser didn't load web properly in my ubuntu 8.10"
date: 2009-04-20
forum: General Help
---

### Post by aljauzaa on 2009-04-20
sir,i want to ask something, that important to me or anyone who had same problem with me.

in my ubuntu 8.10, if i want to browse web with firefox or opera (i use FF ver 3.0.8 and opera 9.64) with flash_player installed, in a certain address like yahoo.com, the browser cannot load all the image, this is the picture of yahoo...

[[img]http://img258.imageshack.us/img258/5916/84305587.th.png[/img]](http://img258.imageshack.us/img258/5916/84305587.png)

and if i want to open my e-mail account, yahoo always says like this:

Ooops. Yahoo! Mail can't load

Loading Yahoo! Mail failed due to a client side error

You might try going into your firewall settings, and disabling "Ad blocking". If that doesn't work, please contact customer care.
Try clearing your browser cache
Try clearing your browser cookies
Taking too long? More info
If you received an ActiveX warning, please enable ActiveX
Check your email in Yahoo! Mail Classic
Switch back to Yahoo! Mail Classic 
by opting out of Yahoo! Mail 
Click here to try again

and if i open address like imagehacks.us, it didn't open.

FYI, my ubuntu is updated daily.

for your kind attention i want to say thnk u very much.

---

### Post by codeseer on 2009-04-20
Basically it seems like your profile is messed up.

Open a terminal by going to the top left of your screen and clicking on Applications->Accessories->Terminal.

In this terminal type the following:

```
firefox -profilemanager -no-remote
```

In the window that comes up, create a new profile, select it and launch it. Then try to access your websites again.

---

### Post by aljauzaa on 2009-04-22
firefox -profilemanager -no-remote

that command didn't work.firefox still slow loading yahoo.and if the browser complete the loading, the web show same as the picture that i attach to this forum before.in opera 9.64 is faster loading the web but shows same as firefox display...
my speedtest.net download speed is 0.13mbps...if i using XP in that connection and opening yahoo or mail yahoo with Firefox and opera, it's work like crazy...but why in my ubuntu 8.10 using Firefox and opera browser works bad???
FYI, my ubuntu updated every day...
thx before...

---

### Post by aljauzaa on 2009-04-22
this is the display in opera (if i want to login in yahoo mail)...

[[img]http://img524.imageshack.us/img524/41/mailyahoo1.th.png[/img]](http://img524.imageshack.us/img524/41/mailyahoo1.png)

any browser in ubuntu 8.10 can't open yahoo mail...

---

### Post by codeseer on 2009-04-22
If it requires ActiveX, then it isn't going to work in any native Linux browser. It would probably work under Wine though.

---

### Post by aljauzaa on 2009-04-23
but, in your ubuntu 8.10 happen like in my ubuntu?

and if i want to open facebook,opera shows this :

[[img]http://img127.imageshack.us/img127/9734/image2449.png[/img]](http://www.imagehosting.com/)

please help me guys...

---

### Post by aljauzaa on 2009-04-23
please help me guys...:(

---

### Post by codeseer on 2009-04-23
You're right. My Ubuntu browsing doesn't look anything like that. Not on Yahoo! or Facebook or anything else.

You don't experience weird graphics like that anywhere else on your system?

This is an off the wall guess, but does your ISP cache or optimize anything for you? Like an accelerator type thing.

---

### Post by aljauzaa on 2009-04-23
> **codeseer said:**
> You're right. My Ubuntu browsing doesn't look anything like that. Not on Yahoo! or Facebook or anything else.

You don't experience weird graphics like that anywhere else on your system?

This is an off the wall guess, but does your ISP cache or optimize anything for you? Like an accelerator type thing.

i don't now...FYI,my internet connection didn't straight to my ISP, but through internet gateway in my office. if my office network administration grant all the bandwith to my IP (approximately 2mbps), and i try to browse yahoo and facebook...the results is same...

but if i use XP in same PC as Ubuntu 8.10, yahoo and facebook load properly...

weird isn't it?

please help me...

---

### Post by aljauzaa on 2009-04-23
And i didn't found weird graphics like that anywhere else on my system.

what about the problem of login to yahoo mail...i cannot entering my yahoo mail...

---

### Post by codeseer on 2009-04-23
I haven't touched Yahoo!'s services in probably 8 or more years, but that error page says something about Yahoo! Classic; could you use that to access the email until you figure this out? Also, if you're a paid member of the Yahoo! email, they let you use POP3.

Edit:

Out of curiosity, how did the X configuration detect your color depth? If you type this:

```
gedit /etc/X11/xorg.conf
```

...you should have a section that looks like this:

```

Section "Screen"
	Identifier     "Default Screen"
	Device         "Configured Video Device"
	Monitor        "Configured Monitor"
	Option         "NoLogo" "True"
	**DefaultDepth	24**
	SubSection "Display"
		**Depth       24**
		Modes      "nvidia-auto-select"
	EndSubSection
EndSection

```

---

### Post by aljauzaa on 2009-04-25
this is my xorg.conf (sorry..a little bit late) :

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```


FYI,i test another linux distro in PC that have trouble mention in before, i test slackware12.2...but the problem still lying in slackware too...cannot open yahoo mail, yahoo page didn't show properly...(what happening...)

---

### Post by codeseer on 2009-04-25
What's the exact address you're going to?

Also, what is the output when you type this in a terminal:

```
lspci | grep VGA
```

---

