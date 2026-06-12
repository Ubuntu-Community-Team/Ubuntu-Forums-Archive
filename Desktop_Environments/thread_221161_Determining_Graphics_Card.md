---
title: "Determining Graphics Card"
date: 2006-07-22
forum: Desktop Environments
---

### Post by panrubius on 2006-07-22
Hi,

I have just switched to Ubuntu from the dark side and I'm loving it. I have the installation pretty much how I want it and everything is going well.

Over the past few  weeks I've been reading about XGL & Compiz and thought I'd give it a try. Therein lies the rub:

Is there a way of determining what type of graphics card one has without opening the box?


Thanks

---

### Post by taurus on 2006-07-22
This command probably will tell you...

```

sudo lspci

```

---

### Post by jhaxxis on 2006-07-22
go to a terminal and type   lspci
You'll get a list of your devices ... including your vga compatible controller

---

### Post by panrubius on 2006-07-22
Excellent, Thank you.

I don't suppose you know if I can install Xgl & Compiz on this hardware, do you?

---

### Post by panrubius on 2006-07-22
Cheers

---

### Post by taurus on 2006-07-22
> **panrubius said:**
> Excellent, Thank you.

I don't suppose you know if I can install Xgl & Compiz on this hardware, do you?
On what hardware???  I have no idea what graphic card do you have!

---

### Post by panrubius on 2006-07-22
Sorry, I'm such an idiot!

The graphics card is a:

Matrox Graphics, Inc. G400/G450 (rev 85)

---

### Post by adam.tropics on 2006-07-22
I don't believe a Matrox will run it yet. Apparrently, it may do later. That said, I have heard of other cards, that 'will not run it' turning out to run it just fine, so provided you are able to get DRI without xgl/compiz, then I suppose you could give it a try. I might suggest just making sure you are a little comfortable with the command line, and the directory struture before you dive right in, as you may need to do some backstepping if something goes wrong, without a nice gui to help! Also, provided you're not on a laptop, a known working card needn't be a top of the line expensive little number. Some pretty low-spec (read::cheap) cards are known to be fine. Have a read around [http://www.compiz.net](http://www.compiz.net)

---

### Post by panrubius on 2006-07-22
Thanks for the help, I shall go off and do some investigating.

---

