---
title: "sword and sworcery graphics problem"
date: 2012-06-08
forum: Gaming &amp; Leisure
---

### Post by dougleduck on 2012-06-08
I've attached a screenshot of the first thing I see when trying to play sword and sworcery. Installed via the software centre (from HIBV :) ). The game doesn't lag or crash, the graphics don't display properly. 

Running from command line I see no output. 

I'm fully up to date (I've reinstalled the game, including clearing the cashed package).

Specs below.

Any ideas? I've yet to find anyone else with this problem. Cheers for any help.

---

### Post by Shwetank on 2012-06-10
> **dougleduck said:**
> I've attached a screenshot of the first thing I see when trying to play sword and sworcery. Installed via the software centre (from HIBV :) ). The game doesn't lag or crash, the graphics don't display properly. 

Running from command line I see no output. 

I'm fully up to date (I've reinstalled the game, including clearing the cashed package).

Specs below.

Any ideas? I've yet to find anyone else with this problem. Cheers for any help.
I have the exact same problem.. :/


Specs:
Dell Inspiron N5010
12.04 32 bit
raedon hd 5xxx series
first gen i5
4 gb ram.

---

### Post by Gaygerbil on 2012-06-11
Weird mine runs perfectly on an onboard card. (Nvidia Geforce 4300)

How does it look in the main menu? And have you tried changing the resolution around or taking it out of fullscreen to see if it does anything?

---

### Post by dougleduck on 2012-06-11
Equally strange on different resolutions, in window mode, and on the start screen.

I've got a radeon card, not NVidea (no problem with other games, can just about run skyrim).

---

### Post by thatguruguy on 2012-06-11
Have you checked your log?  You can read it by typing the following in a terminal:
```
gedit ~/.capy/SwordAndSworcery/log.txt
```Feel free to change "gedit" to whatever your editor of choice is.

---

### Post by dougleduck on 2012-06-11
Looks fine to me, no errors or warnings. File attached.

---

### Post by Shwetank on 2012-06-11
> **dougleduck said:**
> Equally strange on different resolutions, in window mode, and on the start screen.

I've got a radeon card, not NVidea (no problem with other games, can just about run skyrim).

Same ... Is it because of the radeon card.. :/ and bastion is also giving me probs.... hanging at startup.. :(

---

### Post by Shwetank on 2012-06-11
> **Gaygerbil said:**
> Weird mine runs perfectly on an onboard card. (Nvidia Geforce 4300)

How does it look in the main menu? And have you tried changing the resolution around or taking it out of fullscreen to see if it does anything?

One thing... when the game opens and the game's logo comes swirling on the screen ..everything looks fine but as soon as it stops the graphics gets corrupted.

---

### Post by thatguruguy on 2012-06-11
FWIW, it appears that Windows users with ATI graphics are having the same or similar problems.  You might want to read [this thread]("http://forums.steampowered.com/forums/showthread.php?t=2654637") on the Steam forum and see if any of the information contained therein is helpful to you.

---

### Post by moteprime on 2012-06-17
Any body found out what to do, mine doesn't even start up.
I get this in the log and it just crashes. -also have Radeon. (for the last time).
> Error: FMOD Event System update error! (81) This command failed because System::init or System::setDriver was not called. 

---

### Post by lbds137 on 2012-06-17
> **thatguruguy said:**
> FWIW, it appears that Windows users with ATI graphics are having the same or similar problems.  You might want to read [this thread]("http://forums.steampowered.com/forums/showthread.php?t=2654637") on the Steam forum and see if any of the information contained therein is helpful to you.

Thanks for posting the link - I found that disabling Catalyst AI immediately solved my problems. I hope it works out for you guys, too.

---

### Post by dougleduck on 2013-01-16
Disabling catalyst AI worked. Cheers.

---

