---
title: "adobe flash player 9, dapper drake 6.06, opera 9.64"
date: 2009-03-19
forum: General Help
---

### Post by Claus7 on 2009-03-19
Hello,

I was trying to upgrade adobe flash player version 9 to version 10. In my surprise I found out that this cannot happen. The version of mozilla that opera shares with a lot of plugins is 1.5 in dapper, whereas flash player 10 supports mozilla 2 and higher. 

So deleting all the flash files in the directories :
/usr/lib/opera/plugins
/usr/lib/mozilla/plugins
/home/*user*/.opera
/home/*user*/.mozilla
/home/*user*/.opera/plugins
/home/*user*/.mozilla/plugins

I was left with empty web pages if they had flash animations. In order to put things back I downloaded flash 9 from here:
[http://kb.adobe.com/selfservice/viewContent.do?externalId=kb406791](http://kb.adobe.com/selfservice/viewContent.do?externalId=kb406791)

and in order to play in mozilla I installed it with:
./flashplayer-installer
in
/home/*user*/.mozilla

for flash 9 to work in opera I had to install it via cp command in /usr/lib/opera/plugins as they did here:
[http://all-about-ubuntu.blogspot.com/2008/02/install-flash-player-on-opera.html](http://all-about-ubuntu.blogspot.com/2008/02/install-flash-player-on-opera.html)

The command :
sudo ./flashplayer-installer 

choosing destination 
/usr/lib/opera/plugins 

even though it didn't produce any errors, it didn't suffice for a sound installation. 

Regards!

---

