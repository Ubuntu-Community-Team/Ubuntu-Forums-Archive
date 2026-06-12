---
title: "3rd Party Theme Half Reverts to Default Theme"
date: 2012-08-07
forum: Desktop Environments
---

### Post by messiah5150 on 2012-08-07
Hi There;

So, I have read that some people have experienced this issue in 11.04 / 11.10.  I've also read that it could be compatibility with GTK 2 / 3?  SO...I'll just get to my little issue and see what comes about.

When I use a 3rd Party theme (Orta currently), from time to time when I work away, I'll notice that the theme half changes back to the default theme. I also use FS-Icons and they will change back as well when this happens.  I can't pin point the exact trigger for it as its pretty random.

I use: Ubuntu 12.04 with Ubuntu Tweak. I also have Compiz installed, My Unity and Advanced settings. I use only Ubuntu Tweak to change the theme and Icons. Nothing else.   Since I'm newish to Ubuntu (Started with 10.04) and haven't programmed anything since the Commodore 128 (When I was 8yrs old) I'm rusty.  So...any thoughts? Software conflict? Bug? User error? I'm open to it all.

Thanks a bunch!

Darryl

-Asus G74sx Core i7-2670QM, 16gbDDR3, Nvidia 560GTXM 3gb, 750gb 7200WD

---

### Post by mcduck on 2012-08-07
What do you mean by "half changes back to the default theme"? Do yo see aprts of the application nusing default theme and parts using Orta, or is it that some applications use default theme and some use Orta?

In the latter case that would likely be because the theme doesn't include support for both GTK2 and GTK3. GTK2 apps will only use GTK themes, and GTK3 apps only use GTK3 themes, and most liekly you have a mix of both app types installed so you need to use themes that include support for both...

---

### Post by messiah5150 on 2012-08-07
> **mcduck said:**
> What do you mean by "half changes back to the default theme"? Do yo see aprts of the application nusing default theme and parts using Orta, or is it that some applications use default theme and some use Orta?

In the latter case that would likely be because the theme doesn't include support for both GTK2 and GTK3. GTK2 apps will only use GTK themes, and GTK3 apps only use GTK3 themes, and most liekly you have a mix of both app types installed so you need to use themes that include support for both...

GTK Theme goes default, icons go default, windows, only half changes.  Panel changes, Panel indicators stay with the 3rd party theme / icons.

I've heard and read about the GTK issues...this theme uses GTK2 or GTK3 from what I understand... but would the version be an issue if there is such a thing? Both GKT2 and GKT3 folders exist in the .theme/orta folder.

D

---

