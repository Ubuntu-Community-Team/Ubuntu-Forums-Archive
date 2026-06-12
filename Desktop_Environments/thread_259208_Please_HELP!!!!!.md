---
title: "Please HELP!!!!!"
date: 2006-09-17
forum: Desktop Environments
---

### Post by serewen on 2006-09-17
Hey guys,Newbie that 1st time to tried the LINUX.I was facing a few difficulties recently regarding the UBUNTU 6.06TLS that was installed recently.


1)Internet Connections
2)Audio files were not playable(MP3)
3)EXE files were not installable.

1st,I have checked with my network settings,And I have ping the page.It works perfectly.

[IMG]http://img.photobucket.com/albums/v436/sakisuki/network.png[/IMG]

[IMG]http://img.photobucket.com/albums/v436/sakisuki/pingpage.png[/IMG]

But while I open up the firefox browser to surf the net/webpages,It loaded half page.

[IMG]http://img.photobucket.com/albums/v436/sakisuki/halfpage.png[/IMG]

2nd,I got a memory card(SD) with card reader,It could be detected perfectly But I want to test it out with the UBUNTU LINUX environment,It failed.I have tried with the built-in music player that came along with the OS.

[IMG]http://img.photobucket.com/albums/v436/sakisuki/pendrivedetection.png[/IMG]

[IMG]http://img.photobucket.com/albums/v436/sakisuki/audioerror.png[/IMG]


3rd,I want to try about the applications that will it capable with LINUX.

[IMG]http://img.photobucket.com/albums/v436/sakisuki/exeerror.png[/IMG]


Thanks for the reply to help me out,Or you can send the soolution to my email:serewen@gmail.com



Kindest Regards,
Serewen

---

### Post by pay on 2006-09-17
.exe files are not installable because they are binary files for windows. However you can install wine to add some windows compatiablity. 
Also to play mp3 files in totem you need to install the codecs.
Heres a useful guide for someone new to Ubuntu [http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)
Goodluck.

---

### Post by bigken on 2006-09-17
in the firefox browser you could try this type about:config the in the filter bar type ipv6 then double click to change it from flase to true ;)

hope this helps

---

### Post by sprinkles on 2006-09-17
EXE files are Windows executables, and will not run under linux.

---

### Post by Pumm4 on 2006-09-17
> **serewen said:**
> 
1)Internet Connections
2)Audio files were not playable(MP3)
3)EXE files were not installable.

1. Try this way:
System > Administration > Networking > Network Settings (will pop-up). Now select the type of connection you use and hit Propeties and set things up from there. Don't forget to add Dns servers and to check your cable if it is in eth0 (gateway device).

2. If you don't like to do everything manualy for adding stuff to work use Automatix: [http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38](http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38) (more info can be found on the forums and in the site itself)

[SIZE=2] 3. As said above If you really want to run [/SIZE][SIZE=-1][SIZE=2]executable programs use Wine ([ www.winehq.com]("http://www.winehq.com%29") )[/SIZE]
[/SIZE]

---

