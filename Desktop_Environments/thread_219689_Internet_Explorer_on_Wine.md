---
title: "Internet Explorer on Wine"
date: 2006-07-20
forum: Desktop Environments
---

### Post by wizzkid on 2006-07-20
I Installed Wine, so I could run windows application like Dreamweaver, flash etc. however, internet explorer is required, so  downloaded the internet explorer 5.5 and 6, but I encounter an error when I run the ie6setup.exe, same with ie5setup.exe 

error message is: setup was unable to install all the components. Please close all applications and try running setup again. 

So I tried running setup again and i still got the same error.

I also tried to install wine-config-sidenet, the ie was installed successfully, however, other application like jre doesnt want to install. it says wrong version of windows.

I am using Wine 0.9.12.

Also, I installed firefox for windows and its running fine, however, i cannt see it on the wine configuration.


please help! 

Thanks.

---

### Post by FrdPrefct on 2006-07-20
Try running winecfg and setting a different version of Windows.  That may help.  You can set application specific versions of Windows later using this method too if necessary.

---

### Post by aysiu on 2006-07-20
IEs4Linux is your friend.

---

### Post by wizzkid on 2006-07-20
I already tried, 98 200 XP and it does the same thing, I still encounter error.

error message is: setup was unable to install all the components. Please close all applications and try running setup again. 

I install firefox for windows, flash player 9 and java and all has no problem. however, ie is just a pain. I need to install it so i could install the other programs.

Hope somebody could give me a solution :-)

TY

---

### Post by aysiu on 2006-07-20
> **wizzkid said:**
> 
Hope somebody could give me a solution :-) [http://www.tatanka.com.br/ies4linux/index-en.html](http://www.tatanka.com.br/ies4linux/index-en.html)

---

### Post by wizzkid on 2006-07-20
does wine detect the IEs4Linux? I need to install ie its just because other installation line dreamweaver asked me to install ie.

Please advice
TY

---

### Post by aysiu on 2006-07-20
> **wizzkid said:**
> does wine detect the IEs4Linux? I need to install ie its just because other installation line dreamweaver asked me to install ie.

Please advice
TY
It works the other way around. IEs4Linux detects and uses Wine. It's an installation script that uses Wine and Cabextract to install Internet Explorer.

---

### Post by wizzkid on 2006-07-21
I installed ies4linux, all went okay. but when I tried to install visio, it was asking to install the internet explorer first, meaning it didnt detect the ies4linux.. please help.

Also, the visio installation asked me to restart computer, how can I restart the wine? or do I have too? 

wizzkid@wizz-laptop:~$ ies4linux -help
bash: ies4linux: command not found
wizzkid@wizz-laptop:~$

Thanks.

---

### Post by mikeoh on 2006-07-21
ies4linux creates its own fake windows installation separate for your normal fake windows.  So no other program will detect it.  Usually the ies4linux installation is at:
    ~/.ies4linux
while your normal wine installation is at:
    ~/.wine
where ~ is your home directory.

To restart your wine use wineboot which simulates a windows reboot.

---

### Post by wizzkid on 2006-07-21
Can I also install other program like photoshop, dreamweaver, visio 2003 on ies4linux? :)

and how?

Please advice, Thanks.

---

### Post by myrek on 2006-07-21
Look in the application database for wine.

Dreamweaver:
[http://appdb.winehq.org/appview.php?iAppId=183](http://appdb.winehq.org/appview.php?iAppId=183)

Photoshop:
[http://appdb.winehq.org/appview.php?iAppId=17](http://appdb.winehq.org/appview.php?iAppId=17)

Visio:
[http://appdb.winehq.org/appview.php?iAppId=119](http://appdb.winehq.org/appview.php?iAppId=119)

---

