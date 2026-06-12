---
title: "Gutsy, ATI, &amp; Compiz"
date: 2007-11-01
forum: Desktop Effects &amp; Customization
---

### Post by angelogladding on 2007-11-01
So when I booted up the first time post-install I had out-of-the-box Compiz support however I received the notification that my ATI proprietary drivers were yet to be downloaded & installed. I install the ATI drivers and upon reboot I no longer have Compiz enabled.

Is *System > Preferences > Appearance > Visual Effects* the only interface to Compiz?!? This window & tab shows *"**None:** Provides a simple desktop environment without any effects."* to be selected. When I attempt to select *"**Extra:** Provides more aesthetically pleasing set of effects. Requires faster graphics-card."* I receive an error dialog stating *"The Composite extension is not available."*

Lastly, does the default Compiz come with the Cube feature and other advanced options?

Thanks,
Angelo

---

### Post by Prospero2006 on 2007-11-01
ATI- Drivers:

-The most recent ati driver is 8.42
However, depending on your card, you may want to use one of the earlier ones. 
I have a middle school computer lab and the 8.39 driver is the only one that 
works with the ati the district has packed on out optiplex 620's. So, the most recent driver won't necessarily be the best choice.

[http://ubuntuforums.org/showthread.php?t=575843](http://ubuntuforums.org/showthread.php?t=575843)

That thread talks about how to download, unpack and install.

Compiz extras:
Once you get the compiz working,you'll want to do:
sudo apt-get install compizconfig-settings-manager
sudo apt-get install compiz-fusion-plugins-extra

That should enable everything, although I can't figure out how to make window spacing work.

Pros

---

### Post by angelogladding on 2007-11-02
Thanks for that info but here's the thing. Last week I pushed 7.10 to a Feisty install and the new drivers worked fine with Compiz and my Radeon Mobility 9600.

When I attempt to run `compiz` from the terminal I receive:

```
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity
```

Must I load an Xgl script session? I'm not quite sure what that does but I've seen it before.. I'm trying to make a connection here somehow. Anyone know about whitelisting an ATI driver for Compiz?

---

### Post by Forlong on 2007-11-02
See the last step [here](http://forlong.blogage.de/article/2007/10/23/fglrx-8423---finally-with-AIGLX-support).

But I recommend using the open radeon driver with your card (you did, in fact, on first boot).

---

### Post by angelogladding on 2007-11-02
Hmm.. I just logged in to post that I got things working again by simply installing the missing xgl:

```
sudo apt-get remove xserver-xgl
```

> But I recommend using the open radeon driver with your card (you did, in fact, on first boot).

Good thing to know but can you comment on why you feel the open radeon is a better choice?

---

### Post by Forlong on 2007-11-02
> **angelogladding said:**
> Hmm.. I just logged in to post that I got things working again by simply installing the missing xgl
Ah, OK... I thought you followed Prospero2006's advice and installed the latest one.
> **angelogladding said:**
> Good thing to know but can you comment on why you feel the open radeon is a better choice?
Because it works very well with Compiz and doesn't require Xgl.
If you are fine with Xgl, stick to it.

---

