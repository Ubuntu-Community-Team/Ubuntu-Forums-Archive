---
title: "[newb] Desktop doesn't load after login"
date: 2005-03-15
forum: Desktop Environments
---

### Post by sander marechal on 2005-03-15
Hello all,

I am *very* new to Linux and I have a problem I can't solve. When I boot my PC everything works great untill the login screen. I enter my username and password, the login screen is replaced by a brown background am my mouse cursor shows. After that, nothing.... There's supposed to popup a box that starts loading all kinds of window managers and what-not but it simply doesn't show. All I get is an empty brown background an my cursor.

My Ubuntu installation is still really fresh. The only things I did are:
- Install my Alcatel SpeedTouch USB modem
- Remove two modprobe warnings ( [http://www.ubuntuguide.org/#modprobefatalerror](http://www.ubuntuguide.org/#modprobefatalerror) )
- Remove networking loading ( [http://www.ubuntuguide.org/#configuringnetworkinterfacestooslow](http://www.ubuntuguide.org/#configuringnetworkinterfacestooslow) )
- Remove NTP update ( [http://www.ubuntuguide.org/#synchronizingclocktooslow](http://www.ubuntuguide.org/#synchronizingclocktooslow) )

The rest is exactly like it was installed from the CD. I am still very new to all this so please explain clearly if I need to do something, look up something, etcetera. Oh yes, my PC:

PIII 600 Mhz
128 Mb RAM
30 Gb HDD (master) -> Win98 SE
80 Gb HDD (slave) -> Ubuntu

Thanks in advance for any help you can give!

--
Sander

---

### Post by iomicifikko on 2005-03-15
[QUOTE=sander marechal]Hello all,

I am *very* new to Linux and I have a problem I can't solve. When I boot my PC everything works great untill the login screen. I enter my username and password, the login screen is replaced by a brown background am my mouse cursor shows. After that, nothing.... There's supposed to popup a box that starts loading all kinds of window managers and what-not but it simply doesn't show. All I get is an empty brown background an my cursor.

My Ubuntu installation is still really fresh. The only things I did are:
- Install my Alcatel SpeedTouch USB modem
- Remove two modprobe warnings ( [http://www.ubuntuguide.org/#modprobefatalerror](http://www.ubuntuguide.org/#modprobefatalerror) )
- Remove networking loading ( [http://www.ubuntuguide.org/#configuringnetworkinterfacestooslow](http://www.ubuntuguide.org/#configuringnetworkinterfacestooslow) )
- Remove NTP update ( [http://www.ubuntuguide.org/#synchronizingclocktooslow](http://www.ubuntuguide.org/#synchronizingclocktooslow) )

The rest is exactly like it was installed from the CD. I am still very new to all this so please explain clearly if I need to do something, look up something, etcetera. Oh yes, my PC:

PIII 600 Mhz
128 Mb RAM
30 Gb HDD (master) -> Win98 SE
80 Gb HDD (slave) -> Ubuntu

Thanks in advance for any help you can give!

--
Sander[/QUOTE]
 --> IM A NEWBIE <---

hi, i really dunno what the problem could be but if i was in u i'd try to restore old settings and look what happens. in my newbie opinion those changes should not be related with that problem but i'd try anyway.  to do that just reboot pc and during grub loading press esc, select the rescue mode (the system will load in console mode) then type this if u have followed exactly the guide

sudo cp /etc/hotplug/blacklist_backup /etc/hotplug/blacklist 

sudo chmod +x /etc/init.d/networking  (only if u had permanently disabled network service)

sudo chmod +x /etc/init.d/ntpdate     (only if u had permanently disabled syncr clock service)

sudo reboot

and if u have again the problem, u have done somehting else, maybe installed something strange (in that case u can try uninstalling it via console mode -- give a look typing in console "man apt-get" for options about installing things (apt-get is the actual textbased program of which synaptic is a frontend))

i hope this can help u, sorry for my english, byez

---

### Post by sander marechal on 2005-03-15
[QUOTE=iomicifikko]
sudo chmod +x /etc/init.d/networking  (only if u had permanently disabled network service)

sudo reboot
[/QUOTE]

Just enabling networking fixed it. Thank you!

/me tips hat

---

### Post by iomicifikko on 2005-03-15
[QUOTE=sander marechal]Just enabling networking fixed it. Thank you!

/me tips hat[/QUOTE]
 wow happy to be usefull but really strange!
now u should understand why that happens;)

the only thing that i can think about is that the graphical environment is called  X "server" (so maybe something related with networking,... or not? ioi bah) but in that case u should not be able to see graphic at all.  really strange.  maybe someone could explain it.

byezz!

---

### Post by fdoving on 2005-03-15
[QUOTE=sander marechal]Just enabling networking fixed it. Thank you!

/me tips hat[/QUOTE]
 The reason was that lo, the 127.0.0.1 dummy network interface, was disabled. Some programs depend on it.

---

### Post by iomicifikko on 2005-03-15
[QUOTE=fdoving]The reason was that lo, the 127.0.0.1 dummy network interface, was disabled. Some programs depend on it.[/QUOTE]
 ahh yes u are right, i didnt think about it!;)

learning learning....

byez

---

### Post by sander marechal on 2005-03-16
Yes, that's probabely it. Thank you!

---

