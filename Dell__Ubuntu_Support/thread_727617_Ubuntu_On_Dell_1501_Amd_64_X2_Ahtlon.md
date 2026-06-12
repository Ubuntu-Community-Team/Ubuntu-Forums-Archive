---
title: "Ubuntu On Dell 1501 Amd 64 X2 Ahtlon"
date: 2008-03-17
forum: Dell  Ubuntu Support
---

### Post by BlayJabe on 2008-03-17
Hello Just Installed Ubuntu On My Dell Got It Working Finally Had A Little Trouble With The Wireless Now Working Thx....couple Things Left

1.cant Get Flash Working

2.cant See To Get The Best Settings For The Beryl Ubuntu Working And Just Wondering Of Any Other Advice For This System It Should Work Well But Just Not Sure How Well Its Supported

So Basically Can Anyone Give Me Some Advice How I Can Optimize All Of This I'running On An Amd 64 Athlon X2 With 2 Gig  Of Ram So I Should Be Good Just Would Like Some Feedback 

Thx

---

### Post by notquitemichael on 2008-03-18
well Compiz relies on the graphics card more than the processor, so i can tell you that it should work as long as you've got a good card.

a quick pit fall may be having an nvidia card and not using the restricted driver.

also, if you mean you can't configure them, you need to install ccsm:

sudo apt-get install ccsm

(which is the real configurator of compiz, which for some reason doesn't come installed with ubuntu automatically.)

then just run ccsm, (its should be in system-preferences-advance desktop settings.)

that'll give you access to configure each plug in, like the cube.

flash may be broken temporaryily (it was when i tried to install,) if macromedia updates. that should be fixed in a few days.

---

### Post by knowledge_is_power on 2008-03-18
Im writing this from a 1501, and let me tell you.
hard as shi- to get working 100%
i still dont have it going just right. I had a flash problem where after my first flash object, firefox/iceweasel/whatever would lock up and i would have to force quit.  Fixed that through dicking around with older flash versions, and im still not 100% sure how i did it.  there are like 3 places where the flashplugin resides, and I had to get rid of em all, and then reinstall manually an older version.
hibernate/suspend still will not work.  havent tried epicially hard to fix because I know its fairly hit and miss.
Got rid of BrdCOM 46xx driver and did sum NDIS wrapping to get better wireless range (it was at 3 bars maximum... right next to router)
Had very much trouble with stupid CISCOs stupid VPN software... ended up getting the network admin of our universities network to give me the access key so i could use gnomes network-manager
Usplash screen didnt come up.  fixed that through setting grub screen resultion to right size.
aaand right now im having videocard problems as it would appear direct rendering is not available.
Its a hard-knock life owning a dell.
good luck to you sir, and I wish you better luck than me.  maybe dell puts new h/w in these things now. :)

---

### Post by Koolgecko91 on 2008-03-18
Its not as bad as it seems. I have a 1501 and it takes alittle work but its not that bad. I the wireless most of the tim has 3 bars but Ive gotten 4. The screen res. change is like a 3 minute fix. And flash works fine. Go to ubuntu1501.com. Its EXTREMLY helpful and will walk you through all the little things you need to get Ubuntu running well.

---

### Post by knowledge_is_power on 2008-03-18
aye, that blog rocks.
the bootup problem i think is probably my fault for dicking around too much...
above poster is right... its not **that** bad...
just, cisco and ATI suck quite a bit.
also broadcom.
god.

---

