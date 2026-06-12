---
title: "Dock without compiz or effects?"
date: 2008-12-10
forum: General Help
---

### Post by Macmee on 2008-12-10
I'm using dual monitors with an Intel 945GM, and because of this I have to use virtual monitors. With the 945GM and dual monitors where the horizontal resolution exceeds (I think it's) 2048, you cannot enable effects or compiz (apparently). I've already tried a variety of docks which rely on effects/compiz for transparency, and as result the docks either refuse to run, or do run and in place of transparency there's just a black background :(. I also tried SimDock and it ran, though because I have dual monitors it centered in-between both monitors. I turned off auto positioning but it hasn't seemed to work.

Any help is appreciated, thanks!
 - David (I'm runing 8.10 with GNOME)

---

### Post by eternalnewbee on 2008-12-10
Hi there.
You don't need compiz to run Cairo-Dock. You might want to give it a shot.
[https://help.ubuntu.com/community/CairoDock](https://help.ubuntu.com/community/CairoDock)

---

### Post by Twitch6000 on 2008-12-10
wbar might suit your needs although it isn't quite a fully featured dock either.

I think Kiba-Dock can run without Compiz aswell although I cannot confirm this as I have always ran Kiba-Dock(or any dock for that matter) with compiz on.

---

### Post by Macmee on 2008-12-10
Thanks guys, but I've already tried both. Cairo I think does rely on compiz, when I use compiz where it should be transparent it's black. As for Kiba it did work, however when I right mouse click on it, it freezes my entire system, and I have to reboot.

---

### Post by yogo on 2008-12-10
> **Macmee said:**
> Thanks guys, but I've already tried both. Cairo I think does rely on compiz, when I use compiz where it should be transparent it's black. As for Kiba it did work, however when I right mouse click on it, it freezes my entire system, and I have to reboot.


Here is a little magic for you. Transparency and Cairo-dock

gconftool-2 -s -t bool /apps/metacity/general/compositing_manager true

Props go to Forlong for this.

---

### Post by eternalnewbee on 2008-12-11
> Thanks guys, but I've already tried both. Cairo I think does rely on compiz, when I use compiz where it should be transparent it's black. As for Kiba it did work, however when I right mouse click on it, it freezes my entire system, and I have to reboot.
Check this out:
[https://help.ubuntu.com/community/CairoDock](https://help.ubuntu.com/community/CairoDock)

---

### Post by Macmee on 2008-12-11
> **yogo said:**
> Here is a little magic for you. Transparency and Cairo-dock

gconftool-2 -s -t bool /apps/metacity/general/compositing_manager true

Props go to Forlong for this.

It works! Thanks:D!

---

### Post by eternalnewbee on 2008-12-11
Excellent. Remember, if your problem is solved to mark it as such, under [COLOR="Red"]Thread Tools[/COLOR], at the top of this page.

---

### Post by Macmee on 2008-12-11
> **eternalnewbee said:**
> Excellent. Remember, if your problem is solved to mark it as such, under [COLOR="Red"]Thread Tools[/COLOR], at the top of this page.

Thanks, though after enabling the setting that fixed the dock, remote desktop stopped working for my Virtual XP. Now when I run the remote desktop, the XP screen is locked up, all my GNOME bars are 100% transparent, and my dock at the bottom autohides upon hovering over it. The only way to fix this is to do
gconftool-2 -s -t bool /apps/metacity/general/compositing_manager false

---

### Post by fabounet on 2008-12-12
did you try with the fake transparency of Cairo-Dock ? (in the System tab)
it's a workaround but you won't need composite manager then.

---

### Post by Macmee on 2008-12-12
> **fabounet said:**
> did you try with the fake transparency of Cairo-Dock ? (in the System tab)
it's a workaround but you won't need composite manager then.

Yes, it works but makes the dock only appear on the desktop.

---

### Post by yogo on 2008-12-12
> **fabounet said:**
> did you try with the fake transparency of Cairo-Dock ? (in the System tab)
it's a workaround but you won't need composite manager then.


Interesting, I did not know about that!

 When I use the built-in fake transparency though, my dock is hidden behind all windows that are open. ie browser is on top of dock etc so the only way to view the dock is to minimize windows..

The fix [ gconftool-2 -s -t bool /apps/metacity/general/compositing_manager true] leaves the dock on top of windows but has some minor quirkyness.

I looked thru the configuration, I could not see how to get the dock on top of windows using the fake transparency.

For the record, I changed no setting, the dock behind windows happened when using built-in transparency.

Any ideas?

TIA

---

### Post by fabounet on 2008-12-15
when using fake transparency, the dock is purposely left behind other windows, because otherwise you would see the dock's background.
you would see a piece of wallpaper covering your windows, which is not nice.

---

### Post by 4ebees on 2008-12-29
Maaaaaaaaaaaate,

Thanks for that. I'd installed this one of my children's computers and it was driving me crazy!

Brilliant.:popcorn:


> **yogo said:**
> Here is a little magic for you. Transparency and Cairo-dock

gconftool-2 -s -t bool /apps/metacity/general/compositing_manager true

Props go to Forlong for this.

---

### Post by chosenbeans on 2009-09-06
> **yogo said:**
> Here is a little magic for you. Transparency and Cairo-dock

gconftool-2 -s -t bool /apps/metacity/general/compositing_manager true

Props go to Forlong for this.

That is probably one of the most useful commands I have ever seen. I was trying to accomplish this in Arch Linux. Worked like a charm. At the time I executed this command I had about three other docks open but they would not show up due to lack of having Compiz. Once I used this command all three docks showed up. I can now use all docks that require Compiz thanks!

---

### Post by chosenbeans on 2009-09-12
> **yogo said:**
> Here is a little magic for you. Transparency and Cairo-dock

gconftool-2 -s -t bool /apps/metacity/general/compositing_manager true

Props go to Forlong for this.

I turned it into a button using Python and Tkinter! CKB stand for "Compiz Killing Button". I wanted to make it easier for some users to do this. Hope this helps. 

Just download my attachment and double click it to run it.
(when you click ckb a box will appear where you click "Run")

Note you need python3 to run this. 

```
sudo apt-get install python3-tk
sudo apt-get install python3
```

You also need to make it executable by right clicking ckb > Properties > Permissions > check the box next to "Execute:" or just enter this command if ckb is in your home folder:

```
chmod +x ckb
```

Let me know if any of you use this as it is my first GUI program with Tkinter. :-)

---

