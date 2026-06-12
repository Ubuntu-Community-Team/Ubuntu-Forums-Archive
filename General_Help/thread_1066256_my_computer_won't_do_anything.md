---
title: "my computer won't do anything"
date: 2009-02-10
forum: General Help
---

### Post by guine on 2009-02-10
My computer was running really slow today and I had downloaded some pictures from my camera onto it which filled up the harddrive so I started trying to delete files to free up room.  Some of these files deleted but had no impact on free disk space or showed up in my trash folder while others said they couldn't be deleted(these were all videos and pictures that I had put on the computer a couple years ago from the same user account, nothing that shouldve been undeletable).  After trying to delete some files the computer froze and I turned it off and then I restarted it.  It got through the bios and started booting ubuntu for a little and then I got a message saying it couldnt boot further because the harddrive was full and all I could do was press the power button to have it shut down.  After doing this one more time on the third time I tried to boot the computer it just turned on and immediately beeped 4 times and then did nothing.  Is there anything that I can do or does this just mean that my computer is dead and I need to go computer shopping?

---

### Post by guine on 2009-02-10
And I forgot to mention that it does the exact same thing if I try to turn it on with a live cd in it.

---

### Post by ugm6hr on 2009-02-10
Sounds like a hardware problem.

But it is likely a single component - perhaps motherboard, posiibly HD.

Unfortunately, without being able to boot a LiveCD, it will be tricky to find out what.

Maybe take the HD out and try a LiveCD?

---

### Post by boof1988 on 2009-02-10
> **guine said:**
> And I forgot to mention that it does the exact same thing if I try to turn it on with a live cd in it.

If you are CLI savvy and you have a GPartEd LiveCD, you could load the GPartEd (entirely) to RAM (if you have enough RAM), mount the drive and delete the offending files.

Another possible option...  There might be an option to disable the use of the swap partition while using the liveCD.  I don't know if this will help you or not though.  Hopefully someone else can chime in and give you the correct/sure answer.

---

### Post by boof1988 on 2009-02-10
> **ugm6hr said:**
> Maybe take the HD out and try a LiveCD?

I think this would be a good way to see if there are any other hardware issues.

---

### Post by Hobgoblin on 2009-02-10
> **guine said:**
> I tried to boot the computer it just turned on and immediately beeped 4 times and then did nothing.  Is there anything that I can do or does this just mean that my computer is dead and I need to go computer shopping?

The beeps tell you what is wrong, but you need to know the BIOS type/version to interpret them.  In general they mean you have a hardware fault which is preventing the BIOS getting as far as initialising the video, hence the only way to communicate is via beeps.

[This may help](http://www.bioscentral.com/beepcodes/awardbeep.htm).

---

### Post by guine on 2009-02-10
> **Hobgoblin said:**
> The beeps tell you what is wrong, but you need to know the BIOS type/version to interpret them.  In general they mean you have a hardware fault which is preventing the BIOS getting as far as initialising the video, hence the only way to communicate is via beeps.

[This may help](http://www.bioscentral.com/beepcodes/awardbeep.htm).

Thats what it was, this is the second time ive had the ram come loose on its own and I just had to get a high school student from down the street to get it back in since for some reason 1 of my sticks of ram doesn't go in easily.  So now I'm just trying to clean up some diskspace on my main harddrive from my old breezy install(that install has saved me a number of times) so that I can boot on my main harddrive again.  I'll be back if I have any more trouble, thanks for the help everyone.

---

