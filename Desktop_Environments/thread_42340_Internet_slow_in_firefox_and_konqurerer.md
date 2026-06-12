---
title: "Internet slow in firefox and konqurerer"
date: 2005-06-17
forum: Desktop Environments
---

### Post by JamesNorris on 2005-06-17
My internet connection is super slow in both firefox and konq, but apt-get is fine.

I was trying to dowlnoad the latest CVS of aMSN and I got 0.3kbs in both browsers. However, downloading with apt-get and shell scripts from a console is fine... 

From what I can tell my DNS lookups are taking forever, though, even in the console. 

ADSL pppoa, TiscaliUK with eagle-usb drivers

[COLOR=Red]Edit[/COLOR]
Problem sorted, looks like it's actually an ISP problem... APPARENTLY, they're upgrading the cable in my area to DDSL, or something, so my connection will be awful for up to 10 days  ](*,) 

I do still have the problem with ICS, so please read [[COLOR=Red]This Thread[/COLOR] ](http://ubuntuforums.org/showthread.php?t=41873)and provide me with all your answers please :p ty  :-P

---

### Post by exile on 2005-06-17
is your route ok?

I've found that sometimes if the default route gets muddled up things have to wait to time out before they down the correct path.

---

### Post by jrev on 2005-06-17
Hi all,
It comes apparently from a missing package in the 5.04 distribution :
the gnome-ppp
We don't know yet the name/number of the package and where to download it from...
[COLOR=Red]In fact this issue cannot connect at the right speed on a dial-up modem connection [/COLOR]
thanks for your attention
jrev

---

### Post by byen on 2005-06-17
I have the same problem..my downloads are superfast on my cable connection but firefox takes ages to load pages...gets stuck at "looking up website" for over 3 secs before opening a page. infact this would be the only main problem that went unsolved so far.....really pisses me off... imagine a 6mbps conn acting like 6kbps....well...someday...!

---

### Post by deadlands on 2005-06-17
[QUOTE=byen]I have the same problem..my downloads are superfast on my cable connection but firefox takes ages to load pages...gets stuck at "looking up website" for over 3 secs before opening a page. infact this would be the only main problem that went unsolved so far.....really pisses me off... imagine a 6mbps conn acting like 6kbps....well...someday...![/QUOTE]

Turn off IPv6 in Firefox

About:config
set "network.dns.disableIPv6" to **true**
restart firefox

---

### Post by shakin on 2005-06-17
[QUOTE=deadlands]Turn off IPv6 in Firefox

About:config
set "network.dns.disableIPv6" to **true**
restart firefox[/QUOTE]

That may work for a lot of people, but not for everybody and definitely not for anybody who had DNS performance problems from the console. My ISP's primary DNS server is slow in Linux, but not in Windows. This is something I've never been able to figure out, but by changing the order of the servers in /etc/resolv.conf or in the network config GUI I can fix the problem. I suggest trying the same thing.

---

### Post by byen on 2005-06-17
i already did that... and it did make some difference but... i just dont understand why..imagine waiting for 5-10 seconds for google.com  to show up on a 6mbps.... :-(

---

### Post by Malkosha on 2005-06-17
I've had this problem in a few distros. Try this and see if it helps.

Type: about :config
In address bar press [Enter]
Double click on and set the following.

browser.tabs.showSingleWindowModePrefs = true

browser.xul.error_pages.enabled = true

network.dns.disableIPv6 = true

network.http.max-connections 48

network.http.max-connections-per-server 24

network.http.max-persistent-connections-per-proxy 12

network.http.max-persistent-connections-per-server 6

network.http.pipelining = true

network.http.pipelining.maxrequests 32

Luck!!

---

### Post by JamesNorris on 2005-06-17
Thing is... all these "change this in about:config" answers won't help, cos I have the same problem in konquerer, too. And DNS lookups from the console. It's not my firefox settings :-\

---

### Post by byen on 2005-06-17
[QUOTE=JamesNorris]Thing is... all these "change this in about:config" answers won't help, cos I have the same problem in konquerer, too. And DNS lookups from the console. It's not my firefox settings :-\[/QUOTE]
 yes i agree with you James norris.. must be something else... sad that thi distro is so good in all areas but somehow fails on this one.
PS-  by the way malkosha...i have already tried what you have posted...thank you,

---

### Post by manicka on 2005-06-17
[QUOTE=JamesNorris]Thing is... all these "change this in about:config" answers won't help, cos I have the same problem in konquerer, too. And DNS lookups from the console. It's not my firefox settings :-\[/QUOTE]
Are you using dhcp? Try your settings manually. I get a faulty dns server setting when i use dhcp

---

### Post by byen on 2005-06-17
[QUOTE=manicka]Are you using dhcp? Try your settings manually. I get a faulty dns server setting when i use dhcp[/QUOTE]
 yes i am using DHCP.. but i do not know anything about it...i configured my wlan card and dhcp option poped in by default and i left it there....what can i do. do you want me to manually enter ipaddress, subnet and gateway? is there something i can do with the dns option?

sorry...when it comes to networking im a bum...! any help would be greatly appretiated.

---

### Post by deadlands on 2005-06-17
[QUOTE=byen]yes i am using DHCP.. but i do not know anything about it...i configured my wlan card and dhcp option poped in by default and i left it there....what can i do. do you want me to manually enter ipaddress, subnet and gateway? is there something i can do with the dns option?

sorry...when it comes to networking im a bum...! any help would be greatly appretiated.[/QUOTE]
 From what I've been reading there is a quirk in the Ubuntu kernel with IPv6

Here's a possible fix:

/etc/modprobe.d/aliases

says :

alias net-pf-10 **off**

NOT

alias net-pf-10 **ipv6**

Then a reboot.

---

### Post by byen on 2005-06-17
[QUOTE=deadlands]From what I've been reading there is a quirk in the Ubuntu kernel with IPv6

Here's a possible fix:

/etc/modprobe.d/aliases

says :

alias net-pf-10 **off**

NOT

alias net-pf-10 **ipv6**

Then a reboot.[/QUOTE]
 ok... it looks like there is a difference. the difference being... once i get into a certain site the related pages/links of the site loads really fast (i did a lotta about config changes too along with your tip). I do see a difference and i have to say..thank you.
But one thing i do not understand is it waits for a bit saying "looking for sitename" wonder why...gotta be a dns problem... but thank you deadlands.

---

### Post by manicka on 2005-06-18
[QUOTE=byen]ok... it looks like there is a difference. the difference being... once i get into a certain site the related pages/links of the site loads really fast (i did a lotta about config changes too along with your tip). I do see a difference and i have to say..thank you.
But one thing i do not understand is it waits for a bit saying "looking for sitename" wonder why...gotta be a dns problem... but thank you deadlands.[/QUOTE]
 To manually enter your provider's dns server address go to 
System--Administration--Networking

click on the DNS tab

You can then add the dns server address for your provider here. When I first clicked on this tab it had my routers gateway adresss as the dns server, which my router doesn't handle. I deleted this, then added my providers dns servers address. (This info is usually accesible through router/modems web interface). I then added in the search domain info and everything was back to normal.

HTH

---

### Post by JamesNorris on 2005-06-18
[QUOTE=deadlands]From what I've been reading there is a quirk in the Ubuntu kernel with IPv6

Here's a possible fix:

/etc/modprobe.d/aliases

says :

alias net-pf-10 **off**

NOT

alias net-pf-10 **ipv6**

Then a reboot.[/QUOTE]
 I love that... A "quirk" Now, I would call this a problem, lol.

I also use DHCP (so my g/f can connect to the internet from her Windows machine) but like Byen, I'm ignorant of DHCP settings... Could you point me in the right direction for a guide or something so I could do my settings manually? I will also try your /etc/modprobe.d/aliases change. I'll cross my fingers...

---

### Post by JamesNorris on 2005-06-19
Bump... Golly these forums are busy, it's only been 12 hours and this post dissapeared to the third page...

---

### Post by JamesNorris on 2005-06-19
Problem sorted, looks like it's actually an ISP problem... APPARENTLY, they're upgrading the cable in my area to DDSL, or something, so my connection will be awful for up to 10 days  ](*,) 

I do still have the problem with ICS, so please read [[COLOR=Red]This Thread[/COLOR] ](http://ubuntuforums.org/showthread.php?t=41873)and provide me with all your answers please :p ty  :-P

---

