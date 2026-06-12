---
title: "best way to do &quot;mac&quot; style in Ubuntu?"
date: 2012-11-23
forum: Desktop Environments
---

### Post by ELD on 2012-11-23
So I am looking to find the best way to have a bottom dock and top bar.

Anyone know the best way to do it and what the most up to date dock currently is as i hear AWN isn't supported anymore.

---

### Post by cwsnyder on 2012-11-23
AWN dock, Cairo dock, Conky dock, Wbar dock are all options for lower docks, as for which will be the best one for your taste, I don't know.  I run Xfce with wbar.

---

### Post by Frogs Hair on 2012-11-23
Cairo Dock is the closest to looking like a Mac dock that I have used. Gnome Classic, or Xubuntu may be the best DEs to use. 

Here is a theme that works with 12.04 . [http://gnome-look.org/content/show.php/Adwaita+Cupertino?content=147061](http://gnome-look.org/content/show.php/Adwaita+Cupertino?content=147061)

---

### Post by ugm6hr on 2012-11-24
Although currently in beta, Pantheon DE is worth considering.

Elementary OS Luna is basically Ubuntu 12.04 + Pantheon if you want to check it out in a LiveUSB/CD. I've been using it for a few hours on my netbook, and like it a lot.

---

### Post by cwsnyder on 2012-11-24
If we are bringing in non-Ubuntu OSs, look at Pear Linux, [http://pearlinux.fr/download/](http://pearlinux.fr/download/) a french-based GNOME 3.x Linux base which has been tweaked to look a lot like Mac OS X.

---

### Post by offgridguy on 2013-01-31
> **cwsnyder said:**
> if we are bringing in non-ubuntu oss, look at pear linux, [http://pearlinux.fr/download/](http://pearlinux.fr/download/) a french-based gnome 3.x linux base which has been tweaked to look a lot like mac os x.
+1

---

### Post by markbl on 2013-01-31
> **ELD said:**
> So I am looking to find the best way to have a bottom dock and top bar.

I use a Mac (MBA) also but I don't understand why anybody would want the dock at the bottom rather than the side on a widescreen monitor where vertical screen space is tight, horizontal screen space is not. I have my dock configured on the left side on my Mac, i.e. just like Unity and Gnome shell.

---

### Post by P4man on 2013-03-27
> **ugm6hr said:**
> Although currently in beta, Pantheon DE is worth considering.

Elementary OS Luna is basically Ubuntu 12.04 + Pantheon if you want to check it out in a LiveUSB/CD. I've been using it for a few hours on my netbook, and like it a lot.

+1

I only discovered Elementary OS a few days ago, but Im absolutely loving it.  
It looks very polished; the UI doesnt get in the way and isnt "in your face", and it actually works pretty damn well. It combines the best features of Gnome3, unity and Mac.

I was getting desperate finding a replacement for ubuntu, but it looks like I found it now! A screenshot does it no justic (app and workspace switching is awesome), but here is one anyway

[[IMG]http://storage9.static.itmages.com/i/13/0327/s_1364387779_4976393_a7c502ac0f.png[/IMG]]("http://storage9.static.itmages.com/i/13/0327/h_1364387779_4976393_a7c502ac0f.png")

---

### Post by ugm6hr on 2013-03-30
> **P4man said:**
> +1

I only discovered Elementary OS a few days ago, but Im absolutely loving it.  


I remain a fan... But be warned: Pantheon interferes with other DEs, so it can be troublesome if installed on top of another Ubuntu / derivative OS (from personal experience).
If you want to try it, do it from the Elementary OS beta ISO directly...

---

### Post by P4man on 2013-04-24
> **ugm6hr said:**
> 
I remain a fan... But be warned: Pantheon interferes with other DEs, so it can be troublesome if installed on top of another Ubuntu / derivative OS (from personal experience).
If you want to try it, do it from the Elementary OS beta ISO directly...

Been using it for several weeks now; Im no longer as big a fan as I was initially. It still looks great, and I realize its in beta, but too many things are still quite wrong with it:

- geary(mail client) is hopeless for now. Massive memory leaks, lacking even the most basic features like search, storing of drafts, spell check etc. Yes it does look fairly good but its not usable. The author wants to raise $100K for further developing it:
[http://www.indiegogo.com/projects/geary-a-beautiful-modern-open-source-email-client](http://www.indiegogo.com/projects/geary-a-beautiful-modern-open-source-email-client)
Cant argue against opensource devs using crowdfunding to support them, I realize they have to eat too, but given the state of the app and their call to glory being Shotwell, which I happen to think is another horribly designed app, I am not too excited about this. Fortunately you can just install thunderbird.
- for some reason firefox seems to be leaking lots of memory too. I havent noticed this on other OS's, certainly not to this extent. 
- Pantheon (file manager) is still way too buggy, particularly when accessing network resources or removable storage. Had to install nautilus. Pantheon does hold promise though, if the fix the bugs its actually a nice improvement over nautilus.
- Noise (music player) is sorely missing in features too. Wont even do network streaming of internet radio. Radiotray FTW.
- Printing. Where are the printer settings? I can only configure users. Had to do the rest through cups web interface.

In short; after replacing all the unusable apps with usable ones, it almost feels as using ubuntu with a nicer theme and launchers, less features and more bugs. To make matters worse development seems to be slow. Shame. It has potential. I just wished they would settle on more usable apps for the time being, and just like Mint started out, focus on the things they do get right, like the desktop environment which is perhaps the best and slickest Ive used to date.

---

### Post by gnugen on 2013-04-24
I have configured the Cinnamon desktop environment to look like Mac OS X. 

First, you have to get the Cinnamon desktop and Cairo Dock. Cairo Dock is already in the Ubuntu Software Centre, so you can get it from there. 

To get cinnamon, open a terminal and type in these commands:

```
sudo add-apt-repository ppa:gwendal-lebihan-dev/cinnamon-stable
sudo apt-get update
sudo apt-get install cinnamon
```
 
Then log out and log back into Cinnamon. Open Cinnamon Settings, go to Panel Settings and there will be a option ot make the panel go to the top. There is also a Windows setting manager, where you can move your window controls to the left in the desired order that they should appear. Get the Mac OS X Theme for Ubuntu from Noobslab.com and install it. Activate Cairo Dock and get any themes you want from the Cinnamon Spices website and you will have a Mac OS X lookalike(with a start menu).

I use 12.10.

---

### Post by eric-yorba on 2013-04-24
> **P4man said:**
> - geary(mail client) is hopeless for now. Massive memory leaks, lacking even the most basic features like search, storing of drafts, spell check etc.

Have you reported these memory leaks you're seeing?  We're not aware of any serious leaks in 0.3.1, though Vala versions prior to 0.20 do have a nasty habit of introducing leaks in certain cases.  Bear in mind that if nobody reports a bug, we can't fix it.

Also, Geary has had a rather limited spell check for some time.  Until recently WebKitGtk didn't support much in the way of spell checking, but (assuming Yorba is somehow still around next year) we should be able to bring a much better spell checking experience once WebKitGtk2 is more widely available.

---

### Post by P4man on 2013-04-24
> **eric-yorba said:**
> Have you reported these memory leaks you're seeing?  We're not aware of any serious leaks in 0.3.1, 

Im using 0.3.1 now, but Im not sure what version I had last week. Right now memory usage looks quite good.
I have not reported those issues, I kicked geary's tires and decided it wasnt for me, at least yet.

> Also, Geary has had a rather limited spell check for some time.  Until recently WebKitGtk didn't support much in the way of spell checking, but (assuming Yorba is somehow still around next year) we should be able to bring a much better spell checking experience once WebKitGtk2 is more widely available.

Yeah, well it underlines typo's, but doesnt offer corrections, but Im sure you are aware. 

Anyway, I didnt want to diss your work, but I think you will agree that at this stage its hardly ready for daily use - except if you only read mails as they come in. And that goes for (too) many apps in Elementary OS. I fear the devs may have bitten off more than they can chew. If they had followed an approach closer to what Mint did, which was initially pretty much a straight ubuntu fork with very common user apps and just a few UI tweaks, it would probably draw more users, and therefore developers, allowing them to divert further over time. But hey, maybe Ill be proven wrong, I sure hope so.

---

### Post by eric-yorba on 2013-04-24
> **P4man said:**
> Anyway, I didnt want to diss your work, but I think you will agree that at this stage its hardly ready for daily use - except if you only read mails as they come in.

Well yeah, it's not a 1.0 by any means! Hopefully we'll be around long enough to deliver a solid 1.0 release, but as we've all seen that's rare in the open source world.

---

### Post by ugm6hr on 2013-04-25
> **eric-yorba said:**
> Well yeah, it's not a 1.0 by any means! Hopefully we'll be around long enough to deliver a solid 1.0 release, but as we've all seen that's rare in the open source world.

I'm hoping so too... I've installed Elementary on my Netbook and subsequently put Pantheon on top of Ubuntu on my main computer (which was a bit of a struggle)... Wouldn't want to have to take a step back!

There is definitely room for improvement: my personal issues are that Files struggles with network shares mounted by Gigolo, and has no bookmarking feature, so have to have Nautilus installed as a backup. I love the Gala / Plank / Wingpanel combination for workflows and desktops, and find that no other DE has similar features which work well on my lowly netbook.

Good work.

---

