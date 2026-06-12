---
title: "How to add custom pictures (as transitions) in &quot;Change Background...&quot; dialog box"
date: 2021-05-07
forum: Desktop Environments
---

### Post by linuxleaf2 on 2021-05-07
Hello,

I have a set of some pictures I downloaded off of internet that I want to use as wallpapers but also have them transition automatically just like the other picture/wallpaper sets available in the "Change Background..." dialog box.

For that, I have done the following
1. Copied the images to a folder called "citylife" in /usr/share/backgrounds
2. Set the ownership of the folder and all the images in it to root and set the file permissions same as other images in other folders i.e. "-rw-r--r--"
3. Created a file called city-timed.xml (see below) that sets the transitions for those images
4. Created a file called citylife-wallpapers.xml in /usr/share/gnome-background-properties (see below)
5. Set the ownership of the citylife-wallpapers.xml to root and set its permissions same as other files in the directory "-rw-r--r--"
6. Logged out and back in. (Even restarted the machine)

However, the set of images is still not even appearing inside the dialog box leave alone as a transition set (sorry I don't know the exact name used for such a set - basically I am referring to the set of images that change automatically as time passes).

Could anyone tell me what is missing in the steps above ?

(I looked at [this post]("https://ubuntuforums.org/showthread.php?t=2033019") as I was trying to go about doing this.)

Thanks for your time ! :)

Contents of city-timed.xml
=======================
```

<background>
  <starttime>
    <year>2009</year>
    <month>08</month>
    <day>04</day>
    <hour>00</hour>
    <minute>00</minute>
    <second>00</second>
  </starttime>
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/citylife/1c0e71348bb67c28272840c34c0d18a2.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/citylife/1c0e71348bb67c28272840c34c0d18a2.jpg</from>
    <to>/usr/share/backgrounds/citylife/cityscape-1619835007537-6202.jpg</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/citylife/cityscape-1619835007537-6202.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/citylife/cityscape-1619835007537-6202.jpg</from>
    <to>/usr/share/backgrounds/citylife/cup_coffee_coffee_machine_191312_1440x900.jpg</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/citylife/cup_coffee_coffee_machine_191312_1440x900.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/citylife/cup_coffee_coffee_machine_191312_1440x900.jpg</from>
    <to>/usr/share/backgrounds/citylife/goodwp.com_32307.jpg</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/citylife/goodwp.com_32307.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/citylife/goodwp.com_32307.jpg</from>
    <to>/usr/share/backgrounds/citylife/iStock-685668626WEB.jpg</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/citylife/iStock-685668626WEB.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/citylife/iStock-685668626WEB.jpg</from>
    <to>/usr/share/backgrounds/citylife/man-people-coffee-702251.jpg</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/citylife/man-people-coffee-702251.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/citylife/man-people-coffee-702251.jpg</from>
    <to>/usr/share/backgrounds/citylife/NlXGIR.webp</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/citylife/NlXGIR.webp</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/citylife/NlXGIR.webp</from>
    <to>/usr/share/backgrounds/citylife/pexels-burst-373912.jpg</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/citylife/pexels-burst-373912.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/citylife/pexels-burst-373912.jpg</from>
    <to>/usr/share/backgrounds/citylife/pexels-burst-374132.jpg</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/citylife/pexels-burst-374132.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/citylife/pexels-burst-374132.jpg</from>
    <to>/usr/share/backgrounds/citylife/pexels-chevanon-photography-302899.jpg</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/citylife/pexels-chevanon-photography-302899.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/citylife/pexels-chevanon-photography-302899.jpg</from>
    <to>/usr/share/backgrounds/citylife/pexels-clem-onojeghuo-221442.jpg</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/citylife/pexels-clem-onojeghuo-221442.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/citylife/pexels-clem-onojeghuo-221442.jpg</from>
    <to>/usr/share/backgrounds/citylife/pexels-isabella-mendes-858480.jpg</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/citylife/pexels-isabella-mendes-858480.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/citylife/pexels-isabella-mendes-858480.jpg</from>
    <to>/usr/share/backgrounds/citylife/pexels-josh-sorenson-139303.jpg</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/citylife/pexels-josh-sorenson-139303.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/citylife/pexels-josh-sorenson-139303.jpg</from>
    <to>/usr/share/backgrounds/citylife/pexels-kaboompics-com-6053.jpg</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/citylife/pexels-kaboompics-com-6053.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/citylife/pexels-kaboompics-com-6053.jpg</from>
    <to>/usr/share/backgrounds/citylife/pexels-snapwire-234507.jpg</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/citylife/pexels-snapwire-234507.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/citylife/pexels-snapwire-234507.jpg</from>
    <to>/usr/share/backgrounds/citylife/pexels-steven-arenas-314374.jpg</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/citylife/pexels-steven-arenas-314374.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/citylife/pexels-steven-arenas-314374.jpg</from>
    <to>/usr/share/backgrounds/citylife/pexels-tim-gouw-94849.jpg</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/citylife/pexels-tim-gouw-94849.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/citylife/pexels-tim-gouw-94849.jpg</from>
    <to>/usr/share/backgrounds/citylife/pexels-tookapic-9708.jpg</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/citylife/pexels-tookapic-9708.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/citylife/pexels-tookapic-9708.jpg</from>
    <to>/usr/share/backgrounds/citylife/photo-1521017432531-fbd92d768814.jpeg</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/citylife/photo-1521017432531-fbd92d768814.jpeg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/citylife/photo-1521017432531-fbd92d768814.jpeg</from>
    <to>/usr/share/backgrounds/citylife/train-at-subway-station-5k-9l.jpg</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/citylife/train-at-subway-station-5k-9l.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/citylife/train-at-subway-station-5k-9l.jpg</from>
    <to>/usr/share/backgrounds/citylife/1c0e71348bb67c28272840c34c0d18a2.jpg</to>
  </transition>
</background>



```

