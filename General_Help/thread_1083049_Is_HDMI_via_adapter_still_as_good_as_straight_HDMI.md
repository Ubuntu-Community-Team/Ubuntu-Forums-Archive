---
title: "Is HDMI via adapter still as good as straight HDMI?"
date: 2009-02-28
forum: General Help
---

### Post by PsychedelicWonders on 2009-02-28
I need to get another dual video card, but this one needs to have a HDMI port along with a DVI.

Now there are not many in my specs and price range that offer just a straight HDMI port.

I mostly see them just offer HMDI's with adapter setups.

How good are those compared to just a straight HDMI port?

This HMDI port will be connected to a 46" Samsung 750.

The only one Ive seen that offers a straight HDMI port that fits in with the rest of the specs I'm looking for is this one:

This one made by a company called Galaxy:

[http://www.newegg.com/Product/Produc...82E16814162020](http://www.newegg.com/Product/Produc...82E16814162020)

How is that company?

That was really the only one that I found that had all the specs I was looking for:

HDMI port
DVI port
Power port for addtional power
Around my $125 price range
nVidia

But, I've never heard of that company.

How is it?

There are a bunch of other cards that will do HDMI via an adapter, but how is the quality compared to straight HDMI?

I am looking for both video and sound via HDMI.

---

### Post by issih on 2009-02-28
As far as the video quality goes I'd expect there to be no difference whatsoever, as both protocols are entirely digital. The main difference between the two is that hdmi is designed to carry sound as well as video, ans also to allow hdcp.

A straight dvi-hdmi adaptor will not have any capability to carry sound in that cable, and you will need to have a tv that can cope by allowing sound input from another source (the sony I have played with seems incapable of achieving this, but I've seen reports of others managing it with various brands)

Some video cards with direct hdmi out do loop the sound through into the cable, others don't. Its something worth investigating.

Hope that helps

<for me that link goes to a broken page, so I can't comment on the card you mentioned, sorry :()

---

### Post by PsychedelicWonders on 2009-02-28
I do want sound and video via the HDMI

So youre saying that I MUST have an actual HDMI port in order to do both?

These adapters wont cut it for adding sound?

Sorry here is the link:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16814162020](http://www.newegg.com/Product/Product.aspx?Item=N82E16814162020)

---

### Post by issih on 2009-02-28
After a bit of research it looks like most newer ati chipsets (hd4xxx series I think) and some of the newer nvidia ones can do it, but you need to use their own supplied dvi to hdmi adapters, the generic ones wont't cut it. 

In the case of nvidia you have to link the sound hardware into the video card using an internal cable. The ati ones have a little sound chip built into the graphics card so they avoid that.

All in all its a bloody minefield, and I can't find any really good sites that cover what cards do what.

Unfortunately I can't find any info about that card you are interested in either, the closest I got was someone asking if it could do audio out on the hdmi port, with no answer.

So all in all I don't know...sorry

<edit>..This page:
[http://www.bit-tech.net/hardware/graphics/2008/02/21/g94_nvidia_geforce_9600_gt_graphics_card/4](http://www.bit-tech.net/hardware/graphics/2008/02/21/g94_nvidia_geforce_9600_gt_graphics_card/4)

says that some 9600 gts do have an spdif audio passthrough. whether your one does I don't know for sure.. but it is listed as coming with an spdiff cable, so the chances are good :)

---

### Post by thinking2loud on 2009-02-28
All the required physical signals for sound are present in the DVI and HDMI connectors, if you want the TMDS encoded sound.  Just about any adapter will work.  The challenge will be in getting the audio to the graphics card so that it gets encoded along with the video data stream.

However, adapters are a signal-integrity pain in the posterior.  Each one is the equivalent of 1-2 meters of cable in terms of loss.  If you intend to operate at a very high clock rate, it may be 'exciting'.

---

### Post by PsychedelicWonders on 2009-02-28
Ok after not having to worry about getting an expensive HDMI adapter card

Its between these two:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16814127382](http://www.newegg.com/Product/Product.aspx?Item=N82E16814127382)

or 

[http://www.newegg.com/Product/Product.aspx?Item=N82E16814121268](http://www.newegg.com/Product/Product.aspx?Item=N82E16814121268)

What do you guys think?

The Asus has better reviews, but is $40 more.

My other dual card is an Asus, is it a good idea for the drivers to try and run the same card for smoothest play across 4 monitors? (one of which is a 46" samsung lcd)

Both have all specs and got pretty good reviews.

---

### Post by issih on 2009-03-01
As I said earlier, dvi has NEVER as a standard been set up to carry audio. nvidia and ati have set up their own proprietary workarounds to allow sound pass through in order to support hdmi properly, but in both cases you will need to use their own proprietary adapters in order to get the sound to work.

a normal dvi port on a bog standard video card has nothing to do with sound whatsoever, it is only because more recent cards are catering to people wanting to use hdmi that this has been kludged in. As an indication of how recent this change is, my just over a year old macbook is incapable of outputting sound from its dvi port..its a pita.

nvidia cards as you said need to use a cable to link in, ati apparently have sound hardware built into the graphics card.

To that end I'd say that as both those are 2 dvi out cards, you will probably need to source another proprietary adapter if you want to use 2 * hdmi.

Asus is generally considered better quality than msi, but I will note that the asus 6800 I have in one of my boxes has been quite flaky, and irritatingly uses software to do automatic fan control (which of course there is only a windows version of), that took a while to sort out.

I won't comment on the actual cards prowess, as I'm out of the loop a bit there

---

### Post by Amorphous_Snake on 2009-03-01
I have a Radeon 4870 on one of my systems and I can confirm that it runs audio through DVI via the supplied adapter. But I have not tried it in Linux.

As far as card recommendations, why not a Radeon 4670? It's cheap and quite capable.

---

