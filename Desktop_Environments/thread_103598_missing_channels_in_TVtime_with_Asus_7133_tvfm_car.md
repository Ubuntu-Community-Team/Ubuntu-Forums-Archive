---
title: "missing channels in TVtime with Asus 7133 tv/fm card."
date: 2005-12-14
forum: Desktop Environments
---

### Post by 0okami on 2005-12-14
*****EDIT*** moderator, could you please move this to the "hardware help" forums? thanks.** 


Has anyone had this or similar issue where they are missing TV channels that they know to exist? 

Im missing channel 28, 53 and few others. 
Come to think of it, I only get 3 working channels. 
I can dial in the missing channels, but there is no signal. Auto scanning for channels works... but the channels are still missing. I cant see them even if i fine tune. 

Now, If i boot into windows, i can get the channel just fine

Im thinking maybe my asus 7133 tv/fm card is not configured right. But I dont know how to troubleshoot misconfigured devices yet. I read a few posts about changing drivers and all, but im fairly new and the information seems to be missing vital first steps (for new users) .

lspci returns this:
```
 
0000:01:07.0 Multimedia controller: Philips Semiconductors SAA7133 Audio+video broadcast decoder (rev 10)

```

here is a picture of the card im using: 
[http://www.bttv-gallery.de/pict0002.jpg-asus-tv-fm-card_a.jpg](http://www.bttv-gallery.de/pict0002.jpg-asus-tv-fm-card_a.jpg)
my card is ntsc not pal as shown... 

So im puzzled... 
help?

or if someone could tell me how to get every piece of information needed out of a pci device...? that might help me help my self.

---

### Post by ZarathustraDK on 2006-01-13
Hey I got the same problem as you (plus my sound isn't working).

I got a  Philips Semiconductors SAA7134 Video Broadcast Decoder.

The problem is quite identical to yours : only a fraction of the channels are found (at my box I only have channels like DR1 (danish, very blurry) TV2 (danish), NDK (German), NK1 (Norwegian) and a channel-overview (where, to ones discontent, can see that there are other channels available somehow; anyway there should be a lot more like Discovery, CNN, BBC and the likes).

Is it the tuner-number that is wrong? How do I (we) change it? Is there any other way to scan for channels?

---

### Post by ZarathustraDK on 2006-01-13
Hey again, I think I got it.

I did :

> tvtime-configure --norm=pal --frequencies=europe

And then I got access to all the channels I'm used to with Medion Power Cinema under Windows. Of course you'd have to change the "pal" and "europe"-parts if you don't live there, but that's what did it for my part. Got the info by mindlessly stumbling across it at [http://tvtime.sourceforge.net/usage.html](http://tvtime.sourceforge.net/usage.html) , and thinking "oh what the heck, maybe that'll work". :-D

Now I just need to get the darn sound working and then I'll be one happy man! Any suggestions on what to do if the sound doesn't work? Tried unmuting everything, didn't work...

---

