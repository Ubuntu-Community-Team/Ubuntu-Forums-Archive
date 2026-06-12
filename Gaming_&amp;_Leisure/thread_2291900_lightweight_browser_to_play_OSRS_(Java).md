---
title: "lightweight browser to play OSRS (Java)?"
date: 2015-08-23
forum: Gaming &amp; Leisure
---

### Post by joo11 on 2015-08-23
Hi I'm new to Linux, and I need a lightweight browser with very low CPU usage to play OSRS ([http://oldschool.runescape.com/game?world=369](http://oldschool.runescape.com/game?world=369))... I heard that Midori supports javascpit but I couldn't make it work :/

Can someone help me? I understand very little about Linux... I use XUBUNTU.

---

### Post by QIII on 2015-08-23
Hello and welcome to the Forums!

"couldn't make it work" is a bit vague.  Could you tell us what you attempted to do and what behavior you observed?

---

### Post by joo11 on 2015-08-23
> **QIII said:**
> Hello and welcome to the Forums!

"couldn't make it work" is a bit vague.  Could you tell us what you attempted to do and what behavior you observed?

[ATTACH=CONFIG]264017[/ATTACH]

---

### Post by QIII on 2015-08-23
Please don't post such large images.  Ubuntu Forums users come from all around the world.  Some people have slow connections and small bandwidth quotas.  A large image may put them over the top and cost them money -- or take a long time to download.

I just attempted to open that page.  Even with Oracle Java 8 Update 51 installed, I got the "Activate Java" warning.  I would say the issue is with the website.

That said, have you installed Java?

---

### Post by joo11 on 2015-08-23
> **QIII said:**
> Please don't post such large images.  Ubuntu Forums users come from all around the world.  Some people have slow connections and small bandwidth quotas.  A large image may put them over the top and cost them money -- or take a long time to download.

I just attempted to open that page.  Even with Oracle Java 8 Update 51 installed, I got the "Activate Java" warning.  I would say the issue is with the website.

That said, have you installed Java?
I did this to install java. I guess it's working because I could play on Firefox, but the CPU usage is too high :/
[COLOR=#000000]sudo add[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#000000]apt[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#000000]repository webupd8team[/COLOR][COLOR=#666600]/[/COLOR][COLOR=#000000]java
sudo apt[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#000088]get[/COLOR][COLOR=#000000] update
sudo apt[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#000088]get[/COLOR][COLOR=#000000] install oracle[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#000000]java8[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#000000]installer

maybe I need to do something else to work on Midori?

[SIZE=2]edit:[/SIZE]
[/COLOR]**[SIZE=2]Java doesn't work, applets don't show up[/SIZE]**

[COLOR=#666666][FONT=Open Sans][SIZE=2]Java is supported in WebKitGTK+ since 1.1.22. If you need Java, you need to upgrade to at least that version. Sun/ Oracle Java as well as IcedTea are known to work. Distribution specific setup might be required, such as setting LD_LIBRARY_PATH to include the location of libxul.so and making a symbolic link for libnpjp2.so to /usr/lib/mozilla.[/SIZE]
[SIZE=2]icedtea6 version 1.8 and above has been known to crash midori. If this is the case for you, try sun-jre."
[/SIZE]http://midori-browser.org/faqs/
[/FONT][/COLOR]
found this^ on their faqs, but I don't know what it means

I typed this (I think it's a update for midori) and don't get that error screen anymore; but now it just won't load the "activate java" warning

sudo apt-add-repository ppa:midori/ppa && sudo apt-get update -qq && sudo apt-get install midori

---

