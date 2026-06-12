---
title: "unable to install from live cd: x server error"
date: 2007-06-06
forum: Dell  Ubuntu Support
---

### Post by anonymousT on 2007-06-06
I have an (notebook) inspiron 6400 aka e1505 and I was trying to install feisty on it
when i tried to boot ubuntu so that I can install it it stopped because of an error of the x server
and there's a short description which says "no screen found"
I do have a wide screen and an ati graphics card (x1400) but I think I checked and the driver is available for linux

any help would be appreciated, thx

---

### Post by Ek0nomik on 2007-06-06
I have an ATI Mobility Radeon X1400 and Ubuntu Edgy Eft (6.10) installed fine with the Live CD, however Feisty Fawn (7.04) has some issues with ATI cards.

I would burn the Alternate CD and install Ubuntu this way.  That way you don't need the X server to properly work, at least not yet.

The text based installer is just as easy to use in comparison to the Live CD.

Once you have it installed, you should be able to boot to a command line interface, and install the ATI drivers by following this:

[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

---

### Post by anonymousT on 2007-06-06
hi, thanks for the quick reply
I'm not sure what you mean by the alternate CD and i can't find the menu to get to the text installer

and another question, the text installer should include a partition tool right? because i need to repartition the hard drive
and also since you have an e1505 i'm guessing it comes with 'dell media direct' as long as i don't touch that partition it should still work right?

---

### Post by Ek0nomik on 2007-06-06
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

See the green box with the white arrow that says:  "Start Download"?  Below that there is a check box that will allow you to download the Alternate CD rather than the Live CD.

The Alternate CD does include a partitioner that is correct.  I didn't buy my Dell with Ubuntu installed, I have been using Ubuntu before Dell started the offering.  I don't really know how they are setting up their partitions these days.  I personally only have an ext3 and swap partition on my computer.  I wouldn't want any other partitions.

What is Dell Media Direct in relation to Ubuntu?  In Windows it controls the Media Player I think so you can play music and video, but even that I find a bit useless.

Again, just reply if you need any more help or have any other questions.  :)

---

### Post by anonymousT on 2007-06-07
ok, thx a lot, that worked

---

