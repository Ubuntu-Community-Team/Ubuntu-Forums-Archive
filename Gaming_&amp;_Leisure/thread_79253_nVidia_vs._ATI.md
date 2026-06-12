---
title: "nVidia vs. ATI"
date: 2005-10-19
forum: Gaming &amp; Leisure
---

### Post by ThinkOpen on 2005-10-19
No flames please, just wanted to poll the community... in your opinion which cards work better with Ubuntu out of the box, nVidia or ATI?

Thanks.

---

### Post by Mustard on 2005-10-19
I've never had an issue with my nvidia 5200 FX 128mb card.  It's worked for me flawlessly in Hoary and Breezy.

---

### Post by Dolphin on 2005-10-20
I have ATi.  I like it.  Works well.
But anyone who votes that ATi works *better* than nvidia in a linux environment is fooling themselves.

---

### Post by Jesus Franco on 2005-10-20
Last I checked they both work out-of-the-box just as well.
If you mean witch is easier to get hardware acceleration on, I'd have to say nVidia.

---

### Post by Ibuntu_52 on 2005-10-20
Nvidia has much better linux driver support than ATi.I have an ATi card myself and It works fine in linux, but ATi has no catylist control center for linux which really stinks.Especially since I have an all-in-wonder card.

I'm really not sure how to get my tv stuff working at all:???:

---

### Post by _Pete_ on 2005-10-20
I switched from ATI 9600 to Nvidia 6800 GT. I would say this totally changed the whole linux experience. No more odd lockups and crashing!

---

### Post by Hairy_Palms on 2005-10-20
ATI drivers suck p3n4r, also ati cards perform significantly worse when using openGL compared to nvidia. they are slightly faster when using DirectX though so i dunno if this means wine games run better.

---

### Post by ygarl on 2005-10-20
Tricky - Nvidia tend to PERFORM better, but ATI behave better after - say after a kernel update, when you have to either reinstall the driver or perform general messiness to get the X server running again...

---

### Post by darkmatter on 2005-10-20
nVidia tends to perform better out-of-box, though both are solid performers once setup.

---

### Post by No6 on 2005-10-20
[quote=Dolphin]I have ATi.  I like it.  Works well.
But anyone who votes that ATi works *better* than nvidia in a linux environment is fooling themselves.[/quote]

You've got that right. I have an ATI 9200 and an nVIDIA 5500 and the nVIDIA is by far the better. (I'm not talking speed as the cards are different.)

---

### Post by shawn on 2005-10-20
I always buy nvidia and recommend them to all. I had an ATI once and it was a pain, even in windows.

---

### Post by GIBson3 on 2005-10-20
[QUOTE=shawn]I always buy nvidia and recommend them to all. I had an ATI once and it was a pain, even in windows.[/QUOTE]

I have been running nVidia since the Riva 128, when the GF5X00 series came out I went to a Radeon 9800Pro.  The Windows drivers are great (mostly) but My next videocard will be nVidia again, there have been a few to many "glitchy" things with the ATI. The ATi's are better than they were a few years ago, however I've had far fewer issues with my GF4-ti4600, and the 4600 has been running a lot longer.

so I go nVidia, there are fewer little quirks in my experience.

---

### Post by jecos on 2005-10-20
My 9800pro works just fine, given the driver is still maturing..

ATI is working to get everything implemented in linux, and
I'm content with it... as I can expect a new driver every 2 months.

---

### Post by Tichondrius on 2005-10-20
I've gots the Nvidia 7800 GTX and although Nvidia do support linux well, their windows drivers are always released at least a couple of months before the linux drivers. Annoying, since the latest linux driver (7676 which is newer then the one in ubunutu universe repository) still has quite a few bugs and problems supporting the new 7800 series cards. For example, it doesn't recognize wide screen monitors and only chooses a standard 4:3 mode. Also there are some screen corruptions, performance issues, lockups, etc. Look up nvnews.net linux forum. They took two months to release the 7676 driver version and it fixed ZERO bugs. It's time the release linux drivers concurrently with the windows drivers and make sure they have the same quality.

---

### Post by CapnCook on 2005-10-20
I bought an ATI Radeon 9700 Pro, never could get 3d excelleration working in linux. Bought an Nvidia 5950 Ultra FX and haven't looked back. That ati card just sits in a box, hoping I will someday go back to WinBlows.

---

### Post by floyd27 on 2005-10-20
I have an ati card and it works well in linux..
I voted for nvidia though..They have better drivers...
I can notice a MASSIVE difference in performance from windows to linux...
The linux drivers just arnt up to standard.......yet :)

---

### Post by jeffreyvergara.NET on 2005-10-21
i voted for nVidia, but ATI if you use Window$, Imo, ATI is better than nvidia when it comes to gaming in Window$

---

### Post by krak on 2005-10-21
Nvidia has better drivers but ATI has better hardware. I go for ATI. Developing good drivers is just matter of time

---

### Post by Perfect Storm on 2005-10-21
[QUOTE=krak]Nvidia has better drivers but ATI has better hardware. I go for ATI. Developing good drivers is just matter of time[/QUOTE]


That was not the question.

---

### Post by shakin on 2005-10-21
[QUOTE=krak]Nvidia has better drivers but ATI has better hardware. I go for ATI. Developing good drivers is just matter of time[/QUOTE]

Drivers are more important than hardware. Even in Windows ATI's drivers consistently suck. Two months ago I upgraded my 9800 Pro drivers in Windows and I promptly lost 20 FPS in CS:S. Downgrading fixed the problem. Their Linux drivers are a joke... CS:S is barely playable with Cedega using my ATI card, but with my NVidia card it's excellent.

