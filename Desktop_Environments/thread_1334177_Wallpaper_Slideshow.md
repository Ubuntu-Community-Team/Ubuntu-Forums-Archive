---
title: "Wallpaper Slideshow"
date: 2009-11-22
forum: Desktop Environments
---

### Post by haihoo on 2009-11-22
I love the idea of a changing wallpaper for the GNOME Desktop.

In Karmic there is the cosmo-Slideshow that does this ... but not on my PC. I even learned how to make my own desktop slideshow XML-File, but it doesn't work too.

Every time I start Ubuntu (with my own Background-Slide or the cosmo slide). I got a new background, but it is not changing.

Strange: Everytime I save my own slide-xml (duration of 30 seconds) the background changes once but nevermore after that.

Perhaps some gnome settings are prevent the wallpaper from changing, but which? I use Desktop-Effects, but even without Effects the Wallpaper is not changing.

---

### Post by Hetor on 2009-11-22
Check out wallpapoz, I think it's on getdeb.

---

### Post by jwflammer on 2009-11-22
try coping my XML cobe here this might help 

> 
<background>
  <starttime>
    <year>2009</year>
    <month>01</month>
    <day>01</day>
    <hour>01</hour>
    <minute>01</minute>
    <second>01</second>
  </starttime>
<!-- This animation will start at midnight. -->
  <static>
    <duration>600.0</duration>
    <file>/usr/share/backgrounds/cosmos/cloud.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/cosmos/cloud.jpg</from>
    <to>/usr/share/backgrounds/cosmos/comet.jpg</to>
  </transition>
  <static>
    <duration>600.0</duration>
    <file>/usr/share/backgrounds/cosmos/comet.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/cosmos/comet.jpg</from>
    <to>/usr/share/backgrounds/cosmos/earth-horizon.jpg</to>
  </transition>
  <static>
    <duration>600.0</duration>
    <file>/usr/share/backgrounds/cosmos/earth-horizon.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/cosmos/earth-horizon.jpg</from>
    <to>/usr/share/backgrounds/cosmos/blue-marble-west.jpg</to>
  </transition>
  <static>
    <duration>600.0</duration>
    <file>/usr/share/backgrounds/cosmos/blue-marble-west.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/cosmos/blue-marble-west.jpg</from>
    <to>/usr/share/backgrounds/cosmos/galaxy-ngc3370.jpg</to>
  </transition>
  <static>
    <duration>600.0</duration>
    <file>/usr/share/backgrounds/cosmos/galaxy-ngc3370.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/cosmos/galaxy-ngc3370.jpg</from>
    <to>/usr/share/backgrounds/cosmos/helix-nebula.jpg</to>
  </transition>
  <static>
    <duration>600.0</duration>
    <file>/usr/share/backgrounds/cosmos/helix-nebula.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/cosmos/helix-nebula.jpg</from>
    <to>/usr/share/backgrounds/cosmos/jupiter.jpg</to>
  </transition>
  <static>
    <duration>600.0</duration>
    <file>/usr/share/backgrounds/cosmos/jupiter.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/cosmos/jupiter.jpg</from>
    <to>/usr/share/backgrounds/cosmos/sombrero.jpg</to>
  </transition>
  <static>
    <duration>600.0</duration>
    <file>/usr/share/backgrounds/cosmos/sombrero.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/cosmos/sombrero.jpg</from>
    <to>/usr/share/backgrounds/cosmos/whirlpool.jpg</to>
  </transition>
  <static>
    <duration>600.0</duration>
    <file>/usr/share/backgrounds/cosmos/whirlpool.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/cosmos/whirlpool.jpg</from>
    <to>/usr/share/backgrounds/cosmos/cloud.jpg</to>
  </transition>
</background>

that might help mine works just fine !!

---

### Post by Umang on 2009-12-22
Hi,
I'm having the same issue. It changes when I log in, but never by itself (I set the interval to 5 seconds, and transition to 1 second). Interestingly, if I same the xml file (just Ctrl + S without any changes to the xml), the background changes. Waiting doesn't help.

I don't have any desktop effects enabled.

Any ideas on what I should do?

Edit: Occasionally, it changes (and I'm doing something else at that time). But if I wait for it to change (with interval 10 seconds or so) nothing happens.

---

### Post by decrow06 on 2010-05-29
I am having this same problem in 10.04.  Can anyone help?

---

