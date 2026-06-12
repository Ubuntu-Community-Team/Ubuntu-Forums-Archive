---
title: "Volume on Ubuntu Quieter Than Vista"
date: 2009-05-09
forum: General Help
---

### Post by fiveacez on 2009-05-09
I noticed that when I'm running Ubuntu, I need to crank up the volume to max to hear something, while on Vista, I only need to raise the volume only a little to get the same desired volume.  

What is going on?

---

### Post by Altay_H on 2009-05-09
I had the opposite problem on my computer. When I upgraded from XP to Ubuntu my speakers had a greater maximum volume. Unfortunately my sister's computer has the same problem as yours. She switched from Vista to Ubuntu, and now her volume isn't as loud as it used to be. I've searched for solutions, but the only decent suggestion I could find is to open the Volume Control and ensure that all the channels are maxed out. However, that wasn't the problem on my sister's computer. I'm interested in the solution to this problem as well.

---

### Post by fiveacez on 2009-05-09
What computer does your sister use out of curiosity?  Is it an HP laptop?

---

### Post by Tipped OuT on 2009-05-09
Make sure ALL volume channels are set to max. I had this problem before too.

---

### Post by Altay_H on 2009-05-09
> **fiveacez said:**
> What computer does your sister use out of curiosity?  Is it an HP laptop?
Yes. It's an HP Pavilion dv6000.

---

### Post by fiveacez on 2009-05-09
> **Tipped OuT said:**
> Make sure ALL volume channels are set to max. I had this problem before too.


How do I do that?  Do I go to volume control?

---

### Post by fiveacez on 2009-05-09
> **Altay_H said:**
> Yes. It's an HP Pavilion dv6000.


I have a dv5t 1000 with Altech Lansing speakers. Hmmmm. Interesting...

---

### Post by Altay_H on 2009-05-09
> **fiveacez said:**
> How do I do that?  Do I go to volume control?
Click on the volume icon on the upper right and choose "Volume Control...".

---

### Post by fiveacez on 2009-05-09
Ok, well, that didn't help too much... still pretty quiet unless it's above 75%.

---

### Post by fiveacez on 2009-05-10
bump

---

### Post by Tipped OuT on 2009-05-10
Hmm...hold on I'm thinking, just want to let you know..:P

---

### Post by danwood76 on 2009-05-10
In the volume control click preferences and look for anything labelled PCM or Speakers and enable them and turn them up.

Also select pulse (monitor of xxx soundcard (pulseaudio))volume control from the drop down menu and check taht is turned up.

---

### Post by Tipped OuT on 2009-05-10
Okay have you tried other output methods? Like try using Pulse Audio for example.

EDIT: Yeah what the above post says. Posted before me -_-'

---

### Post by fiveacez on 2009-05-10
That helped a little, but it still hasn't done much.  Vista is still twice as loud, and I can't hear ANYTHING under 60% volume with Ubuntu.

---

### Post by danwood76 on 2009-05-10
Very odd, I would hazard a guess that its an alsa bug.
I normally find Ubuntu louder than windows :)

What soundcard do you have in the machine?
(this command will dump it:)
```

lspci | grep -i 'audio'

```

---

### Post by fiveacez on 2009-05-10
```
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

```

---

### Post by danwood76 on 2009-05-10
Odd ICH9 is very common and will probably use the HDA-intel driver.
Although the chipset is rather new so might have a bug in the driver.

There is another volume slider that might be available from the gnome volume control which will be called OSS mixer, that normally has a slider that sets itself around 60% try pumping that up.

---

### Post by fiveacez on 2009-05-10
Ok. It's definitely louder now, but it's still only audible above 60%.

---

### Post by albinootje on 2009-05-10
> **fiveacez said:**
> I noticed that when I'm running Ubuntu, I need to crank up the volume to max to hear something

I've seen this problem on several laptops in the last year or so, and I haven't come across a solution yet.

---

### Post by Altay_H on 2009-05-28
Is there no way to manually "overclock" your speakers? I mean, you would risk damaging the speakers, but it seems like there should be a manual way to set the maximum volume. Does anyone know anything about this?

---

