---
title: "Attn: Mr. Mark Shuttleworth"
date: 2008-05-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by drsaamah on 2008-05-22
Seeing [here]("http://www.guardian.co.uk/technology/2008/may/22/internet.software") that you use the Dell XPS 1330m (:)), I would like to ask... does your Hibernate/Suspend work?  If so, please shed some light for your fellow Ubuntu users.
Regards,
Saam

---

### Post by aidave on 2008-05-22
Haha!  I'd also like to know.  Maybe he never uses it?  Maybe he has an expert tweaking it to work?  

Mine did work for a while with the new 8.04 but now has gone off the deep end with whatever update/thing I did to it.

---

### Post by Technoviking on 2008-05-23
My Hibernate/Suspend works well with my m1330 on Ubuntu 8.04, even using the 64-bit version. My zero changes to get it to work.

---

### Post by drobvice on 2008-05-23
I wish I could say the same.  I get a weird beeping thing that happens when it comes back from suspend, often.  I'm not on 64 bit though.

---

### Post by akniss on 2008-05-23
> **drsaamah said:**
> Seeing [here]("http://www.guardian.co.uk/technology/2008/may/22/internet.software") that you use the Dell XPS 1330m (:)), I would like to ask... does your Hibernate/Suspend work?  If so, please shed some light for your fellow Ubuntu users.
Regards,
Saam

Maybe this will help you:
[http://ubuntuforums.org/showpost.php?p=4876098&postcount=1](http://ubuntuforums.org/showpost.php?p=4876098&postcount=1)
It took some tweaking, but mine now works perfectly.

---

### Post by tighem on 2008-05-23
I get the weird beeping thing on my D820, but it does resume...

---

### Post by drsaamah on 2008-05-23
akniss, thanks for the thread link.  I have the nvidia card so I tried adding nvidia to the whitelist in the acpi-support file and I'll let you know whether or not that fixes my issue.  If it does, maybe we ought to email the link to your thread to Mark :)

---

### Post by akniss on 2008-05-23
> **drsaamah said:**
> akniss, thanks for the thread link.  I have the nvidia card so I tried adding nvidia to the whitelist in the acpi-support file and I'll let you know whether or not that fixes my issue.  If it does, maybe we ought to email the link to your thread to Mark :)

Man... I'm jealous of your 64GB SSD... I ordered mine before they had the larger solid state available. Mine's only 32G.  Plenty for my needs, but bigger is always better, right?

Back on topic: Another thing that I think may be contributing to suspend/resume issues with this laptop is the webcam that comes on this model is different depending on the screen, and I'm not sure if they both use the same driver.  Would you mind posting the output of: ```
lsmod | grep video
```

---

### Post by sdennie on 2008-05-24
I've done nothing to setup suspend/resume on my XPS m1330 (nvidia) other than what is described on the Dell support pages:[here]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10") and [here]("http://linux.dell.com/wiki/index.php/Ubuntu_8.04").  I don't even know if it was needed but, suspend/resume works perfectly fine for me.  It did however start beeping at me on resume at one point so I went to System->Preferences->Power Management->General and disabled the "beep on error" option.

---

