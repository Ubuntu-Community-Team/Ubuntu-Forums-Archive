---
title: "Steam crashing when clicking on videos and screenshots"
date: 2013-05-23
forum: Gaming &amp; Leisure
---

### Post by saracen666 on 2013-05-23
Hi All,
        Hope you are well. I have recently installed steam and I have 2 problems.

When I go into a games videos and screenshots steam crashes as soon a s i click on a video or picture

I cannot close the steam client from the taskbar. I right click steam in the taskbar and click exit and nothing happens.

Please help.

---

### Post by efflandt on 2013-05-27
Which Ubuntu version (and is it 32 or 64-bit) are you running and what video card or chip do you have and default or other video drivers? No clue why you would have trouble with images. And not sure if Flash works automatically in 32-bit. Because Steam is 32-bit, for 64-bit Ubuntu I originally had to **mkdir ~/.local/share/Steam/ubuntu12_32/plugins** and put 32-bit **libflashplayer.so** in that for Flash to work in Steam. Although, without that Steam did not crash, it just said I was missing a plugin and provided instructions that did not work in Linux.

What desktop are you running (Unity?)? As far as exiting Steam, I always just use **Steam** > **Exit** from its own menus at the top (if you were just playing a game sometimes it has to finish syncing with the Steam Cloud).

I have been using Steam in 64-bit Ubuntu 12.04 w/nvidia drivers since late Linux beta in January before it was released, mostly for Team Fortress 2, but I also bought Half-Life and Counterstrike when they were on sale.If you install Steam on another system, your games and stats should  automatically be there (after they download). I did that temporarily in  Win7 (which never had Steam before) when the far end of my drive with Linux started failing, until I got  everything transferred to a new drive.

---

### Post by saracen666 on 2013-05-29
Hi,
    Thanks for the reply. I have


Ubuntu 12.04 64-bit
MSI Twin Frozr Radeon HD7850
I have the binary driver which shows as "ATI Fire GL"

I am using unity desktop yes.

Any ideas from info above?

---

### Post by oldrocker99 on 2013-05-29
Unity and games don't always get along too well.

Try this:

sudo apt-get install lubuntu-desktop

Then log out and select "Lubuntu Desktop" f  drop-down menu and log in again. LXDE (Lubuntu) is a lot lighter-weight than Unity, and should make Steam behave a little better. It also has a quick-to-pick-up interface.

---

### Post by Perfect Storm on 2013-05-29
> **saracen666 said:**
> Hi All,
        Hope you are well. I have recently installed steam and I have 2 problems.

When I go into a games videos and screenshots steam crashes as soon a s i click on a video or picture

I cannot close the steam client from the taskbar. I right click steam in the taskbar and click exit and nothing happens.

Please help.

Try what efflandt suggested regarding flash. Steam tend to crash on 64-bit if it can't find flash, even if you don't trying to watch the videos. There's a guide here you can follow to do this; [http://www.webupd8.org/2013/01/how-to-get-flash-player-to-work-with.html](http://www.webupd8.org/2013/01/how-to-get-flash-player-to-work-with.html)

---

### Post by uaebuntu on 2013-05-30
> **oldrocker99 said:**
> Unity and games don't always get along too well.

Try this:

sudo apt-get install lubuntu-desktop

Then log out and select "Lubuntu Desktop" f  drop-down menu and log in again. LXDE (Lubuntu) is a lot lighter-weight than Unity, and should make Steam behave a little better. It also has a quick-to-pick-up interface.

I'm on Ubuntu 13.04 64 bit with i7 CPU and lots of RAM, I loaded 32 bit Flash and STEAM still crashes, thought I'd try Lubuntu so I did as suggested but cannot find a dropdown menu, when I restart I get the Lubuntu flash screen and then it boots to unity as before

---

