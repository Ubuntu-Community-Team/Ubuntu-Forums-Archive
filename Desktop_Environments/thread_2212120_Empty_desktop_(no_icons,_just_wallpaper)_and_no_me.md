---
title: "Empty desktop (no icons, just wallpaper) and no menu bar"
date: 2014-03-19
forum: Desktop Environments
---

### Post by carlos40 on 2014-03-19
Greetings, buddies

I've made some search at the Google and at the Ubuntu forums, so unless my Search Fu has failed me, I found nothing about my problem.

**PROBLEM**: After upgrading Lubuntu from 12.04 to 13.10, there's an empty desktop (no icons, no menu bar and a different right-click menu) with just the standard Lubuntu's wallpaper at the background. I made a fresh new installation of Lubuntu 14.02 using USB Live (with /home in a separated partition as recommended), but the problem persists.

[[IMG]http://s29.postimg.org/wiktt4kkj/2014_03_18_174830_1024x600_scrot.jpg[/IMG]]("http://postimg.org/image/wiktt4kkj/")  [[IMG]http://s30.postimg.org/y2bew19bh/menu.jpg[/IMG]]("http://postimg.org/image/y2bew19bh/")

(The first image image is a screenshot; the second one is a photo using my cell phone because the right-click menu wasn't showing in the screenshots)

**BACKGROUND:** I was using Lubuntu 12.04 and recently I realized my Lubuntu just stoped to auto-updating and, worse, he somehow refused to realize that there were new updates (and even new Lubuntu versions!) avaliable. After a lot of google search and hours of struggling with the OS, I finally made my way to 12.10. I was happy because everything worked fine. I know that Ubuntu doesn't make "Upgrade Jumps", so my original plan was to spending sometime updating 12.04->12.10->13.04->13.10. When I restarted the Netbook to try to update to the 12.10 to 13.04, for my total surprise the Update Manager offered me an update **straight to 13.10**!! Well... so I did and the problem mentioned above started. I even tried to make a *totally fresh new* instalation using the new, still beta Lubuntu 14.04, formating the root partition while keeping /home safer in another partition. Nothing has changed.

The menu bar only appears if I log in as "Lubuntu Netbook". But I want to use "Lubuntu" instead.

I have no idea of what to do. What can I do to solve this problem??

---

### Post by Rex Bouwense on 2014-03-19
Weird problem.  I have had no good experience trying to use the update tool.  I am 0 for 2 attempts.  However,  Lubuntu 12.04 and Lubuntu 13.04 have already reached their End Of Life.  Lubuntu 12.10 dies next month and 13.10 has about another six months.  I do know that skipping versions causes big time problems.  Since you have already opted to install the beta 14.04 Daily Build it sounds like you might have got a bad download or a bad burn.  Did you check the MD5Sum of the downloaded image?  Did you burn the image at the lowest speed possible?  Also make sure that you are booting Lubuntu and not Lubuntu Notebook or Open Box because you can boot into the others at Log in.  The little icon on the upper right part of the screen allows you to do this.  One other question, did you try 14.04 before you tried to install and did everything work?  If you have the CD or flash drive handy boot from it and see.

---

### Post by carlos40 on 2014-03-19
> **Rex Bouwense said:**
> Did you check the MD5Sum of the downloaded image?

Now that you said that, I didn't check. I forgot to do that.

I checked now and guess what? The MD5SUM **didn't match**.

That brought me hope. I donwloaded it, checked the MD5SUM (and this time it does match!), made the USB Live and a new installation (formating root partition and leaving /home safe in another partition). Restarted...

...and the problem persists. ](*,)

By the way, I must to remember that this problem started *not with the 14.04 new instalation*, but with the Update Manager updating from 12.10 to 13.10!! The problem came before 14.04 (and it was expected that the new instalation would fix the problem, which didn't happened).

> **Rex Bouwense said:**
> Did you burn the image at the lowest speed possible?

As mentioned before, I used a USB Live using Startup Disk Creator from Lubuntu.

> **Rex Bouwense said:**
> Also make sure that you are booting Lubuntu and not Lubuntu Notebook or Open Box because you can boot into the others at Log in.

I know. As said previously, this problem happens only at "Lubuntu". "Lubuntu Netbook" shows the menu bar normally, but I want to use the former option.

> **Rex Bouwense said:**
> One other question, did you try 14.04 before you tried to install and did everything work?

Yes. I tried twice. And this problem wasn't there. Everything just works fine when I try it, but after instalation, the problem is present.

I don't know what to do. I really enjoy this distro. Anyone has any ideia about what can I do to fix it?

---

### Post by jwest68 on 2014-04-18
I just managed to do the same thing to my Lubuntu 14.04 (no desktop, menu, etc.). My quick fix for that is to remove/rename the ~/.config/lxsession/Lubuntu/desktop.conf file.

---

### Post by frank18 on 2014-04-18
> **carlos40 said:**
> Now that you said that, I didn't check. I forgot to do that.

I checked now and guess what? The MD5SUM **didn't match**.

That brought me hope. I donwloaded it, checked the MD5SUM (and this time it does match!), made the USB Live and a new installation (formating root partition and leaving /home safe in another partition). Restarted...

...and the problem persists. ](*,)

By the way, I must to remember that this problem started *not with the 14.04 new instalation*, but with the Update Manager updating from 12.10 to 13.10!! The problem came before 14.04 (and it was expected that the new instalation would fix the problem, which didn't happened).



As mentioned before, I used a USB Live using Startup Disk Creator from Lubuntu.



I know. As said previously, this problem happens only at "Lubuntu". "Lubuntu Netbook" shows the menu bar normally, but I want to use the former option.



Yes. I tried twice. And this problem wasn't there. Everything just works fine when I try it, but after instalation, the problem is present.

I don't know what to do. I really enjoy this distro. Anyone has any ideia about what can I do to fix it?

check if have additional drivers to be installed.

---

### Post by kim-kulak on 2014-04-20
Yes, yes, yes. Had an absolutely black screen after upgrade from 12.04 to 14.04. Ctrl + Alt + T would bring up a terminal. No errors in any of the error logs. Renamed the above desktop.conf file and rebooted. Success! Thank you.

---

### Post by Isabeldelalama on 2014-09-09
[B]I just managed to do the same thing to my Lubuntu 14.04 (no desktop, menu, etc.). My quick fix for that is to remove/rename the ~/.config/lxsession/Lubuntu/desktop.conf file.
[/B]

This solution works for me. Thanks!

---

