---
title: "Couple of Problems"
date: 2009-03-10
forum: General Help
---

### Post by xHalloweenx on 2009-03-10
I just recently installed ubuntu 8.10 inside windows.

Whenever i boot instead of seeing a splash I see a shell, and I have to wait about 50-60secounds and type exit and enter

I cannot View the whole Shell I can only view about half of it (y-axis).

After I boot up I can hear the Drums
Once I Login the kernal or system locks up or freezes.
I am able to move the mouse but keyboard does not respond.
I can boot into the bottom failsafe session

Specifications
--------------
CPU:  	Intel® Celeron® 2.50GHz Processor
128KB L2 cache & 400MHz FSB
Chipset: 	Intel® 845GV chipset
Memory: 	1.25 GB DDR
Hard Drive: 	40GB HDD
Optical Drive: 	48x Max. CD-RW Drive; 3.5" 1.44MB FDD
Video: 	Intel® Extreme Graphics 3D
Sound: 	AC '97 Audio
Ports/Other: 	6 USB 2.0 ports, 1 Serial, 1 Parallel, 2 PS/2, Audio-In & Out

Monitor
-------
Resolution: 1152x864


Any help would be great appreciate.

Thanks for your time and patience,
 - xHalloweenx

---

### Post by Defrector on 2009-03-10
When you say "inside windows" do you mean you used the windows-based installer to install ubuntu?

---

### Post by Svensk023 on 2009-03-10
im assuming that you used wubi to install Ubuntu inside of windows.
I have always had bad luck when doing that on peoples computers that want to try out linux be4 partitioning.
wubi definitley needs alot of improvement.

---

### Post by avtolle on 2009-03-10
As to the first issue, see [http://www.ubuntu.com/getubuntu/releasenotes/810#Boot%20failures%20on%20systems%20with%20Intel%20D945%20motherboards](http://www.ubuntu.com/getubuntu/releasenotes/810#Boot%20failures%20on%20systems%20with%20Intel%20D945%20motherboards)

---

### Post by xHalloweenx on 2009-03-10
well i wouldnt say that necesarily but somewhat.

On the ISO I selected Install inside windows.

---

### Post by avtolle on 2009-03-10
> **Svensk023 said:**
> im assuming that you used wubi to install Ubuntu inside of windows.
I have always had bad luck when doing that on peoples computers that want to try out linux be4 partitioning.
wubi definitley needs alot of improvement.
In my (admittedly limited to only 10 installs) experience with Wubi, there haven't been any problems specific to Wubi itself. There have been issues with badly fragmented HDDs, but after running into that once or twice, learned to defrag before installing; there have been a few problems resulting from a corrupted file system due to hard shutdowns, and running chkdsk -r has taken care of that. Other issues, such as those posted initially, seem common to Ubuntu installs on certain hardware whether installed using Wubi or Ubuntu on its own partition in a more traditional manner.

That said, Wubi represents a nice way to let a user try Ubuntu out; however, the Wubi guide should be consulted, IMO, before installing that way to learn about any problems that may exist, and certain issues like hibernation not available on a Wubi install, and (prior to Wubi 8.10, according to the guide) installation on RAID set-ups were not supported.

And, yes, once Ubuntu is "tried out" with a Wubi install, the user really should do a traditional installation of Ubuntu on a separate partition. Again, IMO.

---

### Post by avtolle on 2009-03-10
On issue number two, I think you are running into [http://www.ubuntu.com/getubuntu/releasenotes/810#Hangs%20with%20desktop%20effects%20on%20Intel%20830MG%20and%20845G%20video%20cards](http://www.ubuntu.com/getubuntu/releasenotes/810#Hangs%20with%20desktop%20effects%20on%20Intel%20830MG%20and%20845G%20video%20cards) with the solution being to disable Visual Effects. As I'm fairly certain you didn't install using Safe Graphics mode, and you can boot in failsafe mode, once to the desktop, you need to disable Visual Effects under SystemPreferences>Appearance and click on the Visual Effects tab, select none. This may be a situation where you will want to have the "last session" remembered on exit, to retain the disabling of visual effects. 

Not sure, but there may be a better/newer driver available for your graphics chips; you would need to do a search on this. There may also be something that can be edited into the /etc/X11/xorg.conf file to get around the problem; again, a search would be needed. Good luck.

---

### Post by xHalloweenx on 2009-03-10
I originaly did a complete install of the whole partition. I had the same problem there as posted above, since that happend I installed windows xp and did the install inside windows thing.( I only have 1 pc and needed more information )
After I get everything running normal for ubuntu I will do a full install over the partition, and do what needs done

@avtolle
I cant even get to my desktop before it locks up or freezes.
the only thing i can successfully get to is the shell`s
During Bootup, at login - ctrl+alt+f1, and the failsafe.
failsafe being the only 1 I can view all of since its in a small square box.

---

### Post by avtolle on 2009-03-10
Sorry; had a brain cramp. What you need to do is, from the command line, disable or remove compiz. There are many threads on the subject scattered around the forum with instructions on how to do this. I don't have your chipset, and as I don't want or need compiz, I'm aware that it is a problem for some, and that there are threads dealing with how to remove/disable it to overcome your graphics problem. Perhaps a Google search along the lines of remove compiz Ubuntu 8.10 will get you going.

---

### Post by avtolle on 2009-03-10
Take a look at [http://www.sriraminhell.com/2008/11/problems-with-ubuntu-810-intrepid-ibex.html](http://www.sriraminhell.com/2008/11/problems-with-ubuntu-810-intrepid-ibex.html)

---

### Post by xHalloweenx on 2009-03-10
I have successfully loged in now
Thanks for your help avtolle.

---