Contents of citylife-wallpapers.xml
==========================
```

<?xml version="1.0"?>
<!DOCTYPE wallpapers SYSTEM "gnome-wp-list.dtd">
<wallpapers>
    <wallpaper deleted="false">
    <name>City Life Wallpapers</name>
    <filename>/usr/share/backgrounds/citylife/city-timed.xml</filename>
    <options>zoom</options>
    <shade_type>solid</shade_type>
    <pcolor>#3465a4</pcolor>
    <scolor>#000000</scolor>
    </wallpaper>
<wallpapers>



```

---

### Post by grahammechanical on 2021-05-08
I see nothing wrong with the contents of city-timed.xml. If you go to /usr/share/backgrounds/ you should see a folder called contest. I suggest putting city-timed.xml into that folder. You may also need to reboot.

I am using an install of Ubuntu that started out as 17.04 and then was upgraded to 18.04 and on to 20.04. In the contest folder I see bionic.xml, focal.xml & zesty.xml. And the three background slide shows appear in System Settings>Background as options to select.

You may need also to put the images in the backgrounds folder and adjust the paths in the city-timed.xml file accordingly. That is if having the images in their own folder does not work.

What you want to do can be done. I did this many years ago. You are heading in the right direction.

Regards

---

### Post by linuxleaf2 on 2021-05-08
I tried to look at what was different in the way I was approaching the problem vs how its working already and thought that there must be a special list where I need to register my folder name or image set name. I started looking for it using the dconf tool and stumbled on the following key:
 [COLOR=#0000ff]**/org/gnome/desktop/background/picture-uri**[/COLOR]
This key had the direct path to another transition xml file for another set. Obviously I couldn't resist jamming in the path to city-timed,xml in that field and lo behold it worked (transitions and all) !

That said, when I open the Change Background dialog, although I see my background image as a transition image set at the very top (i.e. with the small clock/watch icon) - and it's working as expected - but I still do not see the images from this set in the list of images in the bottom part of the dialog box. This leads me to believe there is some other setting I am missing to surface images in this folder in the dialog box (probably some sort of registration that I started looking for in dconf).

---

### Post by skunkmilk on 2021-11-15
Thanks for this post. It got me going. I had not considered checking Gnome Tweaks. 

Were you ever able to find the setting in dconf to add the images in settings like the one for the stock focal.xml file?

---

