---
title: "WoW almost there, help please"
date: 2006-10-14
forum: Gaming &amp; Leisure
---

### Post by ImplicitProcrastination on 2006-10-14
After a mindblowing South Park, lots of peer pressure, and learning of a special version of wine written specifically for WoW (lol) I finally broke down and installed the World... of Warcraft.

And it works! Almost.

It runs really well, and I was really excited about it until I tried to walk into a tunnel. It turns out that anytime you go into somewhere narrow like a house or a mine or a building of any kind, the graphics go all haywire and there are like these lines that form what kind wanna be 3d and when text comes on the screen after exiting the narrow place it just crashes! Also when I enter a narrow place my map goes all white.

I thought it was a graphics card problem so I followed the instructions in a tutorial for configuring xorg-driver-fglrx but that only made it worse. So i reverted it back to normal. glxgears looks beautiful, I can't figure out the problem.

I've noticed that I'm using the unaccelerated mesa video drivers and am getting a decent (650ish) FPS with glxgears, when I tried to install the ATI ones it made it worse.

Could it be that my video card just hasn't got the balls? It's an ATI Radeon 9100 I think. I've tried scaling down the graphics but to no avail.

Somebody help me! I'd hate to have purchased warcraft time for nothing.

I tried installing the proprietary drivers available on the ATI website, it only made everything slower. After toying with it I've become convinced that my graphics card isn't operating properly. This is fine if I can come up with a reason other than this that warcraft isn't working.

---

### Post by Ferrat on 2006-10-14
Install hardware acc, wow wont run with out it, did you run wow with the 

wine wow.exe -opengl   ??

Do you have the lastest version of Wine? 0.9.22 or 0.9.23

did you do the regedit fix? =) 

Check out this for the best help on how to make it work =)
[http://appdb.winehq.org/appview.php?iVersionId=5606](http://appdb.winehq.org/appview.php?iVersionId=5606)

---

### Post by ImplicitProcrastination on 2006-10-15
i ran it with opengl,

i upgraded wine when u told me there was a newer one

i tried the regedit fix, although I was confused because in hkey_local_machine I didn't have wine in the software category, so i stuck it in the the one which did have it, which I think was hkey_local or something.

it made the crash more immediate

---

### Post by ImplicitProcrastination on 2006-10-15
Holy crap! I followed the instructions precisely creating my own wine key and taking out the other and now the only things that happens is i get a white box which isnt that bad so woo hoo! Thanks dude.

---

### Post by Ferrat on 2006-10-15
> **ImplicitProcrastination said:**
> i ran it with opengl,

i upgraded wine when u told me there was a newer one

i tried the regedit fix, although I was confused because in hkey_local_machine I didn't have wine in the software category, so i stuck it in the the one which did have it, which I think was hkey_local or something.

it made the crash more immediate

You shouldn't place that anywhere else then where is says, sounds like you need to remove all the settings of wine and start over, inserting that value where it shouldn't be then I guess you removed it so there is no value where there should be one. 

just start over and try again but this time don't put the regedit value anywhere else than where it says and do nothing else then it should work.

---

### Post by Ferrat on 2006-10-15
> **ImplicitProcrastination said:**
> Holy crap! I followed the instructions precisely creating my own wine key and taking out the other and now the only things that happens is i get a white box which isnt that bad so woo hoo! Thanks dude.

a white box where? or just a white box?

---

### Post by ImplicitProcrastination on 2006-10-15
A white box.. lol, I'm retarted.

What I meant to say was my radar becomes white.

---

### Post by Ferrat on 2006-10-15
> **ImplicitProcrastination said:**
> A white box.. lol, I'm retarted.

What I meant to say was my radar becomes white.

Ahh yeah that's a know problem with ATi cards, no fix yet =/ but not the worst thing in the world =)

---

### Post by ImplicitProcrastination on 2006-10-15
thanks for the link

---

### Post by Ferrat on 2006-10-15
np that's what the forum is for =)

---

