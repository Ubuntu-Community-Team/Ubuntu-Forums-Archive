---
title: "Did ubuntu wreck my video card?"
date: 2008-12-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by AllisonM on 2008-12-27
I haven't had any response to [my query over on laptop hardware]("http://ubuntuforums.org/showthread.php?t=1018452&highlight=nvidia+d630"), and I'm wondering if it should have been posted here to begin with? 

Sorry for being so persistent with this, but this problem will make or break my Ubuntu allegiance, and I'd really like to come back into the fold!

---

### Post by armandh on 2008-12-27
my son broke a video card with fan clogging lint
heat will do that.

---

### Post by AllisonM on 2008-12-27
I know that heat will kill a video card, especially the defective Nvidia cards. But what are the chances that "lint" killed my card 24 hours after installing linux? I had no problems at all in Vista.

---

### Post by armandh on 2008-12-27
> **AllisonM said:**
> I know that heat will kill a video card, especially the defective Nvidia cards. But what are the chances that "lint" killed my card 24 hours after installing linux? I had no problems at all in Vista.

initial problem during playing a DVD
more enjoyment, more use, more heat! were I to offer a guess.
if dell is offering to send a tech to replace it; accept
their willingness to replace it suggests you are not the first.

my wife's Compaq V6000 laptop runs Ubuntu fine except the battery failed post warranty [$106] but I won't blame my wife.

if on the other hand you were one of many
such as I have seen in HDD failures from bad driver/bios match up........

---

### Post by sirebral on 2008-12-28
You said yourself your card has a high rate of failure.  I wouldn't blame the OS, any OS for that matter, concerning the failure of your card.  The problem is with your card.

You also said that you installed a different driver which affected the fan, thus inducing more heat.  Again, I would not blame the OS for the card failure but the driver.

For a definite answer, NO, Ubuntu did not wreck your video card.  It has a High Failure rate itself, and the fact that you installed a driver did not run the fan enough may have helped cause it's failure.

You might want to point out to DELL that the card you where issued has a high failure rate.  You might be able to get it replaced, and (I don't know) it might need to be recalled.

---

### Post by howefield on 2008-12-28
> **AllisonM said:**
> I haven't had any response to [my query over on laptop hardware]("http://ubuntuforums.org/showthread.php?t=1018452&highlight=nvidia+d630"), and I'm wondering if it should have been posted here to begin with? 

Sorry for being so persistent with this, but this problem will make or break my Ubuntu allegiance, and I'd really like to come back into the fold!

Lack of responses might be because no one else has had or seen the same problem. That should be good news, I think.  :)

---

### Post by AllisonM on 2008-12-28
That's a good point, howefield. 

So it does seem like the old (173) proprietary nvidia driver might have been the culprit. Now I'm in search of an alternative. Maybe the updated BIOS will take care of the heat problem on the 173 driver, or maybe there's a way I can run the 177 driver without going insane? (It pulses.)

I guess it's going to be tough for any of you to guess the best solution until my laptop is up and running again. Some trial and error may be called for. In the meantime, is there a good temperature monitoring utility that will pick up my GPU temp on an Nvidia Quadro NVS 135M?

---

### Post by sirebral on 2008-12-28
Nvidia provides a driver for your video card: [http://www.nvidia.com/object/linux_display_ia32_100.14.09.html](http://www.nvidia.com/object/linux_display_ia32_100.14.09.html)

Is that the driver you are using?

---

### Post by AllisonM on 2008-12-28
For anyone else with this problem: I finally found users with similar issues [over here]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/280805"). A few posts in the thread mention Dell D630s with my graphics card. 

No one else had their video card fail, but apparently the newer 177 driver doesn't pulse the fan after a BIOS update. Once my graphics card is replaced, I'll try that and report back. I'd still like to keep a close eye on my GPU temp from now on though, so utility recommendations still gratefully accepted.

---

### Post by AllisonM on 2008-12-28
Sirebral: The driver I was using originally was the one recommended by the Hardy Heron driver manager, labeled "177". When it ran really strangely (pulsing and loud, even when my computer was quite cool) I downgraded to the other driver in driver manager, labeled "173". I'm not sure how those correspond to the drivers on Nvidia's website.

---

### Post by sirebral on 2008-12-28
I am not sure either.  The one that I saw is version 100, so maybe you have a newer version. But the ones on the Nvidia site are definitely from NVidia.

---

### Post by AllisonM on 2008-12-28
One other thing, for anyone joining us mid-stream - there is a widely documented problem with, as far as I can tell, all Nvidia cards in Dell and other laptops. Some coating on the chip has been reacting badly to fluctuations in temperature. There is no recall, because there is nothing better to replace them with, and because Nvidia hasn't admitted that all their chips are affected - Nvidia is just replacing the video cards in huge numbers. 

A dell technician I chatted with on the phone expressed a hope that the new, replacement Nvidia cards use a different coating, but since the problem hasn't been formally acknowledged for my card, I wouldn't count on it. Luckily, I've got a long warranty.

Incidentally, I asked them to downgrade my card to Intel integrated or something, and Dell sounded willing, even eager to do so - it would save them money and save me time, and I'm not a gamer so I don't care that much - but apparently they don't have an Intel or ATI alternative welded to the right motherboard for D630s. If you don't have a D630, this might be worth looking into - the first tech support guy said it was impossible, but his manager was much more amenable.

On a basic level, Nvidia's hardware problems are why my graphics failed, and why Dell is so quick to replace it - I am one of many. 

That said, my card limped along for a year under Vista and lasted 24 hours under Ubuntu, and I'd like to make sure my next video card lasts more like a year, so I'm looking for ways to run cool.

---

