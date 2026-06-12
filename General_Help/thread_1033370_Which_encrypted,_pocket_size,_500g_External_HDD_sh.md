---
title: "Which encrypted, pocket size, 500g External HDD should I get?"
date: 2009-01-07
forum: General Help
---

### Post by PsychedelicWonders on 2009-01-07
Alright I need to get an external HDD to use as backup and easy grab n' go in case of an emergency (house fire, robbery whatever)

Now I am also looking for a external drive that is encrypted to keep all of my info as secure as possible.

I've found this and really like it...

[http://www.newegg.com/Product/Product.aspx?Item=N82E16822144486](http://www.newegg.com/Product/Product.aspx?Item=N82E16822144486)

supposed to be top tier for data encryption.

Couple of questions about that particular drive...

right now my internal drive is 500g... that external is 320... am I able to back up a 500g to a 320g?

Or does the drive space have to match exactly?

Technically I have no where near 500g or even 320... so all of my info will def fit... i just dont know if the drives have to mirror exact same size to do a proper backup?

Also, in the reviews of that drive, someone mentions this isnt compatible with unix?

Could this be true?

What would stop this drive from not working with ubuntu?

If this drive does not work with Ubuntu, are there any other drives of similar specs out there (physical size & data encryption) that will work with ease in ubuntu?

thanks.

---

### Post by hyper_ch on 2009-01-07
if you want to mirror, they should be at least of equal size... if you just want to backup files, the total size of the files you want to backup must be lower...

You can get any external drive and fully encrypt it with luks/dm-crypt.

---

### Post by PsychedelicWonders on 2009-01-07
So what is the difference in the encryption this particular drive offers compared to the encryption you can put on any external via luks/dm-crypt?

Also, someone left a review for that particular hdd that "you MUST have a powered USB port. If you do not it will just sit there and wine like a sad puppy. But fear not! Newegg has a lot of USB hubs that are powered and are inexpensive as well. This will sove your power problem"

Are all externals like this?

How do I know if my USB ports are powered?

I def want this to be "on" all the time so it can do auto back ups at scheduled times.

What are my options now?

---

### Post by hyper_ch on 2009-01-07
no clue what encryption is on there but one says it not compatible with unix and mac (and also neither with linux).

as said, I'd go with any external hd and encrypt it with luks/dm-crypt.

---

### Post by PsychedelicWonders on 2009-01-07
So what is the difference in the encryption this particular drive offers compared to the encryption you can put on any external via luks/dm-crypt?

Also, someone left a review for that particular hdd that "you MUST have a powered USB port. If you do not it will just sit there and wine like a sad puppy. But fear not! Newegg has a lot of USB hubs that are powered and are inexpensive as well. This will sove your power problem"

Are all externals like this?

How do I know if my USB ports are powered?

I def want this to be "on" all the time so it can do auto back ups at scheduled times.

What are my options now?

---

### Post by PsychedelicWonders on 2009-01-07
after reading more about that one it says this...

With the BlackArmor unit, you either have access to your files, or if the security measures are breached (password not know, format or data retrieval attempt), you will then have an inoperable (locked) permanently wiped out hard drive (paper weight). It's that simple. If that's the type of protection you want, this is the drive for you.


something I do NOT want to have happen.

i doubt I will forget my password... but in any case that I do... I do NOT want the drive wiped completely.

Would this be the case for the luks/dm-crypt option on a regular external?

How secure is this luks/dm-crypt?

---

### Post by hyper_ch on 2009-01-07
If you forget your passwords or lose your key (you can setup multiple password/keys to unlock the drive) you just can't access your data.

[http://en.wikipedia.org/wiki/LUKS](http://en.wikipedia.org/wiki/LUKS)
[http://en.wikipedia.org/wiki/dm-crypt](http://en.wikipedia.org/wiki/dm-crypt)

---

### Post by PsychedelicWonders on 2009-01-23
So any suggestions on which one I should get?

I want to order in the next week or so.

thanks.

What specs should I be looking for?

What are some good small external HDD companies?

---

### Post by niteshifter on 2009-01-23
Hi,

I recently purchased a Western Digital MyBook 640G for $100 and:
1. Dumped the windows and mac software that came on it to a tarball (should I choose to get rid of it).
2. Let Truecrypt have at it, with an internal format of ext3. AES-Serpent encryption, SHA-512 hash, password and keyfiled. (Translation: doubly encrypted, no "key magic" exploits, it requires a password from me and a device mounted to the system that has an additional key in a file.)

Took about an hour for Truecrypt to do it's thing. I now have an archive drive that can be trusted - Truecrypt's code has been vetted by many eyes. Can't say the same about the maxtor unit. So what if it's AES? *The more important question and answer is was it implemented properly*? You'll never know the answer to that question.

Whereas with open-source solutions you already have the answer, be that Truecrypt (my favorite) or dm-crypt/luks.

The MyBook comes with a power supply, you don't need to have (or worry about) powered USB ports. But it's not pocket-sized, more like paperback book sized.

I've also did the same with a Western Digital Passport 250GB unit (that is pocket-sized) that I travel with, but it does require a powered USB port. Be aware some older machines (more than 5 years old) won't like the power needs of external drives.

---

### Post by PsychedelicWonders on 2009-01-29
I have a newly built computer, so I probably have a powered usb port.

I am def looking for the pocket size hdd.

but what other specs should I be looking for?

What companys should I look for?

i want to get this in the next couple of days...

---

### Post by PsychedelicWonders on 2009-01-30
bump

---

### Post by Neural oD on 2009-01-30
seagate has some wonderful drives - have a look at those - don't worry about ones with encryption - you could always put your own on - look at truecrypt -for crossplatform compatibility

---

### Post by PsychedelicWonders on 2009-01-30
> **Neural oD said:**
> seagate has some wonderful drives - have a look at those - don't worry about ones with encryption - you could always put your own on - look at truecrypt -for crossplatform compatibility

Ok so I'll go with Seagate

But what specs should I be looking for exactly?

I know I want 500g and one that is pocket size.

Beyond that, I am clueless.

I've budgeted $150 for this, but obviously if I can spend $100 I will.

What is truecrypt?  A program?

And when you say crossplatform compatibility, are you saying the encryption works on either ubuntu or windows?

---

### Post by jimv on 2009-01-30
Almost all USB ports are powered.  The last one that I saw that wasn't was the one on the end of an Apple keyboard long ago.

That said, any of the higher rated drives on this list would be fine:

[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010150414%201036007801%20131021357&bop=And&SrchInDesc=500gb&Page=1](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010150414%201036007801%20131021357&bop=And&SrchInDesc=500gb&Page=1)

---

### Post by PsychedelicWonders on 2009-01-30
> **jimv said:**
> Almost all USB ports are powered.  The last one that I saw that wasn't was the one on the end of an Apple keyboard long ago.

That said, any of the higher rated drives on this list would be fine:

[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010150414%201036007801%20131021357&bop=And&SrchInDesc=500gb&Page=1](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010150414%201036007801%20131021357&bop=And&SrchInDesc=500gb&Page=1)

Alright so I see the only specs really are:

USB 2.0 - I take it I want to make sure its 2.0?

Some mention 8mb cache, and some dont, do I want this? (I would assume so?)

And it says form factor 2.5 - that is the width?

---

### Post by jimv on 2009-01-30
> Alright so I see the only specs really are:

USB 2.0 - I take it I want to make sure its 2.0?

Some mention 8mb cache, and some dont, do I want this? (I would assume so?)

And it says form factor 2.5 - that is the width? 

You won't find one that's not USB 2, the cache isn't that important, and the form factor is 2.5 inches wide...which is basically like a laptop drive.  These smaller drives don't need to be plugged into separate power source.  Just plug it into you USB and go.

NOTE:  Some drives may require the use of TWO ports, so make sure you have at least two USB ports available on your computer.

---

### Post by PsychedelicWonders on 2009-01-30
> **jimv said:**
> And it says form factor 2.5 - that is the width? 

You won't find one that's not USB 2, the cache isn't that important, and the form factor is 2.5 inches wide...which is basically like a laptop drive.  These smaller drives don't need to be plugged into separate power source.  Just plug it into you USB and go.

NOTE:  Some drives may require the use of TWO ports, so make sure you have at least two USB ports available on your computer.

Even though I have 2 ports available, I dont want to have to have that option in case I travel.

What is the benefit of using 2 usb ports?

So realistically, most of these drives are pretty much all the same except for the case... 

So really just buy either a seagate or something big name with a case I like?

---

### Post by PsychedelicWonders on 2009-01-30
So the form factor 3.5 are the bigger, external ones?

If I want this thing to fit in my pocket... literally... do I need to stick with the 2.5 form factor?

---

### Post by PsychedelicWonders on 2009-01-30
if I have to go 2.5 form factor to stick in my pocket, I am going to get this one...

[http://www.newegg.com/Product/Product.aspx?Item=N82E16822136301](http://www.newegg.com/Product/Product.aspx?Item=N82E16822136301)

cant go wrong with the name, its 500g & black, everything I was looking for.

But seems the case is easily scratched...and if dropped breaks? 

**Are there any 2.5 form factor drives that are made from metal or a very durable plastic?**

would I notice the scratches less with the silver vs. the black?

Is there a 2.5 form factor external that wont break if you drop it?

looking for something "durable"

i really prefer a black case.

Would be nice if there was an LED status on the front instead of the back... but thats not a deal breaker.

Does anyone know of a similar 500g, black 2.5 form factor with an LED status light on the front?

---

### Post by PsychedelicWonders on 2009-01-30
Reading a con about that western digital...

Cons: Unit must be close to computer will not get enough power from a bus

That unit comes with a 1 foot cable... I would probably put a 3 foot blackberry usb cable, which is a very high quality cable.

Do you think I will run into not having enough power to the drive on a 3' blackberry cable?

I also plan on having this external always hooked up to the computer to act as a backup.. that isnt going to be an issue having it always plugged in will it?

i read a comment how it made their computer freeze and they lost a bunch of data?!

---

### Post by PsychedelicWonders on 2009-01-30
Would I want a case for it like this...

[http://www.newegg.com/Product/Product.aspx?Item=N82E16817193033](http://www.newegg.com/Product/Product.aspx?Item=N82E16817193033)

to help keep it safe & secure?

Would I want sata, or ide for this?

i'd really prefer to just buy one that is made of metal istead of having to buy a case...

---

### Post by jimv on 2009-01-31
I would go with the Western Digital Passport.  Other people who commented on Newegg didn't seem to have a problem using a longer cable.

---

### Post by PsychedelicWonders on 2009-01-31
I def like the western digital, but the case apparently is pretty fragile.

I'm looking for exactly what the western digital has to offer, but in a metal case.

Are there other companies out there that offer this with a metal case, yet use Western digital/seagate inside?

---

### Post by Gizenshya on 2009-01-31
just noticed this thread.  I posted some info on the other one

but you brought up some questions here as well...

the power issue...

This all depends on the drive and how much power it uses.  Drives that hog power will need either a double-USB dongle (one of which is ONLY for power.  it essentially doubles the amps available for the drive), or an external power source (an adapter, which should come with the case).  I've used many laptop drives in cases, and I've never had to use an external power adapter.  I've had to use the double-dongles a few times (always on laptops).

its safe to assume you'll have powered USB connectors.

2.5" hard drives are what are used in laptop computers.  They (obviously) have other uses now as well, such as small, portable storage ;)

SATA 2.5" hard drives use the same connectors as 3.5" SATA drives.  If you are good with your hands, or wouldn't mind a project, you could hook it up on the inside (with an adapter piece for the size, or just make one), or make a bay where you could stick it in, and remove it quickly if you need to.

SATA 2.5" drives work in SATA 3.5" drive cases as well. ;)

I wouldn't get an ide drive...

make sure the drive you get and case are both SATA compatible (preferably II).


umm... anything else you want to know?

ohh, and whatever the case, I strongly recommend that you don't get a "bundle" hard drive and case combo.  either the drive sucks, or the case sucks, or both.  To date I have never found an exception.

ohh, and also, if its a combo like that, you void any warranties if you open the case to do anything.

---

