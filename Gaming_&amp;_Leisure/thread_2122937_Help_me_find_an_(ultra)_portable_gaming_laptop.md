---
title: "Help me find an (ultra) portable gaming laptop"
date: 2013-03-06
forum: Gaming &amp; Leisure
---

### Post by Vermind on 2013-03-06
Hi,
I am looking for a laptop that I could use as a Linux gaming laptop.
It needs to be able to run Spring / Zero-K, Achron, and everything in the Humble Bundles so far.
My current laptop is an [Asus UL30VT]("http://www.asus.com/Notebooks/Superior_Mobility/UL30Vt/#specifications") which gives me 8 hours of battery life with discrete graphics off, and lets me play most of the games I want to play. However, it gets slow with Zero-K and Dungeon Defenders (Humble Bundle 7).

My best choice right now seems to be [Asus UX32VD-DH71]("http://www.amazon.com/UX32VD-DH71-Ultrabook-i7-3517U-Bluetooth-Aluminum/dp/B009XU3F8C/ref=sr_1_85?s=electronics&ie=UTF8&qid=1358695816&sr=1-85&keywords=asus+laptop+i7").
However, [This review]("http://www.maximumpc.com/article/%5Bprimary-term%5D/asus_zenbook_ux32vd_review") says that the battery life sucks.

My preferred specs:
Weight: 1.5 KG / 3 LB
Size: 13-14 inch
Screen: 1920x1080 (Not going to buy a smaller one)
Battery: 8 hours with discrete graphics disabled (Probably going for an Optimus laptop)
Graphics: nVidia
CPU: Core i7 preferred (Spring/Zero-K is CPU intensive), others ok too
Price: prefer under 1000 EUR / 1300 USD
For a really good one willing to go up to 1200 EUR / 1500 USD

I will upgrade memory and disk if they are not adequate.

Obviously it's better if someone has tested that Ubuntu or another Linux works on it :).

Any ideas?

---

### Post by oldrocker99 on 2013-03-06
What desktop are you using? I am having great success with razor-qt, a sort-of KDE Lite which uses as few resources as LXDE, but appears to be much more powerful, on a single-core 1.6 MHz Asus Aspire 5516. To install:

sudo apt-add-repository ppa:razor-qt/ppa && sudo apt-get update && sudo apt-get install razor-qt

Then log out and log back in, selecting Razor Desktop. Use htop or top or something to see how low the CPU usage is; I think you'll be impressed, especially if you first check the CPU load on your current desktop.

---

### Post by drawkcab on 2013-03-07
Fair warning, optimus is more than a bit fidgety with the new kernel and doesn't work with hdmi out.

I would wait a few months if not a year to see how support for optimus shapes up.

---

### Post by Vermind on 2013-03-07
Hi guys, thanks for the replies. I have been using powertop to optimize the battery, and I am happy with my desktop's energy usage with the laptops I have tried.
As for Optimus, I am having success with my pre-optimus laptop, the UL30VT, with bumblebee and bbswitch. Since it is  PRE-Optimus, I can actually run pure nVidia and that gives me the HDMI out. This will not be possible for Optimus laptops, which I am aware of.

When Ubuntu changes to MIR and everyone else changes off of X, we will probably see something different happen with optimus/bumblebee. The PRIME framework that was the "right" way to do it for X will probably not be used on very many modern machines.

However, I am looking for a better laptop; please suggest some. Let's talk about Optimus and power optimization / light desktops in another thread :).

---

### Post by mastablasta on 2013-03-07
it's difficult to find a new laptop that works with linux. unless someone already bought it and tried to stick linux on it. there is ubuntu certified website but those models are outdated. it didn't help me at least.

anyway some hybrid Intel/AMD and AMD/AMD combos also work ok with proprietary drivers installed. 

as for battery i found it best if you can find a model that works well in linux to then search if stronger battery is available.sometimes they sell it as accessories, sometimes you can get "unnoficial one" (from other manufacturers)

---

