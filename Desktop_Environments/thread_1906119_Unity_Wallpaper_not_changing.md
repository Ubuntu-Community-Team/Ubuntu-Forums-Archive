---
title: "Unity Wallpaper not changing"
date: 2012-01-08
forum: Desktop Environments
---

### Post by Danial on 2012-01-08
Hi,

I have searched and checked for the following issue but unable to find a resolution. In case, I missed one, I apologize for re-posting the question - please point me to right direction, Thanks.

Recently installed/upgraded to Ubuntu 11.10, activated 2D, all appears to be working fine and I sure like it (though still learning my way around). I have 3 user setup, one as admin user and others as standard user.

Here is my issue: One of the standard user's wallpaper changes automatically (at first I even didn't know that it is possible) however, the other two users (admin and 2nd. standard user) don't have that option available. These two users don't have the **Contest** button available at all. I have checked (enclosed) the background-1.xml for both and with my little knowledge found no difference; except that 'Contest' button is not available to the one named 'not-working-background-1.xml' I am attaching two files named: working... and not-working... plus a screenshot of the Appearance window. I hope, I am not wrong to assume that python is installed to the system since the Appearance app is working in at least one log-in. By the way, both of these files are located in their respective folder "usr/share/backgrounds/contest". I just changed the name here for clarification purpose only and no actual changes were made to either  the content or the name of the file. 

Any advice, help, guidance and your time is very appreciated.

Danial

[IMG]/home/desktop/working-appearance-window-screenshot.png[/IMG]

**Working 'background-1.xml':**

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
<!-- This animation will start at midnight. -->
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/Stalking_Ocelot_by_Sayantan_Chaudhuri.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/Stalking_Ocelot_by_Sayantan_Chaudhuri.jpg</from>
    <to>/usr/share/backgrounds/Small_flowers_by_Dariusz_Duma.jpg</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/Small_flowers_by_Dariusz_Duma.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/Small_flowers_by_Dariusz_Duma.jpg</from>
    <to>/usr/share/backgrounds/WildWheat_by_Brian_Burt.jpg</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/WildWheat_by_Brian_Burt.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/WildWheat_by_Brian_Burt.jpg</from>
    <to>/usr/share/backgrounds/JardinPolar_by_CarmenGloria_Gonzalez.jpg</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/JardinPolar_by_CarmenGloria_Gonzalez.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/JardinPolar_by_CarmenGloria_Gonzalez.jpg</from>
    <to>/usr/share/backgrounds/Buck_off!_by_SirPecanGum.jpg</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/Buck_off!_by_SirPecanGum.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/Buck_off!_by_SirPecanGum.jpg</from>
    <to>/usr/share/backgrounds/Not_Alone_by_Deacon_MacMillan.jpg</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/Not_Alone_by_Deacon_MacMillan.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/Not_Alone_by_Deacon_MacMillan.jpg</from>
    <to>/usr/share/backgrounds/Darkening_Clockwork_by_Matt_Katzenberger.jpg</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/Darkening_Clockwork_by_Matt_Katzenberger.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/Darkening_Clockwork_by_Matt_Katzenberger.jpg</from>
    <to>/usr/share/backgrounds/The_Grass_aint_Greener_by_fix_pena.jpg</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/The_Grass_aint_Greener_by_fix_pena.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/The_Grass_aint_Greener_by_fix_pena.jpg</from>
    <to>/usr/share/backgrounds/Langelinie_Allé_by_SirPecanGum.jpg</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/Langelinie_Allé_by_SirPecanGum.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/Langelinie_Allé_by_SirPecanGum.jpg</from>
    <to>/usr/share/backgrounds/Dybbølsbro_Station_by_SirPecanGum.jpg</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/Dybbølsbro_Station_by_SirPecanGum.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/Dybbølsbro_Station_by_SirPecanGum.jpg</from>
    <to>/usr/share/backgrounds/PurpleDancers_by_Emilio_Merlino.jpg</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/PurpleDancers_by_Emilio_Merlino.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/PurpleDancers_by_Emilio_Merlino.jpg</from>
    <to>/usr/share/backgrounds/Power_of_Words_by_Antonio_Litterio.jpg</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/Power_of_Words_by_Antonio_Litterio.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/Power_of_Words_by_Antonio_Litterio.jpg</from>
    <to>/usr/share/backgrounds/Momiji_Dream_by_Deacon_MacMillan.jpg</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/Momiji_Dream_by_Deacon_MacMillan.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/Momiji_Dream_by_Deacon_MacMillan.jpg</from>
    <to>/usr/share/backgrounds/Mount_Snowdon,_Wales_by_Adam_Vellender.jpg</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/Mount_Snowdon,_Wales_by_Adam_Vellender.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/Mount_Snowdon,_Wales_by_Adam_Vellender.jpg</from>
    <to>/usr/share/backgrounds/Stalking_Ocelot_by_Sayantan_Chaudhuri.jpg</to>
  </transition>
