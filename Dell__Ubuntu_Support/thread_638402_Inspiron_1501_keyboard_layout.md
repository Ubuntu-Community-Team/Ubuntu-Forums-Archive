---
title: "Inspiron 1501 keyboard layout"
date: 2007-12-12
forum: Dell  Ubuntu Support
---

### Post by Sim777 on 2007-12-12
Does anyone know which one I should choose? In logs, I keep getting following error...

"Dec 11 09:21:03 sim-laptop kernel: [  290.483809] atkbd.c: Unknown key pressed (translated set 2, code 0x8d on isa0060/serio0)."

Dec 11 09:21:03 sim-laptop kernel: [  290.483815] atkbd.c: Use 'setkeycodes e00d <keycode>' to make it known. "

---

### Post by jayseye on 2007-12-20
Having the same problem, and am searching for a solution. So far, have found only one other mention of this issue, in an unanswered comment on [www.ubuntu1501.com](www.ubuntu1501.com) 
 
Just one small addition: first saw this happen after receiving a BIOS error on powerup, re the AC adapter being unrecognized. Solved that message by powering down, disconnecting and reconnecting all power cords. However, the keycode message has persisted since then. 

Will post a solution here when found; meanwhile am monitoring this thread in hopes that someone will find and post a fix before I do.

---

### Post by jayseye on 2007-12-20
The following thread seems to have the most promising solution, though it's yet to be confirmed under Gutsy: 
 
 [http://ubuntuforums.org/showpost.php?p=3987837&postcount=23](http://ubuntuforums.org/showpost.php?p=3987837&postcount=23)

---

### Post by Sim777 on 2007-12-28
Did it work? It seems that layout is missing / has wrong keys......

---

### Post by dbeltran on 2007-12-29
Its seems to be a BIOS problem with the dell inspiron 1501. I have updated the bios to the 2.6.3 Version and the problem was solved :).

Note: The first time when i have only restarted with the new bios, the problem was still there, Then i have completely turn off the computer, i have even unpluged the cord and the battery. Then i turned on and the problem was solved. I dont know but perhaps it&#347; something related to the energy state, like an event or something similar, I only know that the problem has disappeared! 

By the way, the solution published up didnt work for me in Gutsy. And the workaround based on setKeycode e00d 120 clears the log but the event is still there. You can easy check it out if you try to scroll any key and you will notice the scroll stop.Its due to the fact that the wrong event works like a key press,

This my first contributions to the ubuntu forum i hope not the last one :).

Thanks to the community.

---

### Post by Sparkypine on 2007-12-30
Same laptop model, same error rapid fire showing up in the event logs.  Seemed like it started showing up only after I installed VMWare Server (I'm not absolutely certain about this).  

Tried stopping the hotkey-setup service as suggested and nothing changed.  It's not a huge hit on my CPU but it seems troublesome.  I'm a Windows person trying to convert to Ubuntu so I have nothing else to offer other than my sympathy...

***after further review of the post above me, I just updated the bios a week or so ago when I had XP running.  I should be up to date with the newest version (I'll have to check if I have that particular version 2.6.3) so I wonder what else could have been triggered by the change.  

At least I know it's nothing like stuck key or something obtuse like that.

---

### Post by Sim777 on 2007-12-30
Newest update does stop log from being consta-spamed.  


But I still would like info about layout. When I run on batteries, I switch brightness to lower settings to conserve power....with current keyboard layout I cannot do that since FN + Up / Down does not work.

---

### Post by Sparkypine on 2008-01-06
The newest BIOS update does NOT stop the log from being spammed.  It was changing the keyboard layout to "Dell" that did it for me.

---

### Post by Sim777 on 2008-01-10
> **Sparkypine said:**
> The newest BIOS update does NOT stop the log from being spammed.  It was changing the keyboard layout to "Dell" that did it for me.

I have it set to "Generic 105-key (Intl) PC" and log is not being spammed.....

---

### Post by dbeltran on 2008-01-11
I really dont know, but for me the new Bios was necessary. I dont say its the only reason but it&#347; seem to be necessary.

I have the Generic 105-Key too and i have stop the spam.

---

### Post by Sim777 on 2008-05-27
I noticed that log is still being spammed, even after bios update and changing layout to closest one to Inspiron1501. 

laptop kernel: [ 5507.230569] atkbd.c: Use 'setkeycodes e055 <keycode>' to make it known.

---

### Post by Skretch on 2008-07-08
[B]This solution fixed the following problems:
[LIST=1]
[*]The battery and AC being unrecognized by the system.
[*]Unknown Key Pressed/Released all the time
[/LIST][/B]

Hello guys,

I have a Dell Inspiron 1501 laptop with both Ubuntu Hardy and Windows Vista installed on the hard drive.

I experienced the problem listed above on both Ubuntu and Windows OS's.
I used the solution posted by **[dbeltran]("http://ph.ubuntuforums.com/member.php?u=465049")** so give him credits if it works for you :)

[LIST=1]
[*]Make sure that you upgrade your BIOS to the latest possible version. You can download BIOS upgrades from the dell official website. I am currently using v2.6.2 but as far as I read there is a newer release - v2.6.3

[*]After applying the BIOS upgrade and making sure that you are still having the problem with the unknown key pressed all the time, Shut Down your laptop. Unplug the AC from the laptop and also unplug the AC from the electric switch. 

[*]Remove the battery from your laptop.

[*]Plug the AC back to the laptop (AC is NOT plugged into the electric switch - there is no electric power) while the battery is off then press and hold the Power button for 2-3 seconds do it 2-3 times. It cleans the leftover electricity.

[*]Unplug the AC once again and Press the Power button again and hold it for 2-3 seconds.

[*]Unplug the cable that connects the AC with the electric switch and plug it again.

[*]Wait for 5 minutes before putting the battery back and connecting the AC adapter with the laptop.

[*]After all is complete turn on your computer and post your results.
[/LIST]

[B]This solution fixed the following problems:
[LIST=1]
[*]The battery and AC being unrecognized by the system.
[*]Unknown Key Pressed/Released all the time
[/LIST][/B]

---

