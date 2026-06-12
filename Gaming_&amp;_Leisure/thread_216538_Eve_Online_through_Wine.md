---
title: "Eve Online through Wine?"
date: 2006-07-15
forum: Gaming &amp; Leisure
---

### Post by Protostar on 2006-07-15
Has anyone gotten Eve Online working successfully through Wine? Because I just downloaded and compiled the latest version last night (0.9.17) and though I managed to install it, it will not connect. Has anyone had any success getting it up and running?

---

### Post by christhemonkey on 2006-07-15
It seems not at the minute.
> What works
The splash screen.

What does not
Everything Else.

What was not tested
The whole game.

Additional Comments
Repeats three fixme's: fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fdcbb08)->(184,0) unrecognized fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fdcbb08)->(194,0) unrecognized fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fdcbb08)->(206,0) unrecognized 

Allthough as you said, this might have changed with the new release of wine.

---

### Post by eqisow on 2006-07-16
I'm pretty sure Cedega has support for EVE Online.

Hopefully there will be a free solution soon. :(

---

### Post by christhemonkey on 2006-07-16
EVE online may be supported with wine!

See this page:
[http://appdb.winehq.org/appview.php?iVersionId=5068](http://appdb.winehq.org/appview.php?iVersionId=5068)

And follow the howto near the bottom of the page.

---

### Post by hobieone on 2006-07-16
i got it running thru cedega but its a bit buggy. on the winehq site they tell you how to get running thru wine but seems to have the same issues as cedega. bascally  stuck at at 1 of 2 resolution levels in full screen theres a black boarder not truelly full screeen and some of the icons on the ui overlap. gameplay is decent but can crash at gate only work around is to zoomm all the way out while gating.

if you read the report on e3 expo this past spring and in one of the ccp dev blogs  the dev are in talks with cedega and those in wine to see about helping them get this game fully working using them. in the dev blog the dev did hint that a linux client may yet be possible. partly due to windows vista which is forcing them to have an extra server just for that os due to enternal testing showed the current eve-online client will not run on vista. and is making them have a second look at linux and to increase in customers in country that are primarily swithing to linux.
 so be be patient looks like theres hope out there. i hope to see this game running native in linux that would rock

---

### Post by Protostar on 2006-07-17
Well I got Cedega and now I can't install it. I think it may have something to do with the fact that I installed it via Wine. Since I didn't install Wine through the repositories and compilied it myself, how do I go about removing it? Would the "sudo dpkg -r" command work?

---

### Post by ceros on 2006-08-04
You should be able to uninstall it by typing in "sudo make uninstall" in the directory you compiled wine in.

---

### Post by Cyraxzz on 2006-08-04
It's a great game. I've heard it has several problems under Cedega.

And according to [this]("http://appdb.winehq.org/appview.php?iVersionId=5068") it works under wine, but most likely unstable.

---

### Post by originof on 2006-08-13
Link for the patch isn't available [http://elfe.mine.nu/eve/linux/]("http://elfe.mine.nu/eve/linux/") ](*,)

---

