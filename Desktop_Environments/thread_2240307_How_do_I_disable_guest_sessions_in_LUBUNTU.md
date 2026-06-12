---
title: "How do I disable guest sessions in LUBUNTU"
date: 2014-08-19
forum: Desktop Environments
---

### Post by Bernard_de_Terwang on 2014-08-19
Hi,

I've installed lubuntu 14.04 on an old PC for my kids. The PC is too old for Ubuntu.

The Guest Session feature is very nice in general but my concern is that I don't want my kids to login freely anytime so I'd like to de-activate this feature. I found information on how to do this with ubuntu with the allow-guest=false parameter but this does not seem to work in lxdm.conf.

So what's the right way to do this.

Note : I'm open even to change the distribution providing it is lightweight enough if it is the only way (xubuntu ?)

---

### Post by ibjsb4 on 2014-08-19
Is this what you did?  Should of worked.

[http://ubuntuforums.org/showthread.php?t=1968967&p=11889180&viewfull=1#post11889180](http://ubuntuforums.org/showthread.php?t=1968967&p=11889180&viewfull=1#post11889180)

Maybe this

[https://help.ubuntu.com/community/Lubuntu/Boot_Install_Login#Changing_LightDM_Settings](https://help.ubuntu.com/community/Lubuntu/Boot_Install_Login#Changing_LightDM_Settings)

More hits here

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=remove+guest+session+lubuntu&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=remove+guest+session+lubuntu&sa=Search&cof=FORID:9)

---

### Post by Bernard_de_Terwang on 2014-08-19
This all is what I hoped I could do. Unfortunatly it is for lightdm / Ubuntu and I am on lxdm / Lubuntu

---

### Post by ibjsb4 on 2014-08-19
Ok

Looks like the file to edit is /etc/lxdm/default.conf

[http://ubuntuforums.org/showthread.php?t=1982685&p=11951220#post11951220](http://ubuntuforums.org/showthread.php?t=1982685&p=11951220#post11951220)

---

