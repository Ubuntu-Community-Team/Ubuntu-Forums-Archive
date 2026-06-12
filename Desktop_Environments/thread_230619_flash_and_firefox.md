---
title: "flash and firefox"
date: 2006-08-06
forum: Desktop Environments
---

### Post by bmonkey on 2006-08-06
Ive installed flash for firefox by downloading off adobes site.. but that doesnt work when i visit flash sites.. i have also used automatix to install it but it aint working either :( any tips/suggestions?

---

### Post by jordilin on 2006-08-06
You should follow the instructions pointed out here:
[http://www.adobe.com/shockwave/download/index.cgi?P1_Prod_Version=ShockwaveFlash&Lang=English](http://www.adobe.com/shockwave/download/index.cgi?P1_Prod_Version=ShockwaveFlash&Lang=English)
or take a quick read at this post:
[http://jordilin.wordpress.com/2006/06/03/installing-flash-player-in-dapper-drake/](http://jordilin.wordpress.com/2006/06/03/installing-flash-player-in-dapper-drake/)

---

### Post by bmonkey on 2006-08-06
Macromedia Flash Player 7 will be installed in the following directory:

Mozilla installation directory  = /home/dave/.mozilla

It doesnt want to give me a choice to change directories.. :/ any idea?

ty for the rapid response :D

--
edit
-- ignore that.. wasnt using sudo

now i am getting this error

Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla): /usr/lib/mozilla-firefox
./flashplayer-installer: line 158: strings: command not found
./flashplayer-installer: line 164: [: `)' expected, found 7
./flashplayer-installer: line 166: [: `)' expected, found 7
./flashplayer-installer: line 168: [: `)' expected, found 7

---

### Post by jordilin on 2006-08-06
> **bmonkey said:**
> Macromedia Flash Player 7 will be installed in the following directory:

Mozilla installation directory  = /home/dave/.mozilla

It doesnt want to give me a choice to change directories.. :/ any idea?

ty for the rapid response :D

/home/dave/.mozilla is OK, not necessary to change it. 

> --
edit
-- ignore that.. wasnt using sudo

now i am getting this error

Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla): /usr/lib/mozilla-firefox
./flashplayer-installer: line 158: strings: command not found
./flashplayer-installer: line 164: [: `)' expected, found 7
./flashplayer-installer: line 166: [: `)' expected, found 7
./flashplayer-installer: line 168: [: `)' expected, found 7
As you said it, you must use sudo.

---

### Post by bmonkey on 2006-08-06
Tried with sudo when i got the errors

/flashplayer-installer: line 158: strings: command not found
./flashplayer-installer: line 164: [: `)' expected, found 7
./flashplayer-installer: line 166: [: `)' expected, found 7
./flashplayer-installer: line 168: [: `)' expected, found 7

Any ideas?

---

### Post by swj on 2006-08-06
Manually install flash


Download: [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_7_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_7_linux.tar.gz)

create a plugins directory:
/home/dave/.mozilla/plugins/

Finally copy flashplayer.xpt and libflashplayer.so to /home/dave/.mozilla/plugins/

Now you have flash installed for Dapper without all the fuss.

---

### Post by bmonkey on 2006-08-06
mmmm so it appears flash was installed all along.. but oddly i cannot access [www.enemyterritory.com](www.enemyterritory.com) - it keeps saying "This site requires Flash 8" 

Is that a completely diff plugin?

---

### Post by swj on 2006-08-06
thats because it does and linux only has 7,0,63,0

I hope that a new release for linux is soon! :confused:

---

### Post by bmonkey on 2006-08-06
*tears out hair* here i am messing around with installing stuff that doesnt need to be isntalled.. lolol :( i am a bum - oh well guess ill just have to wait.. damn inconvenience but what can you do :)

Thanks everybody for your help. 
Sorry about waisting your time

---

