---
title: "KWifi"
date: 2005-06-02
forum: Desktop Environments
---

### Post by Jamesia on 2005-06-02
I don't think KWiFiManager is very functional. Does anyone know if there is a GUI for Kubuntu that will allow me to switch easily from one network to a different one. It'd be cool if it would store itself like an applet in the taskbar, but I'll take whatever I get. I take my laptop an awful lot of places... and my "wireless network ssid and wep key" file is getting really big (where I store all of my wep keys), and it's kind of unproductive for me to manually change them via command line.

By the way, I had been using this one:
[http://sourceforge.net/projects/gtkwifi/](http://sourceforge.net/projects/gtkwifi/) 
while I was using GNOME, and it's really quite good. If you need one, then try that one! :)

---

### Post by NTolerance on 2005-06-02
[QUOTE=Jamesia]I don't think KWiFiManager is very functional. Does anyone know if there is a GUI for Kubuntu that will allow me to switch easily from one network to a different one. It'd be cool if it would store itself like an applet in the taskbar, but I'll take whatever I get. I take my laptop an awful lot of places... and my "wireless network ssid and wep key" file is getting really big (where I store all of my wep keys), and it's kind of unproductive for me to manually change them via command line.

By the way, I had been using this one:
[http://sourceforge.net/projects/gtkwifi/](http://sourceforge.net/projects/gtkwifi/) 
while I was using GNOME, and it's really quite good. If you need one, then try that one! :)[/QUOTE]

I can't get gtkwifi to work right.  All it succeeds in doing is disconnecting me from my AP.  It won't let me add any access points.  It will only let me remove them, but of course there are none in my list because the damn orinoco drivers don't support scanning.  How do I manually add APs to the program?

---

### Post by Jamesia on 2005-06-02
Sorry - I don't know the answer to that.. maybe someone else will chime in? :)

---

### Post by philipacamaniac on 2005-06-02
You could try [http://wlassistant.sourceforge.net/](http://wlassistant.sourceforge.net/)

But, I've resorted to just putting the info in an init script:

```

## wireless-tools Configuration Script
##
## I wrote this script because I couldn't find where
## wireless-tools (iwconfig, etc.) stores its information.
## And, since the information wasn't being remembered after
## a reboot, this script was designed to fix that.
##
## - Philip Cain (philipacamaniac@gmail.com)

## Wireless Interface (the card you want to use)
IFACE="wlan0"

## Wireless Network SSID
ESSID="put your ssid here"

## Wireless Encryption (WEP) Key
## 128bit key format: xxxx-xxxx-xxxx-xxxx
## 64bit key format: xxxxxxxxxx
KEY="put your key here"

## Default Gateway (if you have set a static IP)
GW="192.168.1.1"

echo "Connecting to wireless network..."

iwconfig $IFACE essid $ESSID key $KEY
## Uncomment this line to set the gateway
#route add default gw $GW $IFACE

```

Ultra-evil, but I have wireless networking every time now. I'm happy.

EDIT: Make the script executable and have it start with the system (I put mine in /etc/init.d and made the various adjustments to each runlevel).

EDIT EDIT: I just noticed that you already know how to change via the command line. Oh well, I tried.  \\:D/

---

### Post by dejitarob on 2005-06-02
Have you tried [kde-apps.org](http://kde-apps.org/)? I switch back and forth from a my home using WPA-PSK and school/work using a VPN. I have found the quickest thing to do is making two simple shell scripts and simply execute the one I want to switch to. If you are interested here is my home script: 
```
#!/bin/sh
sudo wpa_supplicant -B -i eth1 -c /etc/wpa_supplicant.conf -D ipw -w -dd #executes wpa daemon
sudo iwconfig eth1 essid xxxx
sudo iwconfig eth1 mode auto
sudo ifdown eth1
sudo ifup eth1
``` and my school/work:
```

#!/bin/sh
sudo killall wpa_supplicant
sudo /etc/init.d/vpnclient_init stop #silly cisco vpn client wants to be started before networking service
sudo /etc/init.d/networking stop
sudo /etc/init.d/vpnclient_init start
sudo /etc/init.d/networking start
sudo iwconfig eth1 essid ufw
sudo iwconfig eth1 mode auto
sudo ifdown eth1
sudo ifup eth1
sudo vpnclient connect ufl-vpn

```

---

### Post by Jamesia on 2005-06-02
[http://wlassistant.sourceforge.net](http://wlassistant.sourceforge.net)

This seems to be working for me. I'll have to take my laptop to school and work tomorrow and see how portable it is. Thank you all for help. 

I think now I will look into shell scripting a little bit more.

---

### Post by SanderAnt on 2005-06-02
Yeah IMHO KDE beats the pants of, ehm the other desktop environment, accept for a couple of areas and wifi management is one of them.
The best solution I've seen is Network Manager [http://people.redhat.com/dcbw/NetworkManager/](http://people.redhat.com/dcbw/NetworkManager/)
but for some reason it isn't available for ubuntu.
wlassistant looks great, but the deb doesn't install. Does anyone know of a package for kubuntu?

---

### Post by Jamesia on 2005-06-02
The deb I downloaded from sourceforge installed fine, but I had to update two things first: 

[http://www.jnewto.com/stuff/libidn11_0.5.13-1.0_i386.deb](http://www.jnewto.com/stuff/libidn11_0.5.13-1.0_i386.deb)
[http://www.jnewto.com/stuff/wireless-tools_27-2_i386.deb](http://www.jnewto.com/stuff/wireless-tools_27-2_i386.deb)

And, then you can install the wireless assistant:

[http://www.jnewto.com/stuff/wlassistant_0.3.9-1_i386.deb](http://www.jnewto.com/stuff/wlassistant_0.3.9-1_i386.deb)

But I wouldn't have been able to know about update the previous two packages if I hadn't installed --

[http://www.kde-apps.org/content/show.php?content=23981&PHPSESSID=65b278207d2222536566073398fc5367](http://www.kde-apps.org/content/show.php?content=23981&PHPSESSID=65b278207d2222536566073398fc5367)

Hope some of that helps...

---

### Post by Seth on 2005-06-02
I use wifi-radar and it seems to work quite nicely.

[http://www.bitbuilder.com/wifi_radar/](http://www.bitbuilder.com/wifi_radar/)

---

### Post by dejitarob on 2005-06-02
> Does anyone know of a package for kubuntu?
You can compile from [source](http://prdownloads.sourceforge.net/wlassistant/wlassistant-0.3.9.tar.bz2?download). From the readme/INSTALL: 
```
tar xfvj wlassistant-0.3.9.tar.bz2
cd wlassistant-0.3.9
make -f Makefile.cvs #you may need automake1.6 (sudo aptitude install automake1.6)
./configure --prefix=/usr
make
sudo make install

``` To run, goto the KDE menu, Utilities, Wireless Assistant. If it gives you an error about permissions, select yes to setuid, type in your password then close and re-open it.

---

### Post by Krash1201 on 2005-06-03
dejitarob,

when i tried to do the make, i got up to ./configure --prefix=/usr and got this

```
checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!

```

then everything stops and make fails.  what "X" am i missing?

thanks

---

### Post by philipacamaniac on 2005-06-03
[QUOTE=Krash1201]then everything stops and make fails.  what "X" am i missing?
[/QUOTE]

I think you need x-window-system-dev...

---

### Post by Krash1201 on 2005-06-05
ok, got x-window-dev, and did the same thing with Qt, now there is another problem.  during ./configure --prefix=/usr the last line before the process stops, i get this

```
checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix!

```

any ideas?

---

### Post by SanderAnt on 2005-06-06
From my humble experience. You generally need a lot of headers and such to compile almost any KDE application.
I would go into Kpackage or Synaptic and filter for dev and select as a bunch of the KDE dev packages, and keep trying, or grab the .deb file and download the other debs Jamesia mentioned.

---

### Post by Krash1201 on 2005-06-06
ends up i was missing kde-devel.  got that taken care of, now its telling me that i have insufficient premissions.   ](*,)

---

### Post by Krash1201 on 2005-06-06
got past the install problem, started the program and got a permissions problem.  went ahead and scanned anyway, now its telling me that its missing executables.  then i run detect to get the paths right, but when i do they don't change, i still get the same error message...any ideas?  thanks in advance

---

### Post by sammyguy193 on 2005-07-19
[QUOTE=Krash1201]got past the install problem, started the program and got a permissions problem.  went ahead and scanned anyway, now its telling me that its missing executables.  then i run detect to get the paths right, but when i do they don't change, i still get the same error message...any ideas?  thanks in advance[/QUOTE]

***There is no need to compile this app from source, and franlky, i couldnt get it to work for the life of me when i tried to install it from source. 

* This application's dependecies CANNOT be met on ubuntu based systems unless you want to piss off APT/synaptic/whatever due to naming discrepancies :mad: , so you need to remove the dependencies from the .deb file itself. The dependencies will be met as long as you install kdelibs4-dev (synaptic is easiest). If you want the .deb file i hacked, i think i attached the file to this post, but i'm not sure, so tell me if it doesnt work.... the older version of this app (0.3.9) works fantastically with my ipw2200, and allows me to roam freely and connect to open networks with ease.... if you're bent on having the latest and greated 0.5.0 version which is supposed to be more up-to-date, and completely rewritten under the hood, well....???????????????


Cheers,
Sam


*PS: this is my first post!!! YAY!  \\:D/

---

### Post by skyboy on 2005-07-19
you need to install kdelibs4-dev

---

### Post by sammyguy193 on 2005-07-19
[QUOTE=skyboy]you need to install kdelibs4-dev[/QUOTE]
 I have it. you need to have it b/c it depends on libdnll-dev or something like that.. but i apt-got it, and hacked the ..deb file. then it installed w/o errors, and synaptic and apt were happy.... and there was much rejoicing...

---

### Post by elsewhere on 2005-07-19
FWIW, I let wpa_supplicant handle my different settings.  Might not be as slick as a system tray app, but it works in the background and I don't have to think about it.

You can have multiple AP's setup in your wpa_supplicant.conf file, like:

network = {
[INDENT]ssid = "work"
scan_ssid=0
psk="my work wpa password"
key_mgmt=WPA-PSK
[/INDENT]}

network = {
[INDENT]ssid="home"
scan_ssid=1
psk="my home wpa password"
key_mgmt=WPA-PSK
[/INDENT]}

network = {
[INDENT]ssid="lab"
scan_ssid=1
key_mgmt=NONE      # for WEP-only encryption
wep_key0=xxxxx
wep_key1=xxxxx
wep_key2=xxxxx
wep_key3=xxxxx
wep_tx_keyidx=0
[/INDENT]}

wpa_supplicant fires up when I boot my laptop, and continually scans in the background.  Whether I'm at work or home it connects, all I need to do is a *sudo ifup wlan0* and I'm set (I don't enable wlan0 automatically at boot, but I'd have that option).  Best of all, wpa_supplicant takes care of configuring the wireless settings to I don't have to use the command line tools or mess around with my *interfaces* file, other than to enable wlan0.

Anyways, it's not KDE-specific but works for me, so thought I'd mention it as an option...

Cheers,
KV

---

### Post by sammyguy193 on 2005-07-20
[QUOTE=elsewhere]FWIW, I let wpa_supplicant handle my different settings.  Might not be as slick as a system tray app, but it works in the background and I don't have to think about it.

You can have multiple AP's setup in your wpa_supplicant.conf file, like:


Cheers,
KV[/QUOTE]


I think i'm gonna give wpasupplicant a second try... did not know you can have multiple ap's and  it will scan and connect automatically in the background.... sound perfect for what i need. but as for roaming and starbucks  :-P hotspots, wlassistant is by far the way to go... 

by the way, does anyone know how to make a deb package from a source .tar.gz file? if so, tell me, and i'll make a ubuntu-specific deb package for the updated wlassistant 0.5.0.... 

sam

---

### Post by elsewhere on 2005-07-20
[QUOTE=sammyguy193]
by the way, does anyone know how to make a deb package from a source .tar.gz file? if so, tell me, and i'll make a ubuntu-specific deb package for the updated wlassistant 0.5.0.... 

sam[/QUOTE]

Easiest way I find is checkinstall, you can download it from the repos, you just execute checkinstall instead of make install when compiling / installing.

ie.

./configure
make
sudo checkinstall

A .deb will automatically be created and installed, you'll have the option of configuring the .deb settings (ie. version, maintainer info etc.).

Cheers,
KV

---

### Post by Flashrider on 2005-08-04
My problem is that I can not compile the source. I have the wireless-tools and libidn pakage and the gcc installed. There are no errors but the programm don't start. The 0.39 Version in the deb pakage work fine. Can please somebody help me to solve this problem or can please somebody build me a working deb from the current version.
Much thanks.

Flashrider

---

### Post by sammyguy193 on 2005-08-09
are you still looking for a .deb package? sorry.. havent been following the post... :roll:

---

### Post by Flashrider on 2005-08-10
Sure, I am. You have one for me???

---

### Post by marleyfan68 on 2005-08-20
I have a .deb package: wlassistant-0.5.3_0.5.3-1_i386.deb (just created it tonight!)... seems to be working fine so far...  let me know if it doesn't work for you...

marleyfan68

---

### Post by daller on 2005-09-03
running the "configure" part, the C compiler fails:

./configure --prefix=/usr

checking for C compiler default output file name... configure: error: C compiler cannot create executables

What may be wrong?

config.log:

gcc version 4.0.2 20050808 (prerelease) (Debian 4.0.1-4ubuntu6)
configure:2588: $? = 0
configure:2590: gcc -V </dev/null >&5
gcc: '-V' option must have argument
configure:2593: $? = 1
configure:2616: checking for C compiler default output file name
configure:2619: gcc     conftest.c  >&5
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status
configure:2622: $? = 1
configure: failed program was:
| /* confdefs.h.  */

---

### Post by daller on 2005-09-03
[QUOTE=marleyfan68]I have a .deb package: wlassistant-0.5.3_0.5.3-1_i386.deb (just created it tonight!)... seems to be working fine so far...  let me know if it doesn't work for you...

marleyfan68[/QUOTE]

Installation of your file went file, but how do I execute wlassistant?

---

### Post by coxx on 2005-09-08
You can just execute it by lauching the following command : 

/usr/local/kde/bin/wlassistant

---

### Post by daller on 2005-09-16
[QUOTE=coxx]You can just execute it by lauching the following command : 

/usr/local/kde/bin/wlassistant[/QUOTE]

Well, I had to force some dependencies, to get wlassistant installed - It seems to have broken the package... It gets removed upon a dist-upgrade...

---

### Post by Manny C on 2005-09-27
I had a couple of dep errors whilst trying to compile it. In particular one needs to install the libiw-dev package.

Follow the instructions given on the first page.

---

### Post by paxmark on 2005-10-02
I have to  configure Kwifi everytime via setting - configuration eiditor when I start so that it recognizes the card and router and then have to sudo in and do dhclient wlan0 every time.  

I saw the script above.  Does it work?  Or should I be setting something up in dhclient.conf?

---

### Post by hlfrk414 on 2005-10-12
Edit - nevermind, I didn't notice the reference to one of the devs. Only problem now is that installed but doewsn't do anything
Edit #2 - huzzah! run it as root. Now seems to run fine

---

### Post by Frank Siebert on 2006-09-05
> **Seth said:**
> I use wifi-radar and it seems to work quite nicely.

[http://www.bitbuilder.com/wifi_radar/](http://www.bitbuilder.com/wifi_radar/)

:D This was a very good hint. And now I am a registered forum member because I felt it really neccesary to thank you for that information.

---

