---
title: "awn manager doesn't start"
date: 2009-10-30
forum: Desktop Environments
---

### Post by Smooke on 2009-10-30
Hello,

i just have installed AWN and cannot open manager...The bar?/dock appears (as it should), but cannot open "dock preferences"..Tried everything...Nothing hapens. When tryin' start manager through the terminal got message something like that (translation from other language):

[COLOR=Red]expected "int", received "float" for key /apps/avant-window-navigator/bar/bar_angle
[/COLOR]
any ideas?

plsss help

regards
s

---

### Post by KlinerDraken on 2009-10-30
the error sounds like you have a "float" value in your bar_angle settings

    press alt-F2 type gconf-editor hit {enter}

    in the left pane navigate to /apps/avant-window-navigator/bar

    look at the value that is set in bar_angle and see if it is a "float" value (ie. 1.25) instead of a int(integer) value (ie. 1)

    if it is a float value remove the decimal portion including the "." so if it is 0.1234 you would make it 0

Note: this is a setting for the angle of the bar (of course) numbers can be set to any whole number from 0 to 90. 0 being horizontal 90 being vertical. If you want just set the value to 0 and it will be horizontal.  


hope that makes sense and helps ;)

---

### Post by Smooke on 2009-10-31
Hello,

this is really strange...Checked gconf-editor and the valuey of the key is proper - was set to 45, changed to 0. Didn't help. The problem is with preferences, not with bar. The bar is OK, but preferences doesn't start. Can't change any settings, can't add any applet...Still when tryin' to start manager/preferences through the terminal i get message, which correspond to bar problems, not manager...I'm confused...

---

### Post by KlinerDraken on 2009-11-04
maybe you can uninstall then reinstall it to see if that helps

sudo apt-get remove awn-manager --purge
sudo apt-get install awn-manager

---

### Post by gamdang on 2009-11-05
When I went to edit bar_angle 'Type' was set to "float", but it was grayed out so I didn't even notice the first time. 
Once I unset the key it changed to "integer" by itself and the manager launched without any trouble.

I hope that helps.

---

### Post by Smooke on 2009-11-06
ok. i'll check it out in few days and give You guys answer...The computer is not mine, but my father's.
 
greetings
sz

---

### Post by Harold.Gcia on 2009-11-08
> **KlinerDraken said:**
> the error sounds like you have a "float" value in your bar_angle settings

    press alt-F2 type gconf-editor hit {enter}

    in the left pane navigate to /apps/avant-window-navigator/bar

    look at the value that is set in bar_angle and see if it is a "float" value (ie. 1.25) instead of a int(integer) value (ie. 1)

    if it is a float value remove the decimal portion including the "." so if it is 0.1234 you would make it 0

Note: this is a setting for the angle of the bar (of course) numbers can be set to any whole number from 0 to 90. 0 being horizontal 90 being vertical. If you want just set the value to 0 and it will be horizontal.  


hope that makes sense and helps ;)
I have the same problem. I did what you said but it's still not working. I changed the value to 0, but its still saying "float" instead of "integer". is there something else that can be done.

---

### Post by Harold.Gcia on 2009-11-09
Oh I'm such a newb, I fixed the problem. I didn't read the part where you have to unset the key. I actually did it by mistake. AWN Manager is working now, Thanks.

---

### Post by Mikegledholt on 2009-11-11
I'm a newb to Linux but am learning fast. My AWN Manager will open up but only as a multipixelated window. I can't do anything with it. I think it might be connect to a compiz problem that I seem to have. Yesterday I opened compiz and I got the same multipixelated window only this was the whole screen and the only way to remove it was a complete new install - a bit drastic I know but that's all that worked.

Has anyone any ideas please.

Ubuntu 9.10

Thanks
Mike

---

### Post by Dunti21 on 2009-11-29
> **KlinerDraken said:**
> maybe you can uninstall then reinstall it to see if that helps

sudo apt-get remove awn-manager --purge
sudo apt-get install awn-manager

Hi, I tried to reinstall awn manager but still nothing happens when I click on it. Or when I click "dock preferences". If I go to awn manager through the application launcher it shows awn manager in my bar above that shows what's open, but after a while it just disappears

---

### Post by absurdus_delirium on 2009-12-06
Had the same problem - got the same message about a mismatch between awn-manager expecting and integer and getting float.
I m just posting to clarify in case anybody else needs help figuring out how to change the key value type from "float" to "integer" because if you try to change the type in gconf-editor for value bar_angle you find that you cannot. You just have to create a new one -  right-click, New Key..., bar_angle, type integer and it replaces the old one. Your problem should be solved!

Noobs unite! :popcorn:

---

### Post by drascus on 2009-12-06
thanks for this post this problem was driving me nuts!! got it working now!

---

### Post by gkh73 on 2009-12-07
Brilliant guys!  This fix worked for me as well!   I'm surprised they haven't come out with a fix for this yet as an update package.  Of course if you're not a noob like me you probably already know how to fix the problem!   :)

---

### Post by absolut1983 on 2010-01-12
It has just worked for me.

Thanks a lot.

---

### Post by RazorV on 2010-02-04
this is a great "how to" post.  Thanks to all that replied.

I just changed the value in gconf-editor for the awn bar angle to 0 and then right clicked on it and selected UNSET key and it worked great!

cheers to all

---

### Post by Raer1192 on 2010-03-30
for the people who's awn-manager or "dock preferences didn't show up you could 
do alt+f2 then type   gconf-editor hit enter and then /apps/avan-window-navigator and then instead of bar go to window_manager then click show_all_windows right click edit key and where it says value change it from false to true and ur awn-manager "dock preferences" should show up..it worked for me :D

---

