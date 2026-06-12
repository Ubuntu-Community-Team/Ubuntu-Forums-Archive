---
title: "&quot;Desktop effects could not be be enabled&quot;"
date: 2007-07-27
forum: Desktop Effects &amp; Customization
---

### Post by tom1g on 2007-07-27
On my brand new ubuntu installation, desktop effects could not "be be" enabled...
I installed ATI Restricted drivers and changed one part in xorg.conf (I enabled Composite extension).


How the hell can I make my Desktop Effcets work? Every help is appreciated :confused:

---

### Post by tom1g on 2007-07-27
C'mon, I rellay can't figure out ******* solution :(:(:confused::confused::(:(

---

### Post by Just-trevor on 2007-07-27
If you read a little you would know

Go to system and Administration and restricted drivers manager
if restricted drivers manager isn't there then right click on the system menu and click edit menus, find restricted drivers manager and check it off, then enable nVidia driver and try again

---

### Post by tom1g on 2007-07-28
> **Just-trevor said:**
> If you read a little you would know

Go to system and Administration and restricted drivers manager
if restricted drivers manager isn't there then right click on the system menu and click edit menus, find restricted drivers manager and check it off, then enable nVidia driver and try again

erm... but I have ATI X200 Radeon :))

When I check ATI res. drivers off,  Enabling Desktop Effects results with plain white screen, and only the cursor can be seen :S

---

### Post by tom1g on 2007-07-28
Do I really have to bump this topic every single time :mad: :mad:

---

### Post by decoherence on 2007-08-01
Hi, I'm also having this problem. I install the ATI driver via Restricted Drivers Management, reboot the computer, try to enable Desktop Effects and get "the Composite extension is not available."

xorg.conf shows I am indeed using the fglrx driver

/var/log/Xorg.0.log tells me "(**) Extension "Composite" is disabled"

I enabled it manually in xorg.conf which allowed Desktop Effects to open, but when I try to activate them it stalls for a minute then tells me they couldn't be activated. I set xorg.conf back, not wanting to anger the ubuntu gods.

I'll post if I find out anything else.

---

### Post by espmartin on 2007-08-02
> **decoherence said:**
> ...
I enabled it manually in xorg.conf which allowed Desktop Effects to open, but when I try to activate them it stalls for a minute then tells me they couldn't be activated...
Exactly what I did and got... Anyone have any ideas?

---

### Post by OZTack on 2007-08-02
Hi, you won't get the desktop effects working easily with the ATI - proprietry - FGLRX drivers.
It doesn't support the Composite made...
You need to try the Radeon drivers  if you are set on using the desktop effects
[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")
Although - maybe you can stick with your system and try Compiz as you eye candy?

---

### Post by espmartin on 2007-08-02
> **OZTack said:**
> Hi, you won't get the desktop effects working easily with the ATI - proprietry - FGLRX drivers.
It doesn't support the Composite made...
You need to try the Radeon drivers  if you are set on using the desktop effects
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
Although - maybe you can stick with your system and try Compiz as you eye candy?

Hello Oz,

Can you point me in a good direction for Ubuntu eye candy? Compiz.

---

### Post by OZTack on 2007-08-02
Well I belive Compiz and Beryl have merged.... [HERE]("http://www.beryl-project.org/")
May take a bit of work though :)

---

### Post by espmartin on 2007-08-02
Thanks Oz,

Have you had any luck w/the "eye candy" stuff? I've read over and over how
many newbies have "broken" their Lnux installs. I've done so and had to
reinstall, like 3 times!!!

---

### Post by OZTack on 2007-08-02
Heh - you are dangerous - I am a complete beginner at Linux/ubuntu - 72 hours and counting :lol:

However - I have been able to get Beryl going by followiing the instructions on the various forums , and the web. I have been using the open source ("radeon")  ATI drivers FWIW - AND I found beryl listed in my add and remove programs menu :D There is a sticky in the "Absolute begginers " Forum that deals with Beryl, another with ATI problems as well  as heaps of posts about graphics issues - have a look there too

With JUST the radeon drivers, the desktop effects work fine BTW. What I am asking in the forums is - What is the downside of these drivers - if any?

So far - no broken installs / reinstalls......

---

