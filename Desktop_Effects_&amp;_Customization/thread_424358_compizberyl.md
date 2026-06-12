---
title: "compiz/beryl"
date: 2007-04-26
forum: Desktop Effects &amp; Customization
---

### Post by ezman5086 on 2007-04-26
Hey, thorugh online tutorials i managed to get my drivers installed.  I have a ati x1300.  Now, I just need to install beryl so i can run it.  From the directions i had been following, I went to the synaptic package manager.  I searched beryl, found it... and all the related stuff...

however, beryl won't install.

it says it depends on beryl-settings and beryl-manager.  the beryl manager says it won't install because it says beryl is not going to be installed.  beryl-settings says it won't install because it relies on beryl-settings-bindings.  beryl-settings-bindings won't install giving me this message:


beryl-settings-bindings:
  Depends: python (<2.5) but 2.5.1~rc1-0ubuntu3 is to be installed

ok, so i searched for python, and tried to downgrade just to see what it would do.  no luck.  then i installed the python that has support for all levels of python.... nothing.

i thought i had the hardest part of beryl business (the graphics card) finished..help?

---

### Post by evilc on 2007-04-26
What version of Ubuntu are you running? depending on that have a look at this lead should hopefully help you.  [http://ubuntuforums.org/showthread.php?t=272104](http://ubuntuforums.org/showthread.php?t=272104)

---

### Post by ezman5086 on 2007-04-26
i'm using feisty with an ati radeon x1300

---

### Post by ezman5086 on 2007-04-26
okay, i still haven't been able to get beryl installed but i've been fooling around a bit, and now when i click system>preferences>desktop effects, i no longer get a white screen.  everything shows up except for the titlebars and window borders.  I guess this means that I need to get beryl installed?.... i think this is just xgl, but i'm a newb so i could be wrong.

I also have the Emerald theme manager installed... that works great, but the themes dont show up (because there are no titlebars or window borders).  

i still can't get the dependencies to stop giving me errors.... how do i get python to go lower?  Is there any way to make it ignore the dependencies?  Has anyone successfully gotten beryl installed in feisty?

---

### Post by ezman5086 on 2007-04-26
bump

---

### Post by ezman5086 on 2007-04-27
ok, I ended up reinstalling ubuntu.  after setting everything up using these directions:
[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL)

... I got beryl to install and xgl is installed and everything.  now, when i choose xgl as the session before i log in, everything is scrambled.  does this mean i have no hope a new version is released?

---

### Post by ericesque on 2007-04-27
ez, I know this may be hard to swallow, but composite on AMD seems more hassle than it is worth.  I have managed to get it working on an x600, but each time it became unstable.  Remember that it is really alpha software-- nowhere near stable for everyone.  I would just try to enjoy the freedom of Ubuntu and let beryl/compiz brew a while longer.

---

### Post by Neuralgia on 2007-04-29
same here.

what's weird, is that in edgy everything worked perfectly... on both, x300, and x1300 cards (desktop and laptop)

---

### Post by Fire_Chief on 2007-07-27
I'm experiencing the same problem on Feisty however it only occurs when I set Beryl to startup automatically in the sessions startup control panel. I'm using XGL on an ATI x1400. I can login to a regular XGL session fine and start Beryl-Manager manually. This works every time. Not sure why the auto start causes the scrambled screen. BTW, everything still works in the scrambled screen (can click on menus, etc.) so I'm able to log out of the desktop session. So for now I'm stuck with manual startup of Beryl...not ideal but it works.

---

