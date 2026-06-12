---
title: "CPU power is at 100% at idle - why?"
date: 2007-03-22
forum: Desktop Environments
---

### Post by jammodotnet on 2007-03-22
HELP!
:(

My computer has been consuming full CPU power at 100%.

For the past few days, the little 'star' update icon would appear in my top task bar? You know, the one signifying that there are Ubuntu updates that need installing?
Well, everytime I authorized installation, an error message would come up after everything 'should have' been installed. It always stated some 'get-apt' problems and that the 'repositories' were not available for Automatix - do I want to continue ignoring this update? or something to that effect.
So I always clicked IGNORE.

Yesterday, I launched Synaptic Package Manager, and decided that I would remove Automatix BEFORE I clicked the little 'star' update icon.
I begin the update progress and my little nephew ... arrrgh ... waltzez right in and presses the power button on my power strip, shutting down my PC - in the middle of a F!@#$%G update?!?!?!

So I'm steaming mad, shout a little bit, and reboot.
Since then my computer has been using an extraordinary amount of CPU for regular tasks.

For instance today, I awoke, turn PC on and login. Everything appears normal, I didn't launch anything, but slowly my Processor meter (I have the little icon/widget on my taskbar) hits 100%.
I right-click it, assuming that I could, and am presented with the System Monitor.
I locate the Process Name that has the highest percentage of CPU consumption, and End Process.
I should have been wise and wrote down the names of the two Process that I killed, but my CPU meter went down to a range between 0% and 20%.

I'm going to do a restart, and come back to this thread if my CPU is at 100% again.

:(

---

### Post by jammodotnet on 2007-03-22
okay, so i did a restart, and process powers are still at 100%.
here is a screen shot of my Processes:

[[IMG]http://img529.imageshack.us/img529/2682/22mar07629812000if8.png[/IMG]](http://imageshack.us)

would it be safe to kill the top 2 power hungry processes?
what are they for?

<<here is a larger screenshot in case you can not clearly read the process data above: [http://img265.imageshack.us/my.php?image=22mar07629812000yz1.png](http://img265.imageshack.us/my.php?image=22mar07629812000yz1.png) >>

---

### Post by GoldNugget on 2007-03-22
I had the same problem when my system was idle. CPU would shoot up to 100%, returning to normal when I touched the mouse.
I found the culprit to be Beagle indexing my files in the background. I killed the Beagle process in the System Monitor and the problem has not returned. Be sure to uncheck the box in Beagle preferences which tells it to index files automatically. I have not rebooted since then so I don't know if the process will return upon a reboot. 
Hope that helps

---

### Post by jammodotnet on 2007-03-22
thank you GoldNugget!
i think that solved it.

although i wont be able to tell until i restart, if so, ill let you know later.
:)

---

### Post by jammodotnet on 2007-03-24
:(
didnt last past my last reboot.

whatever those 2 processes are (gs & hpijs) they keep coming back after i choose to kill their process. as for Beagle, i uninstalled it via Synaptic.

my wife asked me, 'Is it slow cause it was hacked?' ... since i am not proficient enough with Linux in general, i told her i dont know?!
i have NOT installed anything new in the past few days.

ive seen a mention of Firewalls here  on the forums, as well as on the GnomeFiles site.

which brings me to question: if Linux/Ubuntu are more secure than PX/Win, why would we need firewalls? have i been naive? how can i tell if my machine has been compromised?


when i installed Ubuntu a few months ago, i read that by creating a separate partition for my '/home' mountpoint would ease the pain of either upgrading, trying different distros, or in a simpler sense, allow me to retain all my confguration files, settings, and personal files should i ever choose to (again) reinstall Ubuntu.

my thread from here on out shall take a different path.
i will attempt today (in the next hour) to reinstall Ubuntu, but not without backing up my data first. wish me luck everyone!?!?

---

### Post by jammodotnet on 2007-03-24
WOW!
i didnt think i would be able to do it this quickly!

20-30 minutes?!

the ONLY mistake i made was assigning myself a different username when installationg was complete. so now, i had my old /home/olduser/ folder and a /home/newuser/ folder.


at first, i was saddened cause there were no replies to my post ... but then i realized, im just happy, truly glad, that i am getting to the point of KNOWING WTF i am doing here, lol.

Ubuntu has made me a better computer user.
i LOVE the terminal and all her powers ... Windows? what?
neverrrr again!

---

### Post by hikaricore on 2007-03-24
gs - Ghostscript (PostScript and PDF language interpreter and previewer)

hpijs - gs IJS driver (HP Linux Printing and Imaging)

If you're not using hp printing/imaging devices, I'm pretty sure it's safe to kill these processes.

I believe that hpijs is running gs btw.

Also the hp imaging driver is to the best of my knowledge a system service, you can disable this if it's not needed on your system.

Search around the site for disabling system services, there are dozens of great walkthroughs to maximize performance in this area.

---

