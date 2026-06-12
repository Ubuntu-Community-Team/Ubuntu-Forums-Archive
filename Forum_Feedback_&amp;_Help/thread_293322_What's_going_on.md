---
title: "What's going on?"
date: 2006-11-05
forum: Forum Feedback &amp; Help
---

### Post by codypumper on 2006-11-05
I've posted several threads on problems I have only to get no responses. It didn't used to be that way. What's going on? I encourage those who currently have a perfectly working machine to help others more. Strangely it was around the time commercial support was offered that the community began to slack in my opinion. Anyway, I came to Ubuntu for and because of the community, now hope the community will stay strong, rather then weaken. If none of this seems reasonable, it may be because I'm frustrated with alsa, or because its true :confused:

---

### Post by Polygon on 2006-11-05
usually people dont reply to threads when they dont know the answer, so people with REALLY obscure problems most often then not have their threads just ingnored

---

### Post by Sef on 2006-11-05
Why don't you supply a link to your posts along with a short description of the problem you are having for each post.

---

### Post by aysiu on 2006-11-05
Moved to the appropriate forum. > **codypumper said:**
> I've posted several threads on problems I have only to get no responses. It didn't used to be that way. What's going on? I encourage those who currently have a perfectly working machine to help others more. Strangely it was around the time commercial support was offered that the community began to slack in my opinion. Anyway, I came to Ubuntu for and because of the community, now hope the community will stay strong, rather then weaken. If none of this seems reasonable, it may be because I'm frustrated with alsa, or because its true :confused:
I think your perception is off.

I regularly look at the zero-reply threads, and I can promise you they are usually zero-reply for a reason--no one knows the answer. The problem is too difficult or obscure for even the veteran users.

I don't see how the offer of commercial support (which Ubuntu has offered from the very start, as far as I know--at least since Hoary, anyway) should have any effect on the support here. All support on these forums is volunteer support. We are all users like you. None of us is employed by Ubuntu or Canonical.

I suggest you read this thread:
[To all those with zero-reply threads...](http://ubuntuforums.org/showthread.php?t=82471&highlight=zero-reply)

---

### Post by codypumper on 2006-11-05
Sef:
[http://ubuntuforums.org/showthread.php?t=292351](http://ubuntuforums.org/showthread.php?t=292351)
I can't get Creative Soundblaster Audigy 24 bit to work now.

[http://ubuntuforums.org/showthread.php?t=291432](http://ubuntuforums.org/showthread.php?t=291432)
the sound card problem again, as well as my cpu problem

[http://ubuntuforums.org/showthread.php?t=291398](http://ubuntuforums.org/showthread.php?t=291398)
Info I could use to hopefully fix my sound card

---

### Post by codypumper on 2006-11-05
](*,)  Sorry Aysiu. Really, I just need to go to bed...

---

### Post by aysiu on 2006-11-05
> **codypumper said:**
> ](*,)  Sorry Aysiu. Really, I just need to go to bed...
Nothing to apologize about.

Get some rest.

If you feel ignored, bump your thread once every 24 hours about three times, and if you still get no answer... probably no one knows the answer.

---

### Post by kerry_s on 2006-11-05
One thing that doesn't help is the 10 page limit, if your not in the first 10 no one can see your post when they use the "New Posts" button. I'll often wake up and try and catch up, but unless i go from area to area i have no idea how many new posts there actually was. It use to be alot better when there was no limit on pages.

---

### Post by bonzodog on 2006-11-05
hrm...

I have just looked at all these threads, and they ALL point to ONE thing. 

It seems that with the udev upgrades and changes, h/w detection and coldplugging of drivers (hotplug is no longer supported), some thing has broken inside udev with the daemon that modprobes drivers on boot. 
The distro I now use (Zenwalk) has it's own custom written daemon called uwd that detects hardware when it's changed. 
It sounds like a change is needed in one of the conf files; if the card was changed AFTER the edgy install, that it could be that the soundcard driver insertion is hard-coded into a conf file.
I cannot remember what Ubuntu uses as its on-the-fly detection dameon but it sounds like they broke USB detection as well.
Running modprobe ALL the time????

..eep. Thats bad. Like, really bad. 

Yes, it solves the problem of on the fly driver insertion, but it sounds like a temporary fix.

---

### Post by codypumper on 2006-11-05
yeah, its not too fun...

---