</background>
```

**NOT Working 'background-1.xml':**
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
<!-- This animation will start at midnight. -->
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/Stalking_Ocelot_by_Sayantan_Chaudhuri.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/Stalking_Ocelot_by_Sayantan_Chaudhuri.jpg</from>
    <to>/usr/share/backgrounds/Small_flowers_by_Dariusz_Duma.jpg</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/Small_flowers_by_Dariusz_Duma.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/Small_flowers_by_Dariusz_Duma.jpg</from>
    <to>/usr/share/backgrounds/WildWheat_by_Brian_Burt.jpg</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/WildWheat_by_Brian_Burt.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/WildWheat_by_Brian_Burt.jpg</from>
    <to>/usr/share/backgrounds/JardinPolar_by_CarmenGloria_Gonzalez.jpg</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/JardinPolar_by_CarmenGloria_Gonzalez.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/JardinPolar_by_CarmenGloria_Gonzalez.jpg</from>
    <to>/usr/share/backgrounds/Buck_off!_by_SirPecanGum.jpg</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/Buck_off!_by_SirPecanGum.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/Buck_off!_by_SirPecanGum.jpg</from>
    <to>/usr/share/backgrounds/Not_Alone_by_Deacon_MacMillan.jpg</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/Not_Alone_by_Deacon_MacMillan.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/Not_Alone_by_Deacon_MacMillan.jpg</from>
    <to>/usr/share/backgrounds/Darkening_Clockwork_by_Matt_Katzenberger.jpg</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/Darkening_Clockwork_by_Matt_Katzenberger.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/Darkening_Clockwork_by_Matt_Katzenberger.jpg</from>
    <to>/usr/share/backgrounds/The_Grass_aint_Greener_by_fix_pena.jpg</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/The_Grass_aint_Greener_by_fix_pena.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/The_Grass_aint_Greener_by_fix_pena.jpg</from>
    <to>/usr/share/backgrounds/Langelinie_Allé_by_SirPecanGum.jpg</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/Langelinie_Allé_by_SirPecanGum.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/Langelinie_Allé_by_SirPecanGum.jpg</from>
    <to>/usr/share/backgrounds/Dybbølsbro_Station_by_SirPecanGum.jpg</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/Dybbølsbro_Station_by_SirPecanGum.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/Dybbølsbro_Station_by_SirPecanGum.jpg</from>
    <to>/usr/share/backgrounds/PurpleDancers_by_Emilio_Merlino.jpg</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/PurpleDancers_by_Emilio_Merlino.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/PurpleDancers_by_Emilio_Merlino.jpg</from>
    <to>/usr/share/backgrounds/Power_of_Words_by_Antonio_Litterio.jpg</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/Power_of_Words_by_Antonio_Litterio.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/Power_of_Words_by_Antonio_Litterio.jpg</from>
    <to>/usr/share/backgrounds/Momiji_Dream_by_Deacon_MacMillan.jpg</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/Momiji_Dream_by_Deacon_MacMillan.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/Momiji_Dream_by_Deacon_MacMillan.jpg</from>
    <to>/usr/share/backgrounds/Mount_Snowdon,_Wales_by_Adam_Vellender.jpg</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/Mount_Snowdon,_Wales_by_Adam_Vellender.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/Mount_Snowdon,_Wales_by_Adam_Vellender.jpg</from>
    <to>/usr/share/backgrounds/Stalking_Ocelot_by_Sayantan_Chaudhuri.jpg</to>
  </transition>
</background>
```

---

### Post by grahammechanical on 2012-01-08
First thing you should know, there is only one background-1.xml script because it is found in /usr/share/backgrounds/contest which is in the File System and not in each user's home folder. That is why what seems to be two files are identical. They are the same file being looked at from a different usr's home folder.

Second, your screenshot has not appeared in your post. So, we cannot see what you mean by the contest button.

I have two users on my system. One administrator and one standard and I can select the background slide show option (icon of a background image with a little clock superimposed) in either user account. I do not know what you mean when you say:

> These two users don't have the **Contest** button available at all.

I have being doing an experiment to see if I can replicate your problem but as it takes 30 minutes for each background to change it is a slow experiment.

I have found that in the administrator account it does not matter if it is 3D or 2D the slide show works. I am now trying to find out if the slide shows works in a standard user's account in either 3D or 2D or both.

Regards.

---

### Post by Danial on 2012-01-08
Thanks for your response and time to look into this matter.

> **grahammechanical said:**
> First thing you should know, there is only one background-1.xml script because it is found in /usr/share/backgrounds/contest which is in the File System and not in each user's home folder. That is why what seems to be two files are identical. They are the same file being looked at from a different usr's home folder.

Thanks for pointing out above mentioned fact (I didn't know).

> Second, your screenshot has not appeared in your post. So, we cannot see what you mean by the contest button.

My bad that I was not able to post the image properly (I guess now I did it right). What I was referencing to is when I do a right click on the desktop and choose the option 'Change Desktop background' that brings the window title 'Appearance'. On the left side are the pictures or backgrounds to choose and just to the right of that upper side, there is a clickable button named 'Contest'. Having said that, in other threads/solutions, it is mentioned that this option need to be activated to have a desktop wallpaper change automatically. 

>  ... (icon of a background image with a little clock superimposed) ...  

**OKAY, I got it. ** - key was to choose the icon with the clock on it and that brings the 'Contest' button (changed the image at the same time).

I guess, in thirty minutes, I will see a different wallpaper.

**[COLOR="DarkGreen"][SIZE="2"]Thank you so very much for your help and time.[/SIZE][/COLOR]**


> I have being doing an experiment to see if I can replicate your problem but as it takes 30 minutes for each background to change it is a slow experiment.

Now you don't have to waste your time on my this issue.

Once again, thanks a lot for your help.
Regards,
Danial

---

### Post by grahammechanical on 2012-01-08
Glad to have helped. It took me a while when I installed 11.10 to work out that the little clock icon indicated a slide show. I have just proved that the slide show will work in a standard user 2D mode.

Regards.

---

### Post by Danial on 2012-01-08
[QUOTEI have just proved that the slide show will work in a standard user 2D mode.
[/QUOTE]

I will follow your steps. 
Thanks and Regards,
Danial.

---

