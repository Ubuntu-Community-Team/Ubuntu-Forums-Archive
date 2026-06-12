---
title: "No OS Runs On My PC"
date: 2009-03-27
forum: General Help
---

### Post by Unanimated on 2009-03-27
No OS can run perfectly on this PC. Windows, the supposed giant of hardware support, gets the blue screen during installation, so I can't go there. One time I continued the installation, and what I got was a buggy, resource-hogging, blue screen bountiful processor hog. I used Windows several years ago, and it ran perfectly. I haven't changed anything except my video card since then.

And Ubuntu doesn't run perfectly, either. In Kubuntu 8.10, I've been getting more and more frequent kernel panics. Yesterday I had 2 and today I've had one within 20 minutes of using my computer. Again, nothing has changed since it ran perfectly except my video card.

But nothing wrong should be happening with the card. Unless there's an extremely major bug in the drivers for TWO different operating systems, which is extremely unlikely, then I must have a faulty video card or something.

---

### Post by kidux on 2009-03-27
It could be bad VRAM, but more likely bad system RAM. Have you run MemTest86+ yet? Or tried putting the old video card back in?

---

### Post by kerry_s on 2009-03-27
try a different hard drive.

---

### Post by coffeecat on 2009-03-27
It certainly sounds like a hardware, not a software, problem. It could be almost anything. Even [Capacitor Plague]("http://en.wikipedia.org/wiki/Capacitor_Plague").

**Edit:** don't want to labour this, but from that Wikipedia page:

> Some common symptoms are: 
[LIST]
[*]Not turning on all the time; having to hit reset or try turning the computer on again
[*]Instabilities (hangs, _BSODS, **kernel panics**,_ etc.), especially when symptoms get progressively more frequent over time
[*]_CPU core voltage_ or other system voltages fluctuating or going out of range, possibly with an increase in CPU temperature as the core voltage rises
[*]Memory errors, especially ones that get more frequent with time
[*]Spontaneous reboots
[*]In case of on-board video cards, unstable image in some video modes
[*]Failing to complete the _POST_, or rebooting before it is completed
[*]Never starting the POST; fans spin but the system appears dead
[/LIST]


---

### Post by 3Miro on 2009-03-27
If an OS ran once and doesn't run again, it is a hardware issue. Could be the video, but more likely the RAM. Then again, it could be anything.

---

### Post by racerraul on 2009-03-27
I have to say what everyone else has been saying...

You definitely have HW problems.

You're gonna have to tackle them problems 1 at a time.  And it will be time consuming unless you have some sort of way to run HW diags.  Dell, HP are good about having software on CD to do just that on servers, so if you own one of their machines, it should be available free from their websites.

If not, then it would help if you had spare HW to test...

I would start with RAM, then HD since you mentioned blue screens in windows. A system drive or RAM suddenly disappearing will def cause windows to BSOD. Could be as simple as a cable or a bad CD burn too.

Video usually causes lockups, even in Windows.

Good Luck, whatever you do... just do 1 change at a time.

---

### Post by kerry_s on 2009-03-27
the kernel panic tells me hd, memory does a different kind of error. you'll see like read and allocate errors for memory.
kernel panic is hd corruption, it can no longer read the disk properly so it just stops.

---

### Post by Unanimated on 2009-03-29
I told someone about my problem, and he said that it was most likely the HD as well. I forgot to mention that I recently installed a 60GB HDD a friend gave me from his old computer and installed Kubuntu on it. I suppose I could easily just switch the jumpers, install Kubuntu on my 30GB HDD, then copy my /home from it and just wipe the 60GB HDD. I would put in the old video card, but it broke one time - not sure what happened, but no video showed up, and pulling it out resulted in a capacitor falling off, so it's trashed. I'm hoping that it's an HDD or RAM issue. Those are easy (not to mention cheap) to fix.

Is there a program in the repos to check HDD health?

---

### Post by Unanimated on 2009-03-29
Just a clarification as to what happens - I'm not sure if it's an actual kernel panic anymore, but if audio is playing, it loops a small section, similar to a skipping CD. All the visual output is frozen. I wondered for a while if it was just an X server issue, but I'm not so sure anymore. I'll take a look at the capacitors tonight, and see if any have vented or are leaking. Thanks, everyone.

---

