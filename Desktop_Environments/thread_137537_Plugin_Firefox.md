---
title: "Plugin Firefox"
date: 2006-02-28
forum: Desktop Environments
---

### Post by Olderone on 2006-02-28
Every time I visit certain sites I am informed that a plugin is required which firefox  duly identifies as Macromedia flash player. I agree to the conditions for installation and then nothing happens. Any Ideas anyone? As a recent convert to Linux I am impressed. The other Query I have is with Mail Handler. In windows the address "poptiscali.co.uk" ,but Evolution says it does not exist. My Pc is also controlling a router as well as being connected ( part of a plan to link my two machines in the future.
This is my first post and I am unfamiliar with forum etiquette, and not very familiar with net worked systems

---

### Post by kaamos on 2006-02-28
Hello!

For installing flash you can check [https://wiki.ubuntu.com/RestrictedFormats#head-f375cba46014e861cd5ec7643bd7c4ef05acff2b](https://wiki.ubuntu.com/RestrictedFormats#head-f375cba46014e861cd5ec7643bd7c4ef05acff2b)

---

### Post by ccoppenbarger on 2006-04-13
The wiki did not help me very much. Here's what I did. I went to macromeda.com and clicked on the Get Flash button at the bottom.
If you click on the link to download, the link is wrong, but you can click on it anyway.
You'll get an error 404 message, but that's ok. Delete the "fp" at the beginning of the address in the address bar and press enter. The download dialog should now pop up.  Save it to the desktop.  Unarchive the file to the desktop. Open up a terminal window. Browse to the folder on the desktop. Should start with install.
Write the following:
> sudo ./flashplayer-installer
You'll have to write the location of the browser as well as close down your browser, but it works. It's easier than following the wiki as I kept having trouble grabbing the file. Besides, it's the latest version for Linux from Adobe. I hope this helps.

---

### Post by apjone on 2006-04-13
goto macromedia's website and get the install file fro linux and follow there instructions

---

### Post by cls1chuck on 2006-04-30
I'm on Firefox 1.0.8; I have followed all of the above, as well as Mozilla's instructions for installing it (copying the .so to the/mozilla-firefox/components directory).  Still no luck; I *STILL* get errors that say my browser doesn't have Macromedia FlashPlayer plugin installed.

sample url: [www.lego.com/eng/racers/fungames/supersonic/supersonic.asp](www.lego.com/eng/racers/fungames/supersonic/supersonic.asp)

about:plugins shows

Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 7.0 r63
===
MIME Type 	                            Description 	Suffixes   Enabled
application/x-shockwave-flash 	Shockwave Flash    swf 	        Yes
application/futuresplash 	FutureSplash Player 	spl  	    Yes
===
Thanks in advance for any help!

---

