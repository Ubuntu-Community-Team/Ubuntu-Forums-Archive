---
title: "Updates failing, partial upgrade forced, can't authenticate some packages"
date: 2008-12-10
forum: General Help
---

### Post by ubnewbie2 on 2008-12-10
On 8.10 here, and everything has been great until last night.

It tells me 20 updates are available, but when update manager starts, it pops up a window saying "Not all updates can be installed" and offers/suggests a "Partial Upgrade".  I click on that and it starts, then fairly quickly it reports that some packages cannot be authenticated (the list is mostly open office stuff).

So I try again, and this time I hit close, instead of the offered "Partial Upgrade" choice.  This gets me back to the Update Manager and I click on "Install Updates".  This seems to work, then it pops up the whole "Partial Upgrade" thing again. Now I just have the open office stuff, greyed out, and the "Install Updates" button is disabled.  Seems I am stuck with this list of Open Office stuff that it can't handle.  What to do?

---

### Post by em4r1z on 2008-12-10
Try a different repository (System > Administration > Software Sources) and update again.

---

### Post by ubnewbie2 on 2008-12-10
I switched from the "australian" server to the "Main" server, and got the same problem

(please excuse the double post)

---

### Post by ubnewbie2 on 2008-12-10
> **em4r1z said:**
> Try a different repository (System > Administration > Software Sources) and update again.

I switched from the "australian" server to the "Main" server, and got the same problem

---

### Post by pixideps on 2008-12-10
I have the same problem but croatian repository. So ... where is the problem I do not know!

---

### Post by pixideps on 2008-12-10
Ok!! I've found a kind of solution.
in console type: 
sudo apt-get dist-upgrade 
quite obvious and "old fashioned" but seems it works
Though it reported some errors during installation (meaning that it cannot find some dependencies and stuff) it seems that everything works fine now. It upgraded office to 3.0.

---

### Post by pixideps on 2008-12-10
Ok!! I've found a kind of solution.
in console type: 
sudo apt-get dist-upgrade 
quite obvious and "old fashioned" but seems it works
Though it reported some errors during installation (meaning that it cannot find some dependencies and stuff) it seems that everything works fine now. It upgraded office to 3.0.

---

### Post by frankleeee on 2008-12-10
I had upgraded to OO3 from the ppa launchpad site before it was closed due to bugs, and had no problems with the downloaded packages about 2 weeks ago. As of yesterday the packages were put back into the repos, but I read on another thread that there were bugs again so things may be up in the air. Although on two of my computers yesterday from the main server I got the updates and 4 more today all OO3 packages, but on a laptop that I had to reimage since the repos were closed I had the same problems your describing. So I purged all the OO on this laptop, and used this thread for a update with no problems, I had to add some extra stuff to get the help working and systray working. Caraboy's instruction are what I used to get OO3 installed on the laptop the clear command was the key for the install of the same OO3 packages on my other computers which updated yesterday.
[http://ubuntuforums.org/showthread.php?t=993516](http://ubuntuforums.org/showthread.php?t=993516)
If this works thank him, use at your own discretion.

---

### Post by ubnewbie2 on 2008-12-10
> **pixideps said:**
> Ok!! I've found a kind of solution.
in console type: 
sudo apt-get dist-upgrade 
quite obvious and "old fashioned" but seems it works
Though it reported some errors during installation (meaning that it cannot find some dependencies and stuff) it seems that everything works fine now. It upgraded office to 3.0.

Yes, it works, I think, because it allows the upgrade without verification (if you tell it to)

My system is now up to date, thank you.

---

### Post by ubnewbie2 on 2008-12-10
> **frankleeee said:**
> I had upgraded to OO3 from the ppa launchpad site before it was closed due to bugs, and had no problems with the downloaded packages about 2 weeks ago. As of yesterday the packages were put back into the repos, but I read on another thread that there were bugs again so things may be up in the air. Although on two of my computers yesterday from the main server I got the updates and 4 more today all OO3 packages, but on a laptop that I had to reimage since the repos were closed I had the same problems your describing. So I purged all the OO on this laptop, and used this thread for a update with no problems, I had to add some extra stuff to get the help working and systray working. Caraboy's instruction are what I used to get OO3 installed on the laptop the clear command was the key for the install of the same OO3 packages on my other computers which updated yesterday.
[http://ubuntuforums.org/showthread.php?t=993516](http://ubuntuforums.org/showthread.php?t=993516)
If this works thank him, use at your own discretion.


The upgrade from command line, as pixideps posted, seems to fix everything.

---

### Post by frankleeee on 2008-12-10
> **ubnewbie2 said:**
> The upgrade from command line, as pixideps posted, seems to fix everything.

That is great I had not tried the dist-upgrade, two of my computers updated fine but one was showing this partial upgrade, it was a little confusing.

---

