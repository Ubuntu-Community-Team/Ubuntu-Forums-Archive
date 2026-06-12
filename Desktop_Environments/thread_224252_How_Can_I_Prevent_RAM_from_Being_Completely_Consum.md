---
title: "How Can I Prevent RAM from Being Completely Consumed?"
date: 2006-07-27
forum: Desktop Environments
---

### Post by vbgunz on 2006-07-27
I've ran Ubuntu for 30 days straight hardcore (15 apps average across 6 desktops) without a reboot. In my 10 years of Windows experience I've never seen such performance. Frigging incredible for sure and this leads me to my scenario and question.

The other day, I wanted to show my wife what Byzanz could do. Byzanz is a desktop recorder that can either record the whole desktop, a window, the mouse pointer or a selected area. it'll then save the recorded session into an animated gif you could share with others to show what you've done.

Anyhow, I showed my wife I can record the whole screen while she worked and as we giggled and laughed about it we forgot it was running... No, problem, not a slip while it ran *but* when we remembered about 3 minutes later and turned it off and saved the animated image to the desktop, Nautilus went off the hook and consumed all of my ram.

I was forced to hard boot the box *but* when it came back on, Nautilus again acted up and ate all my ram. I had to kill it again and again until I finally just deleted the image on the desktop and emptied the trash can.  Here is the burning question...

Q. how can I say, at least 200 MBs is to never be eaten up *except* by certain applications *only*? e.g. I don't want nothing to eat up all my ram and if in case an application tries to do this, the box will still be responsive enough to fire up the system monitor, or switch to a console so that I can at least with ease, kill the offending app?

I don't know if Ubuntu can do this *but* Linux is so perfect I really cannot see it *not* being able too... A few times, I've experimented with some regex and the same thing would happen... and other times, some small things would lead to big freezes that were due to the RAM being swallowed. 

Q. is there anyway to say, at least 200 MB is to be devoted to the keyboard, mouse, virtual desktops, system monitor, consoles and Force Quit? I hardly ever go above 800MB unless an app is taking the offensive. Is there anything I can do so to always remain in full control and never again see a system freeze due to no available ram?

---

### Post by Sef on 2006-07-27
How big is your swap?  You might want to increase it or make a swap partition if you don't have one.  A swap partition is for when the ram gets full use, so the computer won't stall out.  Normally a swap partition should be twice the ram, though if you have 1 gb memory you may could make it less than two gb.  It just depends on how much ram will you normally be using?  If you are doing videos and other memory instensive things. I would make a 2 gb swap file.

---

