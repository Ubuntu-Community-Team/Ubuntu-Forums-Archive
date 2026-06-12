---
title: "how to - steps for offline updates"
date: 2008-12-27
forum: General Help
---

### Post by nick192 on 2008-12-27
**if some1 has already posted this then i'm extremely sorry. n sorry for bad english.

i'm a newbie ubuntu/linux user. i was having trouble with offline application installations & updates. i worked a bit n i got satisfactory solution for that. tested on ubuntu 8.10. use '**applications->accessories->terminal**' for typing commands(i know this is too basic ;p).

1. we need to know that where ubuntu stores downloaded files that r either for apps or for updates & where r d details:

**/var/cache/apt/archives**		....(packages)
**/var/lib/apt/lists**		....(list)


2. now go to ur friends pc having internet connection & make these folders:

**sudo mkdir -p /xyz/var/cache/apt/archives**

**sudo mkdir -p /xyz/var/lib/apt/lists**


3. now update ur friends pc on ubuntu(same version). u can install packages also (juz remember package names or write them down!)


4. after completing it, copy those folder contents to ur newly created folders like:

**sudo cp /var/cache/apt/archives/*.deb /xyz/var/cache/apt/archives/**

**sudo cp /var/lib/apt/lists/* /xyz/var/lib/apt/lists/**
(juz avoid this error: **cp: omitting directory `/var/lib/apt/lists/partial'**)

**sudo rm /xyz/var/lib/apt/lists/lock**
(we dont need this file)


5. now copy complete /xyz folder to ur flash-drive like:

**sudo cp -R /xyz/ /media/*xxxx*/xyz/**
(here xxxx is ur flash-drive's mount name. check with urs)

6. go home on ur desktop n copy all stuff from ur flash-drive to ur pc:
[B]sudo cp -f /media/*xxxx*/xyz/var/cache/apt/archives/* /var/cache/apt/archives/

sudo cp -f /media/*xxxx*/xyz/var/lib/apt/lists/* /var/lib/apt/lists/[/B]

7. now open '**applications->add-remove**' n click on softwares u've downloaded on ur friend's pc. n click install.


8. for updates, juz open '**system->administration->update manager**', click 'select all'. u'll c the size 0 k. juz click on install updates.
thats it.. u r done !!!

if u n ur friend has installed ubuntu from same source then this process wont give any error.. hopefully :) if somethings wrong.. plz let me know.
:guitar:

---

### Post by EXCiD3 on 2009-01-01
Check out [**Keryx**]("http://keryx.betaserver.org") for downloading updates for an offline machine as well.

---

### Post by sriram kannan on 2011-05-24
you both guys rock!!! :guitar:

you have finally solved a problem which i had for days! :)

now, my friend will agree that ubuntu is awesome (all problem caused because he does not have internet)

:popcorn:

---

