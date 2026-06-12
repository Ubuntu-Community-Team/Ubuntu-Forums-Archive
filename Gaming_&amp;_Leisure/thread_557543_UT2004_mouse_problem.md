---
title: "UT2004 mouse problem"
date: 2007-09-22
forum: Gaming &amp; Leisure
---

### Post by Kenchu on 2007-09-22
Sometimes, just at random occasions, my character will turn "automatically" to some random direction. Really annoying, especially if im loading rockets and suddenly am aiming downwards. Well, it's really annoying generally too of course and could never be accepted, but... Yeah, you get the idea.

Help anyone?
Btw. I've installed both Ubuntu and UT2004 twice (not because of this though), and I've had this same problem both times. Also, I've tried two different mice, and the problem is present with both of them (Logitech Mx518, Logitech Dual Optical).

Regards

---

### Post by Cappy on 2007-09-22
I have this happen to me also. VERY infrequently though - maybe once every 5 hours? For some reason it only happens when I'm NOT fighting someone so it doesn't even disrupt me when it happens. I think it may occur when you move the mouse rapidly and it goes out of some kind of large virtual box in memory for tracking the mouse position.

Basically the way I am aiming immediately flips 180 degrees without any kind of intermediate movement between the two different views.

I think Control+G may solve this problem (while in game of course) but I can't be sure because it hardly ever happens for me.

---

### Post by Nehvrook on 2007-09-23
Hmm, I have no idea about any technical reason this would happen, but I've noticed very similar simptons when people are using an optical mouse on a mouse mat that is too reflective. Have you tried using a different mouse mat?

Probably not the problem, but it's worth a shot lol.

---

### Post by Cappy on 2007-09-23
It's software based because it is a linux only problem. It's possible it is due to the logitech driver because I am using a logitech G5 mouse.

---

### Post by Kenchu on 2007-09-23
> **Cappy said:**
> I have this happen to me also. VERY infrequently though - maybe once every 5 hours? For some reason it only happens when I'm NOT fighting someone so it doesn't even disrupt me when it happens. I think it may occur when you move the mouse rapidly and it goes out of some kind of large virtual box in memory for tracking the mouse position.

Basically the way I am aiming immediately flips 180 degrees without any kind of intermediate movement between the two different views.

I think Control+G may solve this problem (while in game of course) but I can't be sure because it hardly ever happens for me.

To me it happens alot more frequently, about 1 time per 5 min on an average.

I will try out ctrl g when I can and see if it did anything.

---

### Post by Kenchu on 2007-09-25
No it doesn't seem like that did the trick. Im experiencing some insane framedrops online aswell, so Im thinking maybe it's better to play this under windows instead. :p Which is sad because I like being in ubuntu more..

---

### Post by Gillen on 2007-09-26
Hi,

I switched to Ubuntu a year ago when I bought a magazine covering 6.06 LTS I have been playing UT2k4 under each Ubuntu release and it was not until Fiesty that this crazy mouse flip appeared.
I use a generic laser mouse which is excellent under 2000Pro or Vista for UT2k4. Reading various posts and particularly those of Cappy for a different mouse I have been able to smooth the game play to about 95% as good as 2000Pro but this problem remains. I have also noticed that the keyboard scanning under Fiesty does not seem to be up to par as this crazy mouse flip sometimes locks the keyboard which means having to release the key I was pressing (normally forward)  for a moment?
There must be someone in this excellent community that can help.

Regards. Steven.

---

### Post by Cappy on 2007-09-26
> **Gillen said:**
> Hi,

I have also noticed that the keyboard scanning under Feisty does not seem to be up to par as this crazy mouse flip sometimes locks the keyboard which means having to release the key I was pressing (normally forward)  for a moment?
There must be someone in this excellent community that can help.


Hey same for me! I didn't have this problem when I used a PS/2 keyboard but it started occurring once I bought an USB keyboard. It also happens extremely infrequently for me.

I use a creative Fatal1ty keyboard but I doubt that matters.

Kenchu, you should have an adapter for your MX518 so you can hook it up to your PS/2. Can you try that and see if it fixes the problem?

For reference, here is the post Gillen is referring to on changing mouse polling:
[http://ubuntuforums.org/showthread.php?t=392494](http://ubuntuforums.org/showthread.php?t=392494)

---

### Post by Gillen on 2007-09-27
Cappy, This might be unrelated but after yesterdays kernel upgrade to 2.6.20-16 I had a game that night on my brothers Orkney server it was only a short game (2 hours) with just 5 of the Clan playing. During the game the crazy flip keyboard lock only happened once but not to the same degree, it might be just a coincidence?
Our full game is on Friday when there should be about twelve of us playing for about three to four hours I will report back if this problem happens and to what degree.
Just as a bit of background we run the server at a game speed of 135% playing through 750 maps first to 15 frags or the highest after 10 minutes when the map changes, oh and it's just pure Death Match, top stuff.

Regards. Steven.

---

### Post by livingtarget on 2007-11-05
Since there's no solution posted in this thread, I thought I'd do so. To solve this problem just kill "gnome-screensaver" before playing. Whenever the screensaver activates it activates briefly and because you are pressing keys constantly in UT2004 it switches off again and brings UT back up. Annoying to say the least.

It has been reported as a regression, but nobody upstream has had a look at it yet.

Bug Details:
[https://bugs.launchpad.net/ubuntu/+source/libsdl1.2/+bug/32457](https://bugs.launchpad.net/ubuntu/+source/libsdl1.2/+bug/32457)

You can fix this by adding a "killall gnome-screensaver" line in your executable file.

---

### Post by Gillen on 2008-03-23
Thanks LivingTarget worked like a dream.

Regards. Steven.

---

