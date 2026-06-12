---
title: "dell inspiron 1501 audio"
date: 2009-10-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by pateu on 2009-10-25
hey guys,
i've posted a thread for the same problem a while ago, but got no answer and i thought i'd reformulate a bit.
so, i have an inspiron 1501, with Sigmatel STAC9200 audio chipset. my only problem with any linux distro so far is that i can't listen to what i'm playing on my guitar, because there is no monitor volume for any mic/line input in the volume control. (the only working solution is using ubuntu studio with rt kernel and routing the audio input to the output using jack, but i'd rather not depend on that).
this problem is also in windows, but there is a fix for it, found here: [http://en.community.dell.com/forums/p/18112824/18235810.aspx#18235810]("http://en.community.dell.com/forums/p/18112824/18235810.aspx#18235810")
basically, you have to do some modifications in the windows registry, modify some values for tags like "EnableInputMonitor" or "EnableIntSpkrMute" and you get the volume bar in the volume control. 
I was wondering if there is anything similar in linux, to do some changes in order to have the volume for Input Monitor in the volume control. i'm really sorry if my question is stupid, but i'm not really experienced with linux.
thanks a lot

---

