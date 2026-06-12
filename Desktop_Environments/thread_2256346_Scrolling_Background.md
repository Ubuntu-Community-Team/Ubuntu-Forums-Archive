---
title: "Scrolling Background"
date: 2014-12-11
forum: Desktop Environments
---

### Post by Drew_Gardner on 2014-12-11
Is there anyway to make it so that the desktop background is a series of images set to follow one another across the screen? The closest I've been able to find is to make a video and use that, but my editing skills are sub-par at best. 

I wanted to make it so that I could have a folder of comic pages and have the pages scroll across the screen in order. The tricky part is that I wanted it so that there would be multiple pages shown on the screen at a time (otherwise there would be a lot of empty space).

Any ideas on how to make this possible are greatly appreciated.

---

### Post by grahammechanical on 2014-12-11
In Ubuntu it is possible to set the default backgrounds as a slide show. The only difference between what is possible in Ubuntu and what you want is the amount of time each image is on the screen. All the Ubuntu wallpapers are kept in /usr/share/backgrounds. The script that controls the slide show is in usr/share/background/cosmic. The script for 14.04 is called trusty.xml. The script for 14.10 is called utopic.xml. It will open in a web browser and can be edited by Gedit but we need to launch Gedit with administrator privileges in order to save an edited file. This is a sample.

>   <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/Kronach_leuchtet_2014_by_Brian_Fox.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/Kronach_leuchtet_2014_by_Brian_Fox.jpg</from>
    <to>/usr/share/backgrounds/salcantayperu_by_Life_Nomadic.jpg</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/salcantayperu_by_Life_Nomadic.jpg</file>



As you can see each image is on screen for  <duration>1795.0</duration>. I assume that is seconds. The transition from one image to the next is   <transition>    <duration>5.0</duration>.

You can copy this xml file and then replace the references to the default images with references to your images. And adjust the duration as suits you. Note the importance of the correct path

> <file>/usr/share/backgrounds/salcantayperu_by_Life_Nomadic.jpg</file>


There is one more thing you should take note of. When we edit files like this backup copies are automatically made. The same file name is used but a tilde character ( ~ ) is put to the front of the name. This will make the file a hidden file but the system will still read the file. So, you may find duplicates showing up in the Appearance utility.

Regards.

---

### Post by Drew_Gardner on 2014-12-11
What I want to do isn't quite as simple as a slide show. Because of the size of comic pages, 2.5 - 3 images would be displayed at any given time. And with the scrolling, the amount of the images shown on the edges would be constantly changing. As one image is moved farther and farther off the screen, another is moved more and more onto the screen.

---

