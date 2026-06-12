---
title: "sdhc with bad blocks..."
date: 2009-03-29
forum: General Help
---

### Post by ram100987 on 2009-03-29
I have an 8gb micro sdhc that I've been using in my htc G1 phone.  I was having an issue with it not reading the pictures that were on it so I tried ejecting the card and reinserting it a couple time which usually fixed the problem.  Well it would not fix itself.  At first it would show place holders for all the pics it just wouldn't show the pics.  Well now it won't even load the placeholders.  I just keeps saying loading whenever I try to access the card on the phone.  So I decided to take the card and put in the laptop and see if I could accomplish anything.  Well it wouldn't seem to mount.  after a couple tries it seemed to mount but it most of the content that was on the card was no longer being shown.  I tried checking it with several different programs to see if there was an error on the card.  When running fsck on it it said there was an issue with the superblock and that I should try a different superblock, and I tried that and it kept giving the same error.  I tried to format it with mkfs and it told me that the card had bad block and it would not format it. 

So....  is there a way to repair this or is the card fried now?  It would be nice if I could get the content back but I would be satisfied to simply get the card working again.

---

### Post by sdennie on 2009-03-29
How many pictures have you taken with the card and what else have you usen it for?  Those cards are like SSD drives and have limited numbers of writes.  I've never experienced the behavior you are describing with an SD card but, if I did, I'd immediately assume that I'd simply worn it out with writes.

---

