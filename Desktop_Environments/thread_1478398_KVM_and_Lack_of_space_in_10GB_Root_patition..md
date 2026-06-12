---
title: "KVM and Lack of space in 10GB Root patition."
date: 2010-05-09
forum: Desktop Environments
---

### Post by SilverWave on 2010-05-09
Hi Guys.

Using AQEMU to create some quick VM images for testing

Lucid amd64 and i386
Karmic amd64 and i386

So 4 images, I have 8GB of RAM so I set each off with 1GB.

I get to the 4th image and I am informed that I have no space left on / (root).

Checked and I should have 4GB free of 10GB, but down to my last 500MB!

I kill all the VM's and sure enough I now have 4GB free again.

Questions:
What's going on?
Obviously there are some temp files being generated?

Why would they be created on / ?

What are they called and what is their location?

How do I configure KVM to put them elsewhere?

Cheers :-)

___

Note for Moderator: The Thread Title needs the word "patition" corrected to "partition" Cheers :-)

---