### Post by cRaZyBisCuiT on 2013-03-07
What about any solid Ultrabook with a good display and a HD4000? Or maybe wait for HD5000 to be launched. That one should handle all HiB Games including Dungeon Defenders.

I personally would not go for any switchable solution, no matter if Optimus or AMD switchable.

---

### Post by Vermind on 2013-03-07
> **cRaZyBisCuiT said:**
> What about any solid Ultrabook with a good display and a HD4000? Or maybe wait for HD5000 to be launched. That one should handle all HiB Games including Dungeon Defenders.

I personally would not go for any switchable solution, no matter if Optimus or AMD switchable.

That sounds like a good idea. My previous laptop's GMA X4500MHD and the work laptop's Core i7 integrated thing "Intel(R) Sandybridge Mobile (GT2)" according to Xorg log both don't handle Spring well.
Does anyone have experience of running Spring or HiB games on HD4000? My issues are mostly with drivers for Intel, not so much the performance side. The drivers are known to have issues with games that nVidia or ATI drivers don't have.

---

### Post by cRaZyBisCuiT on 2013-03-07
[B]ppa:ubuntu-x-swat/x-updates 

[COLOR=#ff0000]Try that at your own risk! External PPAs may brake your system!

[/COLOR][/B]I'm using this ppa which has some recent drivers in in it. It's quite more stable then **ppa: org-edgers/ppa **(I recommend not to use that one). It runs quite well on the notebok of my girlfriend. The only thing you still need to do then is to activate texture compression and you're done.
Of course high demanding games like Oil Rush and Trine 2 **[COLOR=#ff0000]WON'T RUN ON MAX SETTINGS[/COLOR]** with a HD4000! Please keep that in mind. HiB Games that are released until now should be running quite fine.

---

### Post by Vermind on 2013-03-07
Edit: Hi, I just checked, and the work laptop is an Asus UX31, with Integrated Intel HD Graphics 3000: [http://www.asus.com/Notebooks_Ultrabooks/ASUS_ZENBOOK_UX31E/#specifications](http://www.asus.com/Notebooks_Ultrabooks/ASUS_ZENBOOK_UX31E/#specifications)

> **cRaZyBisCuiT said:**
> [B]ppa:ubuntu-x-swat/x-updates 

[COLOR=#ff0000]Try that at your own risk! External PPAs may brake your system!

[/COLOR][/B]I'm using this ppa which has some recent drivers in in it. It's quite more stable then **ppa: org-edgers/ppa **(I recommend not to use that one). It runs quite well on the notebok of my girlfriend. The only thing you still need to do then is to activate texture compression and you're done.
Of course high demanding games like Oil Rush and Trine 2 **[COLOR=#ff0000]WON'T RUN ON MAX SETTINGS[/COLOR]** with a HD4000! Please keep that in mind. HiB Games that are released until now should be running quite fine.

I use libtxc-dxtn (S3TC compression) and recently the libtxc-s2tc for the compression. Nowadays, that's not needed so much as it was before.
I have been hopping between xorg-edgers and glasenhardt's PPA: [https://launchpad.net/~glasen/+archive/intel-driver](https://launchpad.net/~glasen/+archive/intel-driver) . On debian, I take Intel drivers directly from experimental.
Those PPAs have fixed some visual issues I have with Spring on the work laptop to the point that it is playable but gives lots of errors and makes units invisible on certain zoom levels.

What I talk about when I want games to work with an Intel card, I mean that they don't crash with missing openGL extensions or just segfault when I run them, like Shank 2 and Dungeon Defenders on the GMA X4500MHD. When I run those through optirun, everything is fine.

Edit: I just took drivers for the work laptop from [https://launchpad.net/~oibaf/+archive/graphics-drivers/](https://launchpad.net/~oibaf/+archive/graphics-drivers/) and they are super snappy.
Achron is better than previous driver (messy random colour lines on terrain), with now just black lines on terrain: [http://imgur.com/xmSKo59](http://imgur.com/xmSKo59)
Still, I would prefer no lines on terrain as I get with nVidia...
Dungeon defenders is a black screen with a menu: [http://i.imgur.com/lT0rK47.png](http://i.imgur.com/lT0rK47.png)

Edit: This highlights the issue. Intel: One game, nVidia: all of them. [https://bbs.archlinux.org/viewtopic.php?pid=1209102](https://bbs.archlinux.org/viewtopic.php?pid=1209102)

---

### Post by cRaZyBisCuiT on 2013-03-07
To be honest, the GMA4500MHD is a pretty crappy chipset. I also got that one in my office notebook. I wouldn't wonder if there are some more Open GL Libs provided for HD4000. But I don't have one to try that out. But still, the Intel drivers are getting better and better, though the nVidia and especially AMD drivers, too. In the end I would avoid to use a switchable system. Optirun is not optimal and AMD solutions often suck. So unless you know they work pretty well for a specific mashine (some does!) I would not get them.

---

### Post by Am Elder on 2013-03-08
I can't talk intelligently about chipsets.  My next laptop will be the first I buy with a serious eye to gaming performance.  However, it seems to me you should take a look at the Clevo gaming laptops.  Something like the [Clevo W25AEF]("http://www.avadirect.com/gaming-laptop-configurator.asp?PRID=25872"), for example.  It's at least no further from your ideal configuration than the Asus you're looking at, I think.  It can come loaded with Kubuntu, which is surely some indication that it's Linux friendly.

---

### Post by myromance123 on 2013-03-08
Steer clear of AMD Hybrid graphics if you can. I still can't get the AMD driver to be installed on my father's HP Envy 17", which comes with a Sandy bridge i7 and an AMD HD6850M. I can only get the Intel Integrated graphics to work, not the 6850M at all.

On the other hand, while Nvidia Optimus is not in great shape it is better. My sister's Asus laptop ( I forget the model number ) which comes with an Nvidia 550M and Intel Integrated graphics is at least functional with Bumblebee. I'd say get a laptop with only one graphics solution, but in this modern age of combining the CPU with a GPU, that's impossible now. All new model laptops I can see have Intel's Integrated solution or AMD's APU solution.

However, System76 offer some seriously cool laptops that work with Ubuntu off the bat (if you can get them to ship to you). There's also ZaReason, if you're interested.

To me, System76's Bonobo Extreme that can come with a GTX 680M looks seriously awesome. I don't know if it's battery life may suit you though, but there are reviews of it on Youtube for you to check out :)

Link to the Bonobo Extreme:
[https://www.system76.com/laptops/model/bonx6]("https://www.system76.com/laptops/model/bonx6")
If that's too high price or too much, they do have lower end models to choose from!

---

### Post by Vermind on 2013-03-08
Hi,
the bonobo extreme looks like a tank :). It gives probably all the performance I need, the weight is a little on the heavy side.
Also the Clevo is otherwise great, but the size is larger than my optimal (13.3 - 14 inch). All the other specs check out great.
Thanks for the suggestions.

I have had good experience with my switchable graphics machine, and I have become quite familiar with the libraries and tools required to get that working on any machine. I have some scripts for a working hybrid graphics setup in my linux-stuff repo:
[https://github.com/lagerspetz/linux-stuff](https://github.com/lagerspetz/linux-stuff)

---

### Post by Vermind on 2013-03-15
This one by Gigabyte is light enough, resolution is a bit worse (1600x900), but comes with SSD, a better GPU, and 8GB memory to start with:
[http://www.amazon.co.uk/GIGABYTE-14-1-inch-Ultrabook-Graphics-i7-3517U/dp/B009P4UEGC/ref=sr_1_2?ie=UTF8&qid=1363373365&sr=8-2](http://www.amazon.co.uk/GIGABYTE-14-1-inch-Ultrabook-Graphics-i7-3517U/dp/B009P4UEGC/ref=sr_1_2?ie=UTF8&qid=1363373365&sr=8-2)
It's also a little thicker.

Edit: Amazon reports a completely different weight than is reported here:
[http://www.gigabyte.com/products/product-page.aspx?pid=4210#kf](http://www.gigabyte.com/products/product-page.aspx?pid=4210#kf)

---

