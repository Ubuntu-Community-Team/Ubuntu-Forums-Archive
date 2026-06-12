---
title: "Lucid Lynx 10.04 Live CD -- No Boot Menus?"
date: 2010-05-06
forum: Desktop Environments
---

### Post by Bob P on 2010-05-06
I just downloaded the Lucid Lynx 10.04 LTS Install CD for the desktop.  I am concerned that I have downloaded the wrong ISO or that the CD that I burned is not behaving properly.

Unlike all of the other Ubuntu "Live CDs", this one doesn't offer you a choice of what Ubuntu does at Boot-up.  There's no menu that asks what you'd like to do.  

This CD doesn't give you choices like:

- Test Drive Ubuntu without making any changes to your computer
- Install Ubuntu
- Test CD for Errors
- Test Memory
- Boot from Hard Disk

Instead, this CD just boots right to a Gnome desktop. Normally this wouldn't be a problem, but it turns out the the CD is performing some actions behind my back that I don't like.

All that I wanted to do was to check the CD for errors to make sure that it burned properly.  I didn't want it installing on the system where I was doing the burning.  Instead of giving me options at boot, the CD automatically loaded Gnome, and then proceeded to mount all of the drives on my system, and then attempted to establish connection to IP address 91.189.90.132.  I didn't like that.   Luckily my firewall is secure enough that it stopped this unauthorized outbound data traffic dead in its tracks.

I used reverse DNS to look up the owner if IP address 91.189.90.132.  Here's what I found:

```
http://whois.domaintools.com/91.189.90.132
[LEFT]         **IP Information for 91.189.90.132**

IP Location:                                           [IMG]http://whois.domaintools.com/images/flags/uk.gif[/IMG]                 United Kingdom                                Canonical Ltd                                                                                 Resolve Host:                                                       rookery.canonical.com                                                                             IP Address:                                           91.189.90.132                [                     [IMG]http://whois.domaintools.com/images/whois_button.gif[/IMG]                 ]("http://whois.domaintools.com/91.189.90.132")                 [                     [IMG]http://whois.domaintools.com/images/rip_button.gif[/IMG]                 ]("http://www.domaintools.com/reverse-ip/?hostname=91.189.90.132")                 [                     [IMG]http://whois.domaintools.com/images/ping_button.gif[/IMG]                 ]("http://dns-tools.domaintools.com/ip-tools/?method=ping&query=91.189.90.132")                 [                     [IMG]http://whois.domaintools.com/images/dns_button.gif[/IMG]                 ]("http://dns-tools.domaintools.com/ip-tools/?method=dns&query=91.189.90.132")                 [                     [IMG]http://whois.domaintools.com/images/traceroute_button.gif[/IMG]                 ]("http://dns-tools.domaintools.com/ip-tools/?method=traceroute&query=91.189.90.132")                                     
    [/LEFT]
      [LEFT]         
inetnum:        91.189.88.0 - 91.189.95.255
netname:        CANONICAL-CORE
descr:          Canonical Ltd
country:        GB
org:            ORG-CAN1-RIPE
admin-c:        CAN-RIPE
tech-c:         CAN-RIPE
status:         ASSIGNED PI
mnt-by:         RIPE-NCC-HM-PI-MNT
mnt-lower:      RIPE-NCC-HM-PI-MNT
mnt-by:         CANONICAL-MNT
mnt-routes:     CANONICAL-MNT
mnt-domains:    CANONICAL-MNT
remarks:        rev-srv:        ns1.canonical.com
remarks:        rev-srv:        ns2.canonical.com
remarks:        rev-srv:        ns3.canonical.com
source:         RIPE # Filtered
remarks:        rev-srv attribute deprecated by RIPE NCC on 02/09/2009

organisation:   ORG-CAN1-RIPE
org-name:       Canonical Ltd
org-type:       OTHER
address:        1 Circular Road
address:        Douglas
address:        Isle of Man
address:        IM1 1AF
address:        United Kingdom
e-mail:         [[IMG]http://source.domaintools.com/email.pgif?md5=8e0b8010ef3e8129f71b0f6c70aae271&face=arial&size=9&color=000000&bgcolor=FFFFFF&face=arial&size=9&color=0000FF&bgcolor=FFFFFF&format[]=underline&format[]=transparent&format[]=transparent[/IMG]]("http://www.domaintools.com/registrant-search/?email=8e0b8010ef3e8129f71b0f6c70aae271")
mnt-ref:        CANONICAL-MNT
mnt-by:         CANONICAL-MNT
source:         RIPE # Filtered

role:           Canonical Ltd Admin
address:        1 Circular Road
address:        Douglas
address:        Isle of Man
address:        IM1 1AF
e-mail:         [[IMG]http://source.domaintools.com/email.pgif?md5=030a154efc8f5bd1d5f347200f339e7b&face=arial&size=9&color=000000&bgcolor=FFFFFF&face=arial&size=9&color=0000FF&bgcolor=FFFFFF&format[]=underline&format[]=transparent&format[]=transparent[/IMG]]("http://www.domaintools.com/registrant-search/?email=030a154efc8f5bd1d5f347200f339e7b")
admin-c:        LJ974-RIPE
admin-c:        JT2256-RIPE
admin-c:        NM1806-RIPE
admin-c:        CJ1182-RIPE
admin-c:        SS8542-RIPE
tech-c:         LJ974-RIPE
tech-c:         JT2256-RIPE
tech-c:         NM1806-RIPE
tech-c:         CJ1182-RIPE
tech-c:         SS8542-RIPE
nic-hdl:        CAN-RIPE
mnt-by:         CANONICAL-MNT
source:         RIPE # Filtered

route:          91.189.88.0/21
descr:          Canonical Route Object
origin:         AS41231
mnt-by:         CANONICAL-MNT
source:         RIPE # Filtered


     [/LEFT]
                                     

```Is this a Live CD, where you have some options about what to do at boot-up, or is this only an install CD?  This information isn't clearly spelled out on the download page.

Needless to say, I don't like the idea of this LiveCD taking control of my computer, mounting my drives, and then establishing contact with Canonical Ltd., without even giving me a menu option before doing so.  I feel very lucky that my firewall was there to protect me.

thanks.

Addendum: I downloaded the ISO directly from the ubuntu.com website, not via a torrent.

---

### Post by CharlesA on 2010-05-06
Some info as to why there is no boot menu:

> **philinux said:**
> 
**[COLOR="DarkRed"]Boot options hidden by default on Desktop and Netbook LIVECDs[/COLOR]**
The Ubuntu 10.04 LTS Desktop and Netbook CDs feature a new boot interface that is non interactive by default. 
To configure advanced boot options, press any key at the first boot screen.

---

