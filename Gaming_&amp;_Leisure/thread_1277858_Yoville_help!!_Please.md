---
title: "Yoville help!! Please"
date: 2009-09-28
forum: Gaming &amp; Leisure
---

### Post by dbradt on 2009-09-28
I cannot get past 75% on loading player.   When I try to get in using a window computer it works.  Anyone have any have any ideas????  Thanks :confused:

---

### Post by oboedad55 on 2009-09-28
> **dbradt said:**
> I cannot get past 75% on loading player.   When I try to get in using a window computer it works.  Anyone have any have any ideas????  Thanks :confused:

Which player does it use? Is it the facebook doohickey?

---

### Post by dbradt on 2009-09-28
It is through facebook.  I click on the yoville bookmark and cannot get past 75% of activating my player.

---

### Post by oboedad55 on 2009-09-28
> **dbradt said:**
> It is through facebook.  I click on the yoville bookmark and cannot get past 75% of activating my player.

It looks like a flash app. How did you install flash?

---

### Post by dbradt on 2009-09-28
I downloaded one from the Ubuntu site.

---

### Post by oboedad55 on 2009-09-28
> **dbradt said:**
> I downloaded one from the Ubuntu site.

Okay, uninstall the flash you have now then go to this site and follow the directions to get all of the multimedia extras you need:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by dbradt on 2009-09-28
Could the flash player be Sun Java plugin???

---

### Post by oboedad55 on 2009-09-28
> **dbradt said:**
> Could the flash player be Sun Java plugin???

No, that's the java plugin. Just follow the directions I gave you for medibuntu and that will install the plugins you need.

---

### Post by u235sentinel on 2009-09-29
> **oboedad55 said:**
> No, that's the java plugin. Just follow the directions I gave you for medibuntu and that will install the plugins you need.

I would check the version of flash for linux.  I had problems with most facebook apps with flash 10.  flash 9 seems to work best so far for me.

---

### Post by carolija on 2010-04-03
> **oboedad55 said:**
> Okay, uninstall the flash you have now then go to this site and follow the directions to get all of the multimedia extras you need:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Hi i have same problem and i installed i guess all from that link what you gave as but still have the same problem;/
Can you maybe help step by step coz im not sure exactly about linux ?

Thank you.

---

### Post by carolija on 2010-04-03
Picture ... and how to check which version i have right now after all I did ?

Regards,

---

### Post by carolija on 2010-04-08
Anyone ? ;/

---

### Post by carolija on 2010-04-08
I guess no one except report :(

---

### Post by sigurnjak on 2010-04-09
Hi there , i hope  i am not to late ! 

[http://ubuntuforums.org/showthread.php?t=980342](http://ubuntuforums.org/showthread.php?t=980342)

Follow this tread , it works for me ! 

Nazdravlje !( regarding your RAKIA avatar )

---

### Post by carolija on 2010-04-11
> **sigurnjak said:**
> Hi there , i hope  i am not to late ! 

[http://ubuntuforums.org/showthread.php?t=980342](http://ubuntuforums.org/showthread.php?t=980342)

Follow this tread , it works for me ! 

Nazdravlje !( regarding your RAKIA avatar )

lol no you r not late:)

Tnx for tip ill take a look now, nazdravlje :)

---

### Post by carolija on 2010-04-11
Hi,

Damn i tried and tried but have no luck coz of this > Error: Breaks exisiting package 'flashplugin-installer' conflict: flashplugin-nonfree (< 10.0.22.87ubuntu2~)
i tried this one but wont work say i dont have it lol > nani@jebe-kevu-ovaj-PC:/etc$ sudo apt-get remove flashplugin-nonfree
[sudo] password for nani:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package flashplugin-nonfree is not installed, so not removed
The following packages were automatically installed and are no longer required:
  mobile-broadband-provider-info
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
nani@jebe-kevu-ovaj-PC:

So any ideas please ?

For sigurnjak msg: vidim da si ti vec imao 10-ku ali kazhe da je nema kao shto vidish + sam kliknuo na SVAKI "Disable" kod plugins na firefox-u.

Pozdrav,

And yea i Disabled all plugins in firefox.

Regards,

---

### Post by carolija on 2010-04-11
> ou need Adobe Flash Player 9 to play YoVille.

If YoVille does not load, please install Adobe Flash Player 9 by clicking here, then come back to this page and try again. Thanks!
		
>>Check out your YoVille.com Profile<<
Home Page | Room Contests | Forums


Damn i installed flashplugin-nonfreebeta & nothing ;/

---

### Post by carolija on 2010-04-11
lol hi again ;/

Yoville wont fork with Seamonkey ether ...

---

### Post by u235sentinel on 2010-04-12
> **carolija said:**
> lol hi again ;/

Yoville wont fork with Seamonkey ether ...

I've noticed several fb flash games such as yoville don't work because of flash 10.  Flash9 however seems to work just fine.  I didn't see any reference to the version of flash you are running.  perhaps trying flash 9 will do the trick (presuming you aren't already).

---

### Post by Xyldor on 2010-05-15
Hi, I have had this problem for over a year now. It is because flash 10 does not work properly for linux. My solution up until now was to run firefox (windows version) under wine. This worked until I recently updated ubuntu. Now it still works but freezes regularly. Anyone any thoughts on why this is so.

---

### Post by JayPeeJay on 2010-05-28
Yeah, I had same problem, it's because of Flash 10.

Flash version 10.1 beta is out and Yoville works great with it.

No deb package yet, download the tar and extract the libflashplayer.so to your /usr/lib/adobe-flashplugin folder (use sudo in terminal to get permission to do so).

This is better than going back to Flash 9 because everything else that needs 10 should work and won't if you revert backwards.

---

