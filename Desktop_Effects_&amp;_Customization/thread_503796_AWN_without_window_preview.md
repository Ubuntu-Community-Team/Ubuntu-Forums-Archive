---
title: "AWN without window preview"
date: 2007-07-18
forum: Desktop Effects &amp; Customization
---

### Post by akshayas1986 on 2007-07-18
Hi people,
I have a small issue.. I have been using Beryl with AWN and avant seems to be releasing an update almost everyday. With the previous versions of Avant Window Navigator (AWN), a mouse over gave a window thumbnail preview of the open windows. It still happens with "Windows list" which can be added to the top bar in Ubuntu. But the point of using AWN is to eliminate the dull looking window bar. But with the AWN after updates, I am not able to see any window preview though it is enabled on Beryl and its working with "Windows list"

Thanks

Akshaya Srivatsa

---

### Post by hyperair on 2007-07-18
You have a point. I never noticed it missing though.. ><

I'm using Compiz Fusion and experience the same problem.

---

### Post by PaulieWalnuts on 2007-07-20
I have the same prob with Beryl+ AWN :(
Some kind of fix would be greatly appreciated :)

---

### Post by Death_Sargent on 2007-08-08
same here compiz-fusion user myself and yeah i used to have previews with beryl and now i have none.

---

### Post by walkerk on 2007-08-08
> **Death_Sargent said:**
> same here compiz-fusion user myself and yeah i used to have previews with beryl and now i have none.

in ccsm (type ccsm in terminal) ensure that Window Previews (under Extras) is enabled..

Works for me

---

### Post by FuturePilot on 2007-08-08
I'm really missing the window previews.

---

### Post by kholsheimer on 2007-08-09
in ccsm the window preview plugin is enabled indeed, but still no window previews in awn...

---

### Post by andrewsomething on 2007-08-09
What version of AWN are you using? This issue should have been fixed a few revisions ago.

---

### Post by Death_Sargent on 2007-08-13
I am using the latest edition (ubuntu repo) i used to have previews but it would appear they disabled them in the update that organizez the functions as applets

---

### Post by hyperair on 2007-08-13
Which repository are you using? Last I checked avant-window-navigator did not exist in the Ubuntu repositories. Are you using Trevino's repository? Or Reacocard's repository? If you're using Reacocard's repository, then you have to use avant-window-navigator-svn or avant-window-navigator-bzr. If you're using Trevino's repository, you must switch to Reacocard's repository.

---

### Post by andrewsomething on 2007-08-13
Please uninstall and then follow the instructions here to reinstall: [http://ubuntuforums.org/showthread.php?t=385981](http://ubuntuforums.org/showthread.php?t=385981)

That should get you to the current version where this is fixed.

---

### Post by akshayas1986 on 2007-09-30
Guys
There is a bug with avant-window-navigator-svn

This has been fixed in avant-window-navigator-bzr

Try this
> sudo apt-get remove avant-window-navigator-svn
sudo apt-get install avant-window-navigator-bzr

Hope this helps. In fact BZR is much better than the SVN

---

### Post by kngcrntrd on 2007-09-30
Are you using the development version?  I think dev is more stable than the latest stable.  If that makes sense.

---

### Post by akshayas1986 on 2007-10-05
When downloading from repositories, you typically get the stable ones. So I am guessing I am using the stable one

---

### Post by hyperair on 2007-10-05
It depends which repository you get it from. The stable one is from Trevino's eyecandy repository, and the package is called "avant-window-navigator". The unstable one is from Reacocard's repository, and is called "avant-window-navigator-bzr". You should go for the bzr, as that's the most stable, IMO.

---

### Post by dmber on 2007-10-05
the unstable one is the most stable?  

i know nothing about programming....

---

### Post by hyperair on 2007-10-05
Well the stable version is very obsolete, and has quite a number of bugs. These bugs have been fixed in the newer versions, and since there has no stable released since then... the best to use is the unstable. Anyway reports have shown that the unstable seems to be more stable than the stable. I'm running unstable on my system, and I certainly don't notice any problems.

---

### Post by dmber on 2007-10-05
ha.

nice.  i'm running the bzr, so i'm good to go.

---

