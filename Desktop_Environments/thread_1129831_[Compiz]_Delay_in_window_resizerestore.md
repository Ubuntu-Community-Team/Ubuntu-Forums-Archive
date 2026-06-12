---
title: "[Compiz] Delay in window resize/restore"
date: 2009-04-19
forum: Desktop Environments
---

### Post by Kemper Boyd on 2009-04-19
On a freshly installed 9.04 with standard gnome/compiz desktop env, I notice that resizing windows has a weird delay: when I click on a corner (or ALT + middle mouse) the resizing box appears immediately, but it takes about half a second from release to actual window resize.

Same delay happens when restoring a windows which was minimized to the panel.

I never had this problem on my old 7.10 and it's quite annoying, how can I fix it?

Thanks

---

### Post by sagarthegreat1 on 2009-04-25
i too, am facing the exact problem...
my gfx card is ati 4670...with fglrx drivers...any solutions?

---

### Post by ChrisBeaumont on 2009-04-26
I am having the same problem - started right after I upgraded to jaunty. Graphics card is ATI Radeon 3650

---

### Post by Greguti on 2009-04-27
Same here, ATI Radeon HD 3650, Asus F8vA... Compiz effects are quite unstable for now. Fresh install of Jaunty Jackalope.

---

### Post by sagarthegreat1 on 2009-05-01
yup but when compiz is dsabled, jaunty is snappier than ever...why why why o god?

---

### Post by ChrisHolloway on 2009-05-03
I'm seeing the same delay, just upgraded to 9.04 today on my HP 8510p.  It has an ATI Radeon Mobility 2600 in it.  Any idea what is causing this or a way to fix it?

---

### Post by Nickro on 2009-05-03
I tryed both 32 and 64bits versions of Ubuntu 9.04 and same problem here with Ati HD3870.

---

### Post by Eld.Raven on 2009-05-04
Ive got the same problem, have tried to google it without finding any solution!

---

### Post by Greguti on 2009-05-05
Hi all,

it's not a fix, but FYI, I removed the ATI proprietary driver from my Asus F8vA, and just rebooted. Now the opensource driver is enabled. 

According to Synaptic, it's now server-org-video-ati and xerver-xorg-video-radeon that are installed (I don't really understand the differences between these two packages).

Well, all I can say is that it's FAR MORE STABLE and quick than the official ATI driver. Gnome is far more responsive, even typing text on Firefox or OpenOffice seems faster.

The Compiz effects can't be enabled at all with this free driver, but with the composite effect activated (via Ubuntu Tweaks), I have sexy shadows under the windows and menus and the Alt-Tab function shows snapshots of the applications ; so after all I feel great even withtout the Compiz effects... I mean I can run with Metacity for few weeks or months without feeling frustrated at all (at least I feel like I could!).

Regards to all :)

Greg from Paris

---

### Post by Eld.Raven on 2009-05-05
Well, then u could jusxt have turned off compiz-effects and get ubuntu-tweek. The thing is that you dont want to do that =)

---

### Post by Greguti on 2009-05-06
> **Eld.Raven said:**
> Well, then u could jusxt have turned off compiz-effects and get ubuntu-tweek. The thing is that you dont want to do that =)

I may be wrong, but I think that if I just turn off the Compiz effects, while using the official ATI proprietary driver, it's still that driver that is running! My point is that the opensource driver for this videocard makes the Gnome experience smoother and faster. One may lacks the nice Compiz effects (I do like some 3D desktop enhancements too!), but at least, the overall experience is greater without the proprietary driver.

Regards

Greg from Paris

---

### Post by Eld.Raven on 2009-05-06
Hmm I use the offical driver from ATI, and if I deactivated compiz it will run as smooth at ever, I get problems without the offical driver. Like I cant use max resolution, I cant activate desktop effects and so on. But I guess that this could vary from computer to computer. 

// Seb

---

### Post by Zyren on 2009-05-06
same here. ati 3650, takes a whole 2 seconds to maximize a screen once its minimized. Overall compiz is pretty slow. Not very happy since its a new computer.

---

### Post by madias on 2009-05-07
bug confirmed: [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/351186](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/351186)
we have to wait.

---

### Post by Eld.Raven on 2009-05-07
Yeah I read about it too! =/

---

### Post by futuroimperfetto on 2009-05-10
Damn,

 I seem to have the same bug you guys have, but on an nVidia 8400 GS... I googled a bit, but I couldn't find if a similar fix is in the works for nVidia cards...

Good luck to everyone... It's a pity since desktop effects were working perfectly on Hardy Heron! Argh...

---