---

### Post by DRF on 2005-10-21
I've tended to use ATI (not much difference in what the hardware is capable of with either make so it's just a personal preference). But if someone was to come upto me and ask what card to use in a PC they are making for there first Linux experience I would probably have to suggest nvidia as it is quicker and easier to get setup (not that I find ATI hard to setup and wouldn't suggest to anyone that they should change there current graphics card if they allready have an ATI).

Nvidia:
Get kernel module package, xorg package, control panel package. (aka linux-restricted-modules-*kernel-version*-generic-nvidia-legacy, nvidia-glx, nvidia-settings)
Type nvidia-glx-config enable

ATI:
Get xorg package, control panel package (aka xorg-driver-fglrx, fglrx-control)
Open /etc/X11/xorg.conf and replace the existing driver ('ati' or 'radeon' normally with 'fglrx')

If you use the config script that comes with the fglrx drivers it gets too complicated for people new to linux, but you get most of the functionality just by changing that one part of the xorg.conf file.

In both cases I think the companies involved should put more effort into providing the same ease of use and features across all supported platforms.

Daniel

---

### Post by graigsmith on 2005-10-22
ati 9200 is ok,  only if you use the open source drivers and not ati's lousy drivers.  its kinda nice, cause i get decent 3d acceleration right out of the box with breezy and hoary, no need to install any drivers cause the open source ones come with breezy.  and 9200 is apparently the last videocard that works with the open source drivers.   so don't expect to get 3d with open source drivers on some of the newer ati cards.

i tried ati's drivers on my 9200 and, neverwinter nights framerate skipps horribly.  it does allow me to play the doom 3 demo, at a horrrible frame rate.  But that's the only thing it does for me that the open source drivers don't.   Next upgrade for me is going to have to be an nvidia driver.

---

### Post by jecos on 2005-10-22
[QUOTE=shakin]Drivers are more important than hardware. Even in Windows ATI's drivers consistently suck. Two months ago I upgraded my 9800 Pro drivers in Windows and I promptly lost 20 FPS in CS:S. Downgrading fixed the problem. Their Linux drivers are a joke... CS:S is barely playable with Cedega using my ATI card, but with my NVidia card it's excellent.[/QUOTE]

Again everyone seems to forget nvidia started support for linux sooner.. so technically they should be better.  Everyone seems to think nvidia has no problems in linux.  Yes Ati's opengl has bugs, which I only see when trying to run wine/cedega, but all of native games I've tried run just fine.

---

### Post by Biased turkey on 2005-10-23
I didn't vote, I have both ATI Radeon 9600 on my firewall-router and the Nvidia Asus N6600 on my gaming rig.
I installed UT on both systems and both works nicely on the graphical point of view.
But imho, I think Nvidia does a better work at providing the best Linux drivers.
Just follow the instructions at
[https://wiki.ubuntu.com/BinaryDriverHowto](https://wiki.ubuntu.com/BinaryDriverHowto)

---

### Post by brentoboy on 2005-10-23
6 months ago, I would have said nvidia hands down.

But thier newer chipsets (6200 +) have issues with breezy.  I've helped a dozen or so posters on these forums all overcome "no desktop" - brown screen of death right after the ubuntu drums on their first boot.

The fix is to use the official nvidia driver, which has to be rebuilt every time you get a kernel upgrade - which is pretty regularly with breezy right now.

If you have something new, maybe ati is better in breezy.

After checking the ati website (hoping to find opengl support for my laptop) I noticed that they seem to be supporting linux on thier newer chipsets, but they leave you out in the cold if you have a slightly older card.  That doesnt qualify as "supportive" in my book.

However, nvidia doesnt seem to be as linux friendly as they once were. The nforce4 motherboard chipset (ethernet 10/100/1000, sound, etc.) has no linux drivers on their site.  (kind of a bummer here - becuase I bought my m-board becuase it had an nvidia chipset, and I wanted linux support).

---

### Post by IronWolve on 2005-11-05
I have both, not many problems until this new Nvidia 7800 GT, cant get it work. My ATI 9700 PRO and 7000 (laptop) work great.

Nvidia normally gets the nod for better install and support, but this new 7676 driver is borked.

---

### Post by Remmelas on 2005-11-05
Poll kinda needs a third option.  I've had equal and easy success on both of my boxes, one an ati, one an nvidia

---

### Post by Biased turkey on 2005-11-05
[QUOTE=Remmelas]Poll kinda needs a third option.  I've had equal and easy success on both of my boxes, one an ati, one an nvidia[/QUOTE]

So just do what I did, don't vote.
Glad to hear I'm not the only one to have both ATI and Nvidia doing fine.
B.T.

---

### Post by LitnuX on 2005-11-06
Yo.. Could you tell me where to find nVidia Drivers for linux?

---

### Post by alexan on 2010-09-12
I know that's necro posting, but someone has to declare the absolute winner here (also this is a thread of reference for anyone who google).

This pool did collect 5 years of linux user experiences.. and near 9 out of 10 prefer nvidia: there are reason for this.





[COLOR="Silver"]IMHO: Yeah, meanwhile ATI is improved.. but nearly anything they produced in the past was a no-no for linux. Open to OpenSource was just an excuse... they never did provide usable opensource driver or decent proprietary driver.[/COLOR]

---

### Post by ELD on 2010-09-12
You know it's necro, don't do it.

---

### Post by ibuclaw on 2010-09-12
"Sleep, my dear Moderator?", said the thread. "That is the last thing I'll do."

---

