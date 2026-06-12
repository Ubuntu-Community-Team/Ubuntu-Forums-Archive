---
title: "Dell Inspiron 1525 ubuntu pre-installed question"
date: 2008-04-06
forum: Dell  Ubuntu Support
---

### Post by benji.ijneb on 2008-04-06
Hiyo,

I'm very interested in buying the Dell Inspiron 1525 with ubuntu pre-installed - looks good :)

one thing though. I've heard lots about problems with compiz not working. Apaz there's a fix which causes video playback to get mucked up (hmm... not too good...). Is it true that this will be/has been fixed in ubuntu hardy, and will this laptop be released with hardy pre-installed?

thanks for all your help...

---

### Post by lofidelity on 2008-04-07
Same as with Gutsy, I'm sure they'll be keeping up to the cutting edge.   I'd say keep an eye on [http://linux.dell.com/wiki/index.php/Products/Consumer]("http://linux.dell.com/wiki/index.php/Products/Consumer") sometime after Hardy hits final.  They seem to keep everything posted there that they'll tell us officially.

:popcorn: <----waiting to buy his own!

---

### Post by benji.ijneb on 2008-04-08
> **lofidelity said:**
> Same as with Gutsy, I'm sure they'll be keeping up to the cutting edge.   I'd say keep an eye on [http://linux.dell.com/wiki/index.php/Products/Consumer]("http://linux.dell.com/wiki/index.php/Products/Consumer") sometime after Hardy hits final.  They seem to keep everything posted there that they'll tell us officially.


thanks, but not entirely sure that i understand...
what are you trying to say?

---

### Post by lofidelity on 2008-04-08
Sorry...writing comments while I'm tired is probably bad.

I meant that they'll probably wait a little bit before they start shipping systems with Hardy, same as they did Gutsy.

 I think it was about a 2 month delay to work out the kinks.   Before then though, keep an eye on the dell linux wiki I linked too, since they post bugs / fixes for things there, as well as remastered disks once they have one.

Make more sense now?

---

### Post by notwen on 2008-04-08
> **benji.ijneb said:**
> Hiyo,

I'm very interested in buying the Dell Inspiron 1525 with ubuntu pre-installed - looks good :)

one thing though. I've heard lots about problems with compiz not working. Apaz there's a fix which causes video playback to get mucked up (hmm... not too good...). It is true that this will be/has been fixed in ubuntu hardy, and will this laptop be released with hardy pre-installed?

thanks for all your help...

Compiz-Fusion has blacklisted the Intel X3100 chipset, it can however be ignored, in turn producing a error w/ some video playback.  This also can be fixed by changing the video input.  I have a Inspiron 1420n w/ the X3100 chipset and run Compiz w/o any issues and all video works just fine.  As far as the Nvidia card goes, I have not seen many issues regarding it other than the hibernate one(see Dell Linux Wiki link below)

Check out [Dell's Linux Wiki]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10") for more info on issues that may be affecting the Inspiron 1525.  Each issue generally has a workaround/fix that is easily doable by even a novice user.  

As far as Hardy, I'm guessing Dell will create their own custom Hardy heron image and have it posted a month or two after the official release.  It took them some time to release the custom Feisty image, but their custom Gutsy image was released pretty soon after the official Gutsy release.  

I have zero complaints about my Inspiron 1420n and I do encourage you to support Dell's offering of pre-installed Linux machines if what they offer meets your satisfaction and needs.  Best of luck in your possible future purchase.  =]

---

### Post by benji.ijneb on 2008-04-08
> **notwen said:**
> Compiz-Fusion has blacklisted the Intel X3100 chipset, it can however be ignored, in turn producing a error w/ some video playback.  This also can be fixed by changing the video input.  I have a Inspiron 1420n w/ the X3100 chipset and run Compiz w/o any issues and all video works just fine.  As far as the Nvidia card goes, I have not seen many issues regarding it other than the hibernate one(see Dell Linux Wiki link below)


thanks - all this has cleared things up a bit.

One question, how did you manage to get it all to work - is there a howto?

---

### Post by notwen on 2008-04-08
To skip the blacklist check for Compiz-Fusion check [this sticky thread]("http://ubuntuforums.org/showthread.php?t=582112") in the Desktop Customization sub-forum.

To work around the video playback issue change your video output in whatever video player you prefer to 'no Xv'.  I personally use VLC, but the person who posted this fix changed this in gstreamer-properties.  You can view the launchpad bug [here]("https://bugs.launchpad.net/dell/+bug/141298").  Some ppl claim the fix didn't work for them, but in all instances of video playback I have had no issue.  Post back and let me know if it works for you as well.  =]

---

### Post by benji.ijneb on 2008-07-10
Ooh! one more question (if anyone is still out there...)

I am not in any way planning to use this as a gaming PC, but will 2D games such as teeworlds work well on this PC (it has a X3100 thingamajoogle...). Teeworlds is 2D, but needs to be able to run very fast for it to be playable.

Would UT2004 work -that's not essential but would be nice...

---

