---
title: "Unity and netbook performance"
date: 2011-09-18
forum: Desktop Environments
---

### Post by tpprynn on 2011-09-18
I'm using Ubuntu 11.04 with a Packard Bell Dot S netbook - Atom N450 processor, Intel GMA3150 chipset, 1gb RAM. It's 64 bit, but I had tried 32 bit too and the performance difference was unnoticeable by me, with roughly a third of the RAM being used by both.

Currently I'm using the Classic/ no effects option but with Metacity's compositing, a left-side Docky and the default Ambiance theme, approximating Unity. It's noticeably much smoother and I'm wondering if any tweaks can be made, e.g making a xorg.conf, to make Unity run better - I had Ubuntu on my laptop when 9.04 was out and I dimly remember some lines we had to add to xorg.conf to make Compiz smooth. 

I may have misremembered this but wasn't Unity evolved from the Ubuntu Netbook Remix desktop? Odd that it struggles on this netbook then. (Is Compiz fixed for 11.10?)

Thanks.

---

### Post by Copper Bezel on 2011-09-18
So far as I can tell, the issue is that your video card is poorly supported by the current drivers; Compiz (and Unity) are ordinarily quite snappy, particularly the re-written Compiz in 11.04. However, I'm not finding specific solutions for your card. It's possible that someone who has experience with that card specifically can give you some advice on getting it to work properly with Compiz.

Incidentally, the look and feel of Unity's interface was developed based on that of NBR, but it's a completely separate code base.

---

### Post by zami on 2011-09-18
I know this doesn't answer your questions. But.
My netbook struggled with Ubuntu Netbook Remix, and then with Unity.  Gnome 3 was very snappy on it though!  I don't like that style of setup so I  reverted back to vanilla Ubuntu, but you may want to look into Gnome 3 if you can't get Unity working to your liking.

-zami

---

### Post by freddybob on 2011-09-26
Unity (11.04) also runs like a cow on my Asus Eee PC 1000HE ([Intel GMA 950]("http://en.wikipedia.org/wiki/Comparison_of_Netbooks#Specifications")).

I added more RAM (to the max. of 2GB) but it's not improved much.  

After logging in there is a one or two minute delay until my desktop appears.

There is a delay of 10 seconds between pressing the Super key and seeing the dash appear.

With Ubuntu 10.10 and side-mounted Docky this machine used to fly along.

My GPU is rated [good]("https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements") for Unity so I'm hoping for better performance with 11.10.

**Edit:** after a bit more reading I realise the GMA 950 only meets the [minimum requirement]("https://wiki.ubuntu.com/DesktopExperienceTeam/UnityHardwareRequirements") for Unity.

---

### Post by snowpine on 2011-09-26
The obvious experiment is to try a "lightweight" desktop environment like Xfce or LXDE. (Personally I use Ratpoison on my netbooks, but that might be a little extreme for the average user!)

A Google search for "Ubuntu Unity bloated?" gives 2.8 million hits...

---

### Post by Copper Bezel on 2011-09-26
These are compatibility issues, not raw power ones. Unity is as snappy as anything on my machine, and it's to the same specs.

I'd look into Gnome Shell or KDE, honestly, and see if the graphics card support is any different.

---

### Post by freddybob on 2011-10-18
I have upgraded to 11.10 (Oneiric) on my EeePC 1000HE.

Unity 3D's performance is better than under 11.04 but still slow. :neutral:

Unity 2D's performance is very fast. :D

**UPDATE:** trying a fresh installation of 11.10 (rather than an upgrade) and now 3D seems fast too.

---

### Post by mhpathfinder on 2011-12-22
My unit is an Asus EEE PC 1000HEB.  After testing the feel of Ubuntu 11.10, alternating from Unity to Gnome 3, I liked some features, but both hide easy access to apps and folders.  Why do I have to click to a "dashboard" from the main desktop?  Shouldn't the main desktop BE the dashboard?  So, I tried a couple of derivatives--Mint 12 and PinguyOS's pared down Ping-EEE, both of which utilize Gnome 2, although Mint 12 has Gnome 3 as an option, which you may like to try.  I settled on...Ubuntu 10.04 LTS, Netbook Edition.  For me, best netbook menu and best use of limited netbook screen space.  Plus, it's zippy for a netbook.  Unity demands a hardware upgrade.  Ubuntu 10.04,with Gnome 2, boots quickly and navigates with speed and efficiency.  Better than anything that has come along since, but with all that each distro can do, it is a matter of personal feel and comfort, and some opportunity costs for some of the new platforms and features.

---

