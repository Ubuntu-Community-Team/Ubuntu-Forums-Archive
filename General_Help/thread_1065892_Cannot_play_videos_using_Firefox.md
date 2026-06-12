---
title: "Cannot play videos using Firefox"
date: 2009-02-10
forum: General Help
---

### Post by arepaking on 2009-02-10
Hello All,
I cannot play neither videos nor animations using Firefox. I read some post about installing some plugins (such as flashplugin-nonfree,etc..) and I followed those instructions without being able to get this thing work.

I also tried to manually install the adobe flash 10 player ([http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)) , but, when I double click the debian file I get this error: [COLOR="Red"]ERROR WRONG ARCHITECTURE i386.
[/COLOR]

I am using Ubuntu 8.10 64bits.

Does anyone knows how to overcome this issue? Thank you very much in advance,

-AK

---

### Post by arepaking on 2009-02-10
> **arepaking said:**
> Hello All,
I cannot play neither videos nor animations using Firefox. I read some post about installing some plugins (such as flashplugin-nonfree,etc..) and I followed those instructions without being able to get this thing work.

I also tried to manually install the adobe flash 10 player ([http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)) , but, when I double click the debian file I get this error: [COLOR="Red"]ERROR WRONG ARCHITECTURE i386.
[/COLOR]

I am using Ubuntu 8.10 64bits.

Does anyone knows how to overcome this issue? Thank you very much in advance,

-AK


This issues has been resolved with the help of the guys of system76. All I had to do was run the following command:

sudo apt-get install libdvdcss2 w64codecs


Regards,
AK

---

