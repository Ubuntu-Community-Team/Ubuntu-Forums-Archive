---
title: "DC Client"
date: 2005-04-08
forum: Desktop Environments
---

### Post by JoernErik on 2005-04-08
Hi there!

--------------------------------------------------------------------------------
Since I'm a complete n00b, please be spesific...  :-? 
--------------------------------------------------------------------------------

Where and how can i get a _WORKING_ dc-client?

I'm quite familiar with the apt-get function now, but there's no dc client in the current repository as I can see...

---

### Post by kleeman on 2005-04-08
There are two (dcgui and dcgui-qt) in the universe repository. To enable this follow the directions here:
[http://ubuntuguide.org/#repositories](http://ubuntuguide.org/#repositories)

---

### Post by doclivingston on 2005-04-08
Personally I've always had trouble with getting dcgui (the GTk one) configured properly, even for the DC hub for our house; dcgui-qt works pretty well though.

You can also use DC++ via wine, if you really want to use DC++, although I've seens issues when it tries to catalogue large directories.

---

### Post by zwaardmeester on 2005-04-15
I am using DC++ with Wine. The guide that describes it very well is

[http://www.linux-militia.net/howtos/D++/d++.html](http://www.linux-militia.net/howtos/D++/d++.html)

I got a little problem though; every time I close DC++ (and wine), wineserver keeps alive. When I restart dc++ (in the same session) it gives an port-in-use error. I solved this problem with this little script:

#!/bin/sh
/usr/lib/wine/wineserver -k
trickle -u 40 wine /home/leo/.wine/fake_windows/Program\ Files/DC++/DCPlusPlus.exe

Ps. I use the "trickle"  program to limit my upload bandwidth (in my case to 40 kb/s). See the trickle-man page for more information.

EDIT: for some reason, dc++ keeps running when you close it. You can close it with "/usr/lib/wine/wineserver -k"  though. See SystemTools->SystemMonitor for more info about running aps.

---

### Post by Dandy on 2005-04-30
You can use a good DC client Valknut from adress [http://peppesbodega.nu/turban/tumbo/Debian%20Packages/Apps/Valknut/](http://peppesbodega.nu/turban/tumbo/Debian%20Packages/Apps/Valknut/)

or try DC++ for Linux 

[http://www.ubuntuforums.org/showthread.php?t=28378](http://www.ubuntuforums.org/showthread.php?t=28378)

---

### Post by b3nw on 2005-04-30
I could get DC++ working up untill I tried to download a file then BOOM crash.  ](*,)

---

### Post by ramai on 2005-05-20
thanks for the dcgui thing
thanks!  \\:D/

---

### Post by drytear on 2007-07-22
my valknut won't start downloading. I hit "download" , it adds the transfer to the transfer window but nothing moves .. it's not downloading, i have active mode on. what could be wrong?

---