### Post by vbgunz on 2006-07-27
My swap is 1.8GB. I know about the swap file/disk *but* it appears useless once the RAM is completely consumed by a single application. My thought is, a single application consuming the RAM and virtually halting the box to a standstill and at times forcing a hard boot is unacceptable :(

My thought was it would be nice if I can somehow dedicate a portion of the ram to enough secondary applications *or* limit the ram consumption of an application if it exceeds a reasonable threshold. Some apps are intensive *but* no matter how intensive an application is, shouldn't there be a way to still have a responsive desktop?

I think it would just be nice if Nautilus didn't blow out my RAM and perhaps once it consumed about 600MB/50% something would intervene and say "nautilus appears real hungry, kill it, allow it, limit it? I just think it is pointless that Linux allows an application to bring the box to a halt. I also feel if I could at least have enough speed and memory to launch the system monitor or switch to console I could kill an offending app before it becomes to late.

This might be far fetched from any real world applications that can do this *but* I am writing in the interest of 'maybe one does exist'? If not, wouldn't this be a very smart addition into Ubuntu or perhaps even the Kernel?

if I we're a brand new user to Linux and a little tinkering around could make Nautilus a RAM/SWAP hog, well, reboot after reboot I would almost be completely convinced that my box was either compromised or that it had a virus and neither view of the situation would be the truth. This just isn't cool :(

I just think something has to *prevent* any one single app from completely halting a system. Maybe I am on to something? Is this possible? is there something out there to remedy such problems now? RAM/SWAP just don't cut it once an app goes off the deep end. Thanks for any feedback!

---

### Post by jgcamp99 on 2006-07-28
"saved the animated image to the desktop"

Have the program save the file elsewhere. By putting it on the desktop, it has to load everytime you boot as part of the user profile/desktop. I only save smaller files to the desktop and then only temporarily and move it elsewhere on the hdd in it's own folder, as a profile can take forever to load. If you use something like Citrix on a network, loading that not only takes a long time, but can corrupt your user profile when large files or several smaller files that accumulate are saved to the desktop.

Desktops should really be as clean as possible, and if necessary only have icon shortcuts for quick access. Basically you put a boulder the size of Gibralter on your desktop, instead of a paperweight. And the boulder crushed your system. 

Even internet downloads should be saved to another hdd location other than the desktop. Same reasons, having a 700 MB iso file on your desktop may be easier to find, but it takes up resources.

---

### Post by jgcamp99 on 2006-07-28
Another thing, all OS's need maintenance, Ubuntu has a feature that checks the filesystem every 30 boots. Yes, it's cool to set records with consecutive running days, but it really defeats the purpose of that filesystem check. There is no OS on the planet that is maintenance free. All of them like to be shut down from time to time and restarted. It flushes the memory.

1.8 GB Swap file ?, well, I have 1.5 GB of RAM. I've never used the 850 MB swap file. Even when the memory usage gets up there, since I have my Ubuntu user set to login automatically, just before I leave the computer, I have it restart if I want to clear the memory and am not in the middle of a project. You'd be surprised. Go eat, take a shower, check the US Postal mail, go to the bathroom or any number of other things, by the time you get back, the system has rebooted back into the desktop and you're ready to work again.

---

### Post by patrickthebold on 2006-07-28
jgcamp99  Could you explain the desktop thing further?  Does Ubuntu really do more then display an icon for a file saved to the desktop?  Why doe it load the files?

---

### Post by MWAAAHAAA on 2006-07-28
> **vbgunz said:**
> I've ran Ubuntu for 30 days straight hardcore (15 apps average across 6 desktops) without a reboot. In my 10 years of Windows experience I've never seen such performance. Frigging incredible for sure and this leads me to my scenario and question.

The other day, I wanted to show my wife what Byzanz could do. Byzanz is a desktop recorder that can either record the whole desktop, a window, the mouse pointer or a selected area. it'll then save the recorded session into an animated gif you could share with others to show what you've done.

Anyhow, I showed my wife I can record the whole screen while she worked and as we giggled and laughed about it we forgot it was running... No, problem, not a slip while it ran *but* when we remembered about 3 minutes later and turned it off and saved the animated image to the desktop, Nautilus went off the hook and consumed all of my ram.

I was forced to hard boot the box *but* when it came back on, Nautilus again acted up and ate all my ram. I had to kill it again and again until I finally just deleted the image on the desktop and emptied the trash can.  Here is the burning question...

Q. how can I say, at least 200 MBs is to never be eaten up *except* by certain applications *only*? e.g. I don't want nothing to eat up all my ram and if in case an application tries to do this, the box will still be responsive enough to fire up the system monitor, or switch to a console so that I can at least with ease, kill the offending app?

I don't know if Ubuntu can do this *but* Linux is so perfect I really cannot see it *not* being able too... A few times, I've experimented with some regex and the same thing would happen... and other times, some small things would lead to big freezes that were due to the RAM being swallowed. 

Q. is there anyway to say, at least 200 MB is to be devoted to the keyboard, mouse, virtual desktops, system monitor, consoles and Force Quit? I hardly ever go above 800MB unless an app is taking the offensive. Is there anything I can do so to always remain in full control and never again see a system freeze due to no available ram?

Sometimes my system decides to become almost totally unresponsive too. You can of course force a hard reboot in such a situation. What I do is go into the console (hit CTRL+ALT+F1 for example) and kill the offending app from there (killall -s KILL <application>). It can take ages before my computer decides to switch to console mode though, and than I still have to log in, which can take ages too. BUT you can kill the app without having to reboot.

I used to have a problem when writing large files to disk in the past after I switched from the 2.2 kernel to 2.4. Apparently the kernel folks decided to rewrite the IO system or so, because when I started to write lots of data to the disk, the system would just freeze. I solved the problem by using these 80pin IDE cables or whatever they're called. But the problem still persists somewhat. This might be the cause of your trouble as well. In that case you just have to wait until the write operation finished.

You might also want to read this article:
[http://sourcefrog.net/weblog/software/linux-kernel/swap.html](http://sourcefrog.net/weblog/software/linux-kernel/swap.html)

---

### Post by vbgunz on 2006-07-28
When I experimented in learning Regular Expressions, I would need the system monitor opened next to Kodos (a Python Regular Expression Toolkit) for when a deceivingly simple pattern turned green and went hulk on the system, I'd be able to see the rampage in the system monitor and have a few seconds to respond with a killer action...

If I didn't intercept it, the system would freeze and choke in just the first couple of seconds... if I didn't have the system monitor up, it would take nearly a minute to launch and by this time, a simple pattern is already painting the box red and the system monitor wouldn't be able to do it's job till a few minutes later or worse, it wouldn't do it's job at all. A reboot if not hard in this instance would've been a better bet for a quicker snap back to a livelier system:)

Situations like this with Nautilus and Regex and some other things that act up here and there wouldn't be so bad if when it happened, the box was smart enough to intercept and prevent it unless otherwise permitted. This might be a fairy tale job for Ubuntu or Linux *but* I would seriously love it if I can at least switch to console no matter how bad the ram/swap was getting on me... well, then again I am still a n00buntinite so I might be asking for something that is semantically or painfully impossible... I just thought I ask if anything can help prevent a app from going rogue :)

btw, I do use the desktop for shortcuts and small files. And if it is big, I usually save to the desktop because it usually means I am going to delete it. I'll try to watch that decision a little more closely from now on :)

---

