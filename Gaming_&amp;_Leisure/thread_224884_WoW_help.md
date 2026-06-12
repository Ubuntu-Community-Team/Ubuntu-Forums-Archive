---
title: "WoW help"
date: 2006-07-28
forum: Gaming &amp; Leisure
---

### Post by sodapopinski on 2006-07-28
Ok, I followed the guide here ([https://wiki.ubuntu.com/Wine?highlight=%28wine%29](https://wiki.ubuntu.com/Wine?highlight=%28wine%29)) and here ([https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)) and when I go to install WoW I after accepting the license agreement I get the following error: Unrecognized key "options". (AttributeParser::Parse)

Any ideas?

---

### Post by SishGupta on 2006-08-01
> **sodapopinski said:**
> Ok, I followed the guide here ([https://wiki.ubuntu.com/Wine?highlight=%28wine%29](https://wiki.ubuntu.com/Wine?highlight=%28wine%29)) and here ([https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)) and when I go to install WoW I after accepting the license agreement I get the following error: Unrecognized key "options". (AttributeParser::Parse)

Any ideas?
It sucks that noone has answered you yet. But since I solved this myself I will tell you what I did.

I had this same problem. It isnt a wine/linux problem as i copied the cd files over to my windows comp and tried it. For some reason, putting the files on a HD from the CD isnt working like it is supposed to and you get that error message.

Heres what you should do:
1. Get the actual discs
2. run winecfg and add /media/cdrom to the drives section
3. put cd1 in, wait for it to mount (if you havent changed default settings,  you will know the disc is mounted when the folder displays or when the icon appears on your desktop)
4. Run the installer with wine by cd'ing to /media/cdrom and doing "wine installer" (or the appropirate command and file for you)
5. When it asks for cd2, just put it in in cd1's place, wait for it to mount like in step 3, and hit OK on the prompt.

You will also might to upgrade to wine 0.9.18, i am unaware if you need to use the wow patch on that though. I havent had time to test out my install past the login screen.

I hope this helps.

-Sish

ps. also check out [http://appdb.winehq.org/appview.php?iVersionId=5109&iTestingId=4958](http://appdb.winehq.org/appview.php?iVersionId=5109&iTestingId=4958)
It has a bit more comprehensive wow HOWTO

---

### Post by SishGupta on 2006-08-01
Also, make a windows/temp dir for patches or it tells you that you dont have enough space.

---

