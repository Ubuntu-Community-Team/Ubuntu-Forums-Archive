---
title: "Ubuntu Top Panel Locked to the Right Side"
date: 2009-12-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by MrNaky on 2009-12-14
My Ubuntu Top Panel was locked to the right side...

   Recently, I bought my wife a Dell Netbook (Vostro A90) to use for work as she travels frequently and packs light. It shipped with Ubuntu 8.04, which significantly lowered the total price and complimented our now all Linux household. A couple of days ago she comes to me with a simple problem. "I want my desktop to look like my other computer. I don't like this bar thing" referencing a custom Dell "desktop-mode" with a HUGE applet bar across the desktop. This was new to me, but still sounded fairly simple. 

A quick check under the Ubuntu panel icon revealed a "Switched Desktop Mode" listed near the bottom. I launched the app and selected "Classic Desktop" expecting to be done. Alas, no. The top panel was vertical across the right side of the screen. Okey Dokey, I'll just drag in to the Top. Nope. I'll just right-click to unlock and then drag it. Nope. No unlock option. I'll just take a peek at the properties. The orientation is there, however I can't change it. "Some of these properties are locked down." Bummer.

I hit the forums. The first Google result led me to [http://www.mattcutts.com/blog/moving-the-locked-top-panel-in-ubuntu-gnome/](http://www.mattcutts.com/blog/moving-the-locked-top-panel-in-ubuntu-gnome/). This looks like the right place, and I like how the author described the journey. I fire up gconf-editor and navigate to the “apps” > “panel” > “global” to uncheck the "locked-down" box. It's however already unchecked. I verify the same <schema> keys that I can't change that seem like the logical answer noted in the blog. Argh. I keep searching the Google. Post after post after post, fixes are offered but don't seem to work for me. I search for keys and values in gconf-editor that should lead me to victory. "Right", "locked", "panel", "orientation", and all of these keys look correct! Nothing matches what I'm seeing in the panel properties. The panel remains, almost mocking my every attempt.

Finally, I go back to Matt's post and dissect line by line what he encountered. I decided to hit the configuration files to find the setting that matches the panel orientation, as the gconf-editor keys do not match the panel. I get lucky. A few quick "ls" commands through the .gconf directories and I hit gold...

/home/<user>/.gconf/apps/panel/toplevels/top_panel_screen0/%gconf.xml

I gksudo gedit the file (after an earful from the #ubuntu Freenet channel about the sudo/gksudo differences). And there it is: <stringvalue>right</stringvalue> for the top panel orientation. Changed the value to "top" (without quotes), saved, sudo pkill gnome-panel, and about 2 seconds later the panels re-launched themselves with one at the top, and one at the bottom. I am still lost as to why this setting wasn't in the gconf-editor, but it's done. After a quick reboot, the panels are still in the correct places.

Mission complete. Hero of the day.

Thanks to Matt Cutts and ubuntuforums.com for the posts necessary to track down a solution! I hope this helps you too.

---

### Post by bobcollard on 2009-12-15
> **MrNaky said:**
> My Ubuntu Top Panel was locked to the right side...

   Recently, I bought my wife a Dell Netbook (Vostro A90) to use for work as she travels frequently and packs light. It shipped with Ubuntu 8.04, which significantly lowered the total price and complimented our now all Linux household. A couple of days ago she comes to me with a simple problem. "I want my desktop to look like my other computer. I don't like this bar thing" referencing a custom Dell "desktop-mode" with a HUGE applet bar across the desktop. This was new to me, but still sounded fairly simple. 

A quick check under the Ubuntu panel icon revealed a "Switched Desktop Mode" listed near the bottom. I launched the app and selected "Classic Desktop" expecting to be done. Alas, no. The top panel was vertical across the right side of the screen. Okey Dokey, I'll just drag in to the Top. Nope. I'll just right-click to unlock and then drag it. Nope. No unlock option. I'll just take a peek at the properties. The orientation is there, however I can't change it. "Some of these properties are locked down." Bummer.

I hit the forums. The first Google result led me to [http://www.mattcutts.com/blog/moving-the-locked-top-panel-in-ubuntu-gnome/](http://www.mattcutts.com/blog/moving-the-locked-top-panel-in-ubuntu-gnome/). This looks like the right place, and I like how the author described the journey. I fire up gconf-editor and navigate to the “apps” > “panel” > “global” to uncheck the "locked-down" box. It's however already unchecked. I verify the same <schema> keys that I can't change that seem like the logical answer noted in the blog. Argh. I keep searching the Google. Post after post after post, fixes are offered but don't seem to work for me. I search for keys and values in gconf-editor that should lead me to victory. "Right", "locked", "panel", "orientation", and all of these keys look correct! Nothing matches what I'm seeing in the panel properties. The panel remains, almost mocking my every attempt.

Finally, I go back to Matt's post and dissect line by line what he encountered. I decided to hit the configuration files to find the setting that matches the panel orientation, as the gconf-editor keys do not match the panel. I get lucky. A few quick "ls" commands through the .gconf directories and I hit gold...

/home/<user>/.gconf/apps/panel/toplevels/top_panel_screen0/%gconf.xml

I gksudo gedit the file (after an earful from the #ubuntu Freenet channel about the sudo/gksudo differences). And there it is: <stringvalue>right</stringvalue> for the top panel orientation. Changed the value to "top" (without quotes), saved, sudo pkill gnome-panel, and about 2 seconds later the panels re-launched themselves with one at the top, and one at the bottom. I am still lost as to why this setting wasn't in the gconf-editor, but it's done. After a quick reboot, the panels are still in the correct places.

Mission complete. Hero of the day.

Thanks to Matt Cutts and ubuntuforums.com for the posts necessary to track down a solution! I hope this helps you too.
Next time right click on the panel, find Properties and work from that menu, it's quicker and does the same thing

---

### Post by JohnnyC35 on 2010-03-14
Actually I am having a similar issue with the Karmic Netbook Remix. I have removed the ugly netbook remix huge icons for kids layout so I can just have a regular desktop but I cannot edit my panel. I have tried rick-clicking it but there is no add to panel option, I cannot remove anything from it, and the only thing I can do in properties is resize how big the stupid thing is. lockdown is unchecked in gconf and I checked '/home/john/.gconf/apps/panel/toplevels/top_panel_screen0/%gconf.xml' but there is nothing in there. very frusterating. at least I can use the menu via control+f1. I don't see an option to edit panels there either :^)

---

### Post by bobcollard on 2010-03-14
> **JohnnyC35 said:**
> Actually I am having a similar issue with the Karmic Netbook Remix. I have removed the ugly netbook remix huge icons for kids layout so I can just have a regular desktop but I cannot edit my panel. 
I don't have a netbook, just a laptop.  Have you tried Xubuntu instead of Gnome Ubuntu?  That's where I right click the panel and find +Add New Items, Customize Panel and things.  Xubuntu is a good desktop for smaller or older computers with limited RAM and HDs  It is also very functional, fast and easy to customize.

---

### Post by JohnnyC35 on 2010-03-15
apparently it's a Lucid thing. I forgot that that iswhat I had on my computer. I have since then put Karmic back on my computer and am not having many issues (other tan rtorrent but that's in a different thread). I am using the netbook remix because it is apparently optimized for Atom processors, which I have.

---

### Post by vcrpcant on 2011-04-21
thanks for pointing me in the right direction:
gconf-editor in terminal, then:
/apps/panel/toplevels/top_panel_screen0/orientation
changed the key from "left" to "bottom" and solved my problem, because I couldn't find free space to right-click in the panel and select "properties" :)

---