### Post by Parp on 2009-05-10
[https://edge.launchpad.net/~ubuntu-x-swat/+archive/xserver-no-backfill](https://edge.launchpad.net/~ubuntu-x-swat/+archive/xserver-no-backfill)

Fixed it for me (ATI), Intel have issues with this patch. It's not a proper fix, but it worked for me, for some it has broken their x-servers, so treat with caution, try googling the xserver-no-backfill to see if there is any other info...

---

### Post by Margate on 2009-05-24
Upps, I also added this to an ALT-TAB thread,It might be more appropriate here as I had several issues incl. resize, restore etc...

I had same experience, any actions when switching between windows (except mouse click) resulted in very slow performance, I believe functions such as ALT-TAB involve compiz. Anyway; I remembered that I a few days ago installed Skype and along with that some required qt4 libraries. Removing Skype didn't change anything, Removing qt4 libraries fixed my performance issues using ALT-TAB.

Kind Rgds.
Margate

Versions
Linux 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux
VGA compatible controller: nVidia Corporation GeForce 9600M GT (rev a1)

---

### Post by eerror on 2009-05-24
Just a little bit on my recent experience with an ATI FGLRX driver...

I installed 9.04 on a Toshiba Satellite L300D-044 ( Athlon 64 X2, 4GB RAM, 250GB HD, ATI Radeon 3100 ).  Initially everything worked with no special tweaking required. Wireless, webcam, microphone worked (THANK YOU UBUNTU!) and playing video clips was fine. Then I installed the ATI driver.
videos became choppy, could not display them in full screen mode (either froze or no video was shown, audio still played)

One thing that surprised me was that even the webcam was affected.  Skype test now appeared extremely zoomed in the left-mid section.  Imagine only seeing half of your forehead if you shifted yourself to the left of your laptop.  After troubleshooting for a bit, I removed the ATI driver and everything went back to normal.  Webcam now works, video playback is fast and works in full screen mode.

Hope this helps someone if you're troubleshooting weird webcam issues on a similar Toshiba laptop or general poor display performance.  Stay away from that ATI driver.

---

### Post by HavocXphere on 2009-05-24
Has anyone tried the new 9.5 ati driver yet? Does it make a difference?

---

### Post by Hund on 2009-05-24
> **HavocXphere said:**
> Has anyone tried the new 9.5 ati driver yet? Does it make a difference?

No difference for me. I switched to the open source driver yesterday and I still have the delay problem when I'm using Compiz.

---

### Post by I_can_see_the_light on 2009-05-28
> **Hund said:**
> No difference for me. I switched to the open source driver yesterday and I still have the delay problem when I'm using Compiz.

Have you tried [[COLOR="Blue"]this[/COLOR]]("https://edge.launchpad.net/~ubuntu-x-swat/+archive/xserver-no-backfill") Hund? Fixed the delay problem for me. I have an ATI mobility Radeon X600 using the open source drivers with XAA acceleration. I have not had any problems (so far) with video corruption.

---

### Post by fbkarsdorp on 2009-05-28
I'm on a Vaio-fw(3) series, running ubuntu jaunty 64bit using the fglrx driver (catalyst 9.4). I also noticed the restoring/resizing windows issue. Tried catalyst 9.5 which didn't fix it (in fact I lost video support...). I also saw that there is a patch for this issue. But I don't like patches, especially not when they do not fix all of the problems...

Today through trial and error I managed to get some improvement. From a 3 to 5 second delay to only say 1. Ok, not perfect but a whole lot better!!

This seems to be the problem. It is glxgears having very low fps with fglrx and that's because of PowerPlay. In the catalyst control center you can turn this off.

Hope it helps.

---

### Post by marbot on 2009-05-31
Hi everyone

After installing the newest ATI Driver 8.612 on my Ubuntu 9.04, i ran into this problem too. I had a 2sec delay on maximizing / restoring windows using Compiz.

I managed to solve it by installing :

XServer with no backfill functionality
[https://edge.launchpad.net/~ubuntu-x-swat/+archive/xserver-no-backfill](https://edge.launchpad.net/~ubuntu-x-swat/+archive/xserver-no-backfill)

Everythings works fine again now,

My config:

- Ubuntu Jaunty 9.04
- ATI Mobility Radeon HD 3400 Series
- Driver Version 8.612

Hope this helps

Good Luck
marbot

---

### Post by chadillac83 on 2009-06-06
> **Parp said:**
> https://edge.launchpad.net/~ubuntu-x-swat/+archive/xserver-no-backfill

Fixed it for me (ATI), Intel have issues with this patch. It's not a proper fix, but it worked for me, for some it has broken their x-servers, so treat with caution, try googling the xserver-no-backfill to see if there is any other info...

ATI Technologies Inc Mobility Radeon HD 3600 Series + KDE 4.2

this fixed it for me as well... thanks for the find, this was driving me nuts since I installed jaunty.

---

### Post by ZaHACKieL on 2009-06-08
> **HavocXphere said:**
> Has anyone tried the new 9.5 ati driver yet? Does it make a difference?

I installed the 9.5 driver few moments ago and I still have the delay problem. I may be wrong but it seems the delay is slightly shorter now, but anyway, I still the bug

---

### Post by n0xx on 2009-06-24
> **Parp said:**
> [https://edge.launchpad.net/~ubuntu-x-swat/+archive/xserver-no-backfill](https://edge.launchpad.net/~ubuntu-x-swat/+archive/xserver-no-backfill)

Fixed it for me (ATI), Intel have issues with this patch. It's not a proper fix, but it worked for me, for some it has broken their x-servers, so treat with caution, try googling the xserver-no-backfill to see if there is any other info...

Yes!!! OMG Finally!!! I've been searching for something to fix this issue for years! Ever since compiz came out!

Plz someone sticky this! Someone make this the default Xserver, or whatever.. This is GREAT! I don't need to resize windows with the stupid blue rectangle anymore! It's THAT much better!

ATI Radeon HD 3450 on Sony Vaio VGN-FW11E. Windows are now as snappy as Vista. Only emesene (the python msn messenger client) redraws a bit slower, probably because of theming/gtk issues, since it redraws/resizes a bit slowly even while running metacity. Still, this rocks!

I wonder why don't they make this the default x-server?!... My mate is going to check this out too, he's running X on open source driver... so i guess either of us gonna report how it turned out for him.

Tanks so much for this awesome tip. I would also like to thank the guys at Ubuntu-X team who cracked it. EPIC WIN M8s!

- Plz sticky this!
- Plz consider incorporating this patch by default on the next release...

---

### Post by ChrisBeaumont on 2009-07-07
Hi,

I've been stuck with the same problem ever since I upgraded to Jaunty. I'd like to try out this new xserver build. I added the appropriate launchpad.net URLs to my list of software sources but, when I run sudo-apt-get update, the new package doesn't get marked for installation/updating.

Am I missing something obvious? Do I need to do anything else to coerce the new xserver installation?

---

### Post by Zirafon on 2009-12-09
Hello, I just want to report that I tried the solution via adding  [https://edge.launchpad.net/~ubuntu-x-swat/+archive/xserver-no-backfill](https://edge.launchpad.net/~ubuntu-x-swat/+archive/xserver-no-backfill)

on Ubuntu 9.10, with ATI HD 4570 and it works well, without any unwanted sideeffects.

---

### Post by joes7 on 2009-12-09
Check if your video card is activated on your pc. Go to Applications->System->Hardware drivers. If that is the problem, your video card should be listed on there. It happened to me with my NVidia card.

---

### Post by jeffltw on 2009-12-18
> **marbot said:**
> Hi everyone

After installing the newest ATI Driver 8.612 on my Ubuntu 9.04, i ran into this problem too. I had a 2sec delay on maximizing / restoring windows using Compiz.

I managed to solve it by installing :

XServer with no backfill functionality
[https://edge.launchpad.net/~ubuntu-x-swat/+archive/xserver-no-backfill]("https://edge.launchpad.net/%7Eubuntu-x-swat/+archive/xserver-no-backfill")

Everythings works fine again now,

My config:

- Ubuntu Jaunty 9.04
- ATI Mobility Radeon HD 3400 Series
- Driver Version 8.612

Hope this helps

Good Luck
marbot

Yeap this worked for me too. Installed it and rebooted xserver. Resizing is snappy now.

Thanks!

---

### Post by Muskalado on 2009-12-28
> **jeffltw said:**
> Yeap this worked for me too. Installed it and rebooted xserver. Resizing is snappy now.

Thanks!

This worked for me too! I thought it was my harddisk that caused the delay.

Thanks alot! :):)

---

### Post by cal9745 on 2010-01-01
> Hello, I just want to report that I tried the solution via adding [https://edge.launchpad.net/~ubuntu-x...er-no-backfill](https://edge.launchpad.net/~ubuntu-x...er-no-backfill)

on Ubuntu 9.10, with ATI HD 4570 and it works well, without any unwanted sideeffects. 

On 9.10 and my ATI HD 4650, after installing the no-backfill updates I boot to a black screen. I've tried installing it on multiple installations, with the same effect each time, and I've followed the instructions exactly.

Anybody else getting a black screen at boot after installing no-backfill?

(I've also tried the newest ATI drivers of their site, same lagginess)

---

### Post by chronniff on 2010-01-24
I had that problem when I first applied my patch....I found that you have to uninstall fglrx and then reinstall it after you have installed the patched xserver, and then of course run the aticonfig --initial -f.....I did that and I booted up with faster compiz effects...although I still have some video tearing but I think that has to do with my vga connection to my monitor which will be remedied soon

---

### Post by raghu1111 on 2010-02-07
For users like me, just disabling desktop effects might be the best fix.

[Main Memu]-->[System]-->[Preferences]-->[Appearance]-->Visual Effects Tab -- > select 'None'.

No more resize or other delays. Scrolling is back to what one would expect.

---

### Post by daqron on 2010-05-15
Had this problem on an HP 6930p (ATI video card) running Lucid. I couldn't figure out how to get the no-backfills PPA to install under Lucid, but was able to resolve the problem by removing the ATI proprietary driver. Seems the open source driver works just fine and the resize delay is gone.

---

