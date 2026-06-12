---
title: "Change application for opening wmv files in firefox"
date: 2006-07-09
forum: Desktop Environments
---

### Post by tcollogne on 2006-07-09
Hi all,

First I was using totem as video player, but now I switched to Mplayer.
I got the plugin working in firefox and when I download a wmv file, I can view it in mplayer.

But now there is a site and when I click on the link to the wmv file, I get a notfication from firefox that an external application is about te be called for this file.

The problem is that firefox wants to call totem, but I removed it, so now nothing happens. Where can I change this, so that firefox will open Mplayer instead of Totem.

Can somebody help me?

Thanks

---

### Post by Dubbayoo on 2006-07-09
well, you could just install the mplayer firefox plugin.

---

### Post by yuv on 2006-07-09
it is possible that you will need: [ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.4_i386.deb](ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.4_i386.deb)

see also the
[http://www.beginningubuntu.com/dapper_tips.html](http://www.beginningubuntu.com/dapper_tips.html)

---

### Post by tcollogne on 2006-07-09
I can view wmv files ok. And the plugin works.
I found that the problem was that the url of the movie had the mms protocol.

So I just did what is described here

[http://zerlinna.blogweb.de/archives/73-Watching-Video-streams-mms-and-rtsp-protocol.html](http://zerlinna.blogweb.de/archives/73-Watching-Video-streams-mms-and-rtsp-protocol.html)

And that did the trick.

Thanks anyway.

---

### Post by tcollogne on 2006-07-09
Oh yes,

And I changed mplayer in gmplayer so that the controls are also visible.

---

### Post by chajuram on 2006-07-09
> **tcollogne said:**
> 
And I changed mplayer in gmplayer so that the controls are also visible.

Could you expand on this please? How do I do this?

Thanks,

Chajuram.

---

### Post by tcollogne on 2006-07-09
In the link I posted, there is stated

Open your firefox. Type as url: about:config
Now just rightclick somwhere into the main window. A little box with options to choose will appear. Choose "new", then "string". Then copy this line into the appearing text field:
network.protocol-handler.app.mms
Into the next text field: **/usr/bin/X11/mplayer**
Now you do the same thing again, but this time you choose not "string" but "boolean", and the line to copy is: network.protocol-handler.external.mms. Then set "true".

You change the text I put in bold to this **/usr/bin/X11/gmplayer**

That way the controls of mplayer are shown.

Did this help?

---

### Post by strabes on 2006-07-09
what do you mean by "You change the text I put in bold to this /usr/bin/X11/gmplayer"

Where do I change this? Do I add another new string?

---

### Post by tcollogne on 2006-07-09
You type about:config in the address bar of your firefox browser, than you get a list of configuration entries

First you check if the entry **network.protocol-handler.app.mms** exists.
If it does, you change the value of the **network.protocol-handler.app.mms** entry
from **/usr/bin/X11/mplayer** into **/usr/bin/X11/gmplayer**

If the entry does not exist that you add a new string (right click -> new -> string) **network.protocol-handler.app.mms** with value **/usr/bin/X11/gmplayer**

I had to restart firefox and then it worked.

Do you understand now, or do you need more help?

---

### Post by strabes on 2006-07-09
Got it, thanks. It was just confusing since earlier you told me to make that string, and then said to change it.

---

