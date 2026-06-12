---
title: "Which things can I disable on my computer to conserve resources? And how?"
date: 2009-01-27
forum: General Help
---

### Post by freedomisgood on 2009-01-27
Hi. I have within the last couple months ditched my windows xp off both my laptops. I'm all Ubuntu now. I'm trying to learn how to conserve resources as well as how to add some. Any help would be appreciated. I'd like to disable all unnecessary services that load during boot. That's first.
I also want to figure out if it's worth getting the 2 gig memory which my hp pavilion zv6000 is able to take. If it's a guarantee to speed things up that'll be a "yes" - thanks. Also, I have two partitions on the hp but on the other laptop I installed ubuntu in the primary partition. I thought it might make the computer work faster. I want to do that on the hp but I might have to run a program for the wireless verizon modem sometimes. I figured out how to dial the modem without vz access manager but there are these "updates" which happen and they probably don't happen with how I'm using the modem now.
Thanks if you can offer advice and help.

---

### Post by mb_webguy on 2009-01-27
Well, Ubuntu should already be fairly fast, though there are a few things you can try.

First, go to System->Preferences->Sessions.  Tracker indexes your files and allows fast searches of your file system.  If you want that functionality keep them, but since the indexing can slow down your computer some, if you don't think you'll use this functionality, you may want to uncheck Tracker and Tracker Applet.

Close that, and go to System->Preference->Appearance.  Under the Visual Effects tab, for better performance, make sure either Normal or None is selected.  Advanced gives you access to some very cool effects with Compiz, but at a noticeable hit in performance.  While we're here, if you have a LCD monitor, you may want to click the Font tab and make sure Subpixel Smoothing is selected under Rendering.  This won't increase performance, but it will make the text on your screen look a lot better.

If (and ONLY if) you have a multi-core processor, you can speed up boot time by making one small edit to a system configuration file.  In the terminal, enter the command "gksu gedit /etc/init.d/rc", and look for the line "CONCURRENCY=none".  Change this to "CONCURRENCY=shell", save, and close.

If you have at least 1GB of memory, you can comfortably lower your swappiness setting so that your system will be less likely to write to swap space unless memory is full (which will speed you up since memory is about 100 times faster than reading from the hard drive).  You can temporarily change the swappiness setting with the command "sudo sysctl -w vm.swappiness=nn", where nn is a value from 0 to 100.  The default is 60.  The lower the number, the less the system will tend to write to swap.  A value of 0 means that the system won't use swap space at all.  I'd try a value of 10 or 20, and when you find a value that seems to work for you, you can make it permanent by editing the sysctl.conf file with the command "gksu gedit /etc/sysctl.conf", and adding the line "vm.swappiness=nn" at the bottom, where nn is the value that works for you.

---

### Post by TenPlus1 on 2009-01-27
[http://www.zolved.com/synapse/view_content/28224/How_to_tune_your_Ubuntu_PC_for_faster_performance_](http://www.zolved.com/synapse/view_content/28224/How_to_tune_your_Ubuntu_PC_for_faster_performance_)

---

### Post by freedomisgood on 2009-01-29
Ok great. I'm going to order the extra memory on ebay before anything. My hp laptop has 512 mb and it looks like I can go up to 2 gig. Would you have any particular advice about the memory? I usually get a single module instead of the one split into two. Does that matter? My reasoning is ; should something happen to one slot on the board I still have the other slot to put the memory in. I was about to order the memory before posting but then I realized it doesn't hurt to ask advice first.

---

