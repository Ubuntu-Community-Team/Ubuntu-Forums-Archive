---
title: "Complete reinstall?"
date: 2008-06-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Scornic on 2008-06-17
I have a Dell Latitude D630, with a dual boot of Windows XP and Ubuntu. I use windows mainly, and so I often log onto ubuntu with mounds of updates to install. Well, the last mound of updates was about a week ago. There was a difference though. Three items related to gnome could not be installed. It gave me some 404 error related to an IP address. I am posting this from windows, and at the time I couldn't copy and paste it for some reason, so I'm not sure what the exact error was. Well, I thought nothing of it, and figured the updates probably weren't important. But I started getting gray screens of death.

I would be randomly working in linux, then I couldn't interact with anything. I could move my mouse, but that was it. (At this point, ctrl-alt-backspace doesn't work). Then the mouse freezes, and my graphics go way down, with lots of purple pixels. then it goes to the gray screen, and I have to remove the battery or hold onto the power button to turn it off. This at first was rare, but it got worse. I decided I would search for why these updates weren't installing (since gnome is the graphics related program) when I got another gray screen. This time, when I restarted, the dual boot screen was all messed up. I knew which one was linux and tried booting anyway, but the ubuntu loading screen had tons of green lines and blocks. I turned off the computer again, and this time when I tried to turn it on, it was immediate gray screen. Up until this point windows had worked flawlessly, but now I couldn't even get as far as booting windows.

After about a hundred restarts, I tried just turning it on and letting it sit there for a while (knowing it would boot itself into ubuntu normally) and when I came back, I typed in my username pressed enter, typed in my password and pressed enter, then I heard the gears in my computer turning. I assume this means I could still boot, but the graphics were just not working. I held the power button down to turn it off again, and when I went to try again only for windows, the graphics worked fine. I booted into windows, and am now writing this message.

I am sure that I will get a gray screen after some time in linux, so I want to be ready to do this in the fastest manner possible. I don't have any important files in linux, (Actually, it has become a clutter. I would like a clean slate) and I just want a completely fresh start. I don't know anything about partitioning, coding, or any hardware stuff. My friend installed linux for me. I just know that I have two partitions already.

How would I go about removing linux and reinstalling it? I do like linux, and despite my lack of coding knowledge, I am able to get around it, but I don't want to risk breaking my laptop if there is a graphics problem. I'm thinking a clean reinstall would fix whatever oddity is making the updates not work, and hopefully make everything fine. I don't care about losing files on linux. Anything I care about is also on windows.

One more small note: When linux is booted now, the top left corner of my laptop gets real hot, real fast. Within five minutes of booting linux, the air coming of of that vent can burn me. Windows does not do this. I don't know anything about laptop designs, but if that's where the graphics card is then I know there is some error in linux causing the card to overheat.

So, is there anyone that can walk me through a complete reinstall? I have another computer next to me that I can communicate with while I go through the process, and I can burn a linux download CD if need be. Please help me.

---

### Post by Scornic on 2008-06-17
Why doesn't anyone respond?

---

### Post by Scornic on 2008-06-18
I'm sorry, I thought ubuntu had good tech support. Could someone at least tell me how to remove ubuntu?

---

### Post by leemajors on 2008-06-18
> **Scornic said:**
> I'm sorry, I thought ubuntu had good tech support. Could someone at least tell me how to remove ubuntu?

Sorry noone has replied yet. Sometimes response is quick, sometimes its glacial. Haven't figured out why yet. 

Use your windows install to download the latest ubuntu installation disk and burn it to a CD. Make sure you're burning the image and not just burning the file to the disk. Check its right by inserting the disk back in once youre done, a window should pop up telling you how great ubuntu is. 

If that worked well, you've now got an ubuntu installation disk. 

Restart, and use your boot settings to boot up from the disk. 

From there its pretty straghtforward, follow the prompts to install ubuntu again. 

When the partitioned loads up, you just want to be careful to make sure the guided install isn't saying its going to use the whole disk, but it should be smart enough to detect the linux partition. After you've checked that, hit next a couple more times and let the installer do its thing!

Hope it works out for you :)

---

### Post by swordsmith on 2008-06-19
what leemajors said.

I've had similar situations happening to me sometimes, I have a Latitude D830. My problem was caused by my messing with resolution and dual monitors. After I installed the restricted nvidia driver, however, everything was fine.

What version of ubuntu are you using and have you installed all the needed graphics drivers?

---

### Post by chriscross93 on 2008-08-29
> **leemajors said:**
> Sorry noone has replied yet. Sometimes response is quick, sometimes its glacial. Haven't figured out why yet. 

Use your windows install to download the latest ubuntu installation disk and burn it to a CD. Make sure you're burning the image and not just burning the file to the disk. Check its right by inserting the disk back in once youre done, a window should pop up telling you how great ubuntu is. 

If that worked well, you've now got an ubuntu installation disk. 

Restart, and use your boot settings to boot up from the disk. 

From there its pretty straghtforward, follow the prompts to install ubuntu again. 

When the partitioned loads up, you just want to be careful to make sure the guided install isn't saying its going to use the whole disk, but it should be smart enough to detect the linux partition. After you've checked that, hit next a couple more times and let the installer do its thing!

Hope it works out for you :)

Agree.

---

