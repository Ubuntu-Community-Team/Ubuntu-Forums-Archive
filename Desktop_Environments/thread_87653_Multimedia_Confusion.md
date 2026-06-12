---
title: "Multimedia Confusion"
date: 2005-11-08
forum: Desktop Environments
---

### Post by Ingla on 2005-11-08
Hello.

Actually, I posted this question a few days ago, but had a lot of trouble doing so. The site was not responding or the Internet was having a traffic jam. Anyway, I'm just not sure anyone ever saw it.

I'm still pretty new to Linux and trying to get everything set up (Ubuntu 5.10).

I have xine, mplayer, gixine, VLC, Totem and XMMS on the machine.

Firefox plugins that I can see (usr/lib/mozilla-firefox/plugins) seem to be for Totem and mplayer.

Mostly, when I try to open a stream, Firefox calls xine (gxine). Seems to be default although it doesn't appear in the Plugins list. It works OK for some things.

If I try to test for Quicktime (here:[http://fredrik.hubbe.net/plugger/test.html)](http://fredrik.hubbe.net/plugger/test.html)), xine opens and I get:


"xine engine failed to start.
No demuxer found-Stream format not recognized"

Some streaming radio doesn't work but, if I copy the link and open it in VLC, it's fine.

Some sites with streaming video are using a server side version of Media Player (I think). In Linux it just sits there looking at me and doesn't open anything.

Whenever Firefox suggests a plugin, it returns "No appropriate plugin found".

Any ideas (specifically) how I can get some of this in order?

Thanks.

---

### Post by not_yet on 2005-11-08
give this a try

1) In your Mozilla (or Firefox) location bar, enter the URL about:config
2) Right-click to get a popup, select New->Boolean
3) Enter the string "network.protocol-handler.external.mms", then OK
4) Enter the string "true", then OK
5) Right-click again, select New->String
6) Enter the string "network.protocol-handler.app.mms", then OK
7) Enter the string "gmplayer", then OK

---

### Post by Ingla on 2005-11-08
Wow!

I'm a little afraid to try that in case I didn't understand things well. If I mess up something, can I get Firefox back?

May it be clear that I've never done anything like this before so, with your kind permission, I'll ask a couple of dumb questions before I try it:

>>1) In your Mozilla (or Firefox) location bar, enter the URL about:config
[COLOR="Red"]You mean I type "about:config" (like that)?[/COLOR]
>>2) Right-click to get a popup, select New->Boolean
[COLOR="Red"]Right-Click where...location bar...window?[/COLOR]
>>3) Enter the string "network.protocol-handler.external.mms", then OK
[COLOR="Red"]This will be a pop-up? I get some place to type a string (copy and paste what you wrote)? 
Then there's an "OK" to click...or do I type that too?[/COLOR]
4) Enter the string "true", then OK
[COLOR="Red"]Same question: I now have a new place to type and I write "true"? Or is it a choice to highlight? Is this like DOS?[/COLOR]
>>5) Right-click again, select New->String
>>6) Enter the string "network.protocol-handler.app.mms", then OK
>>7) Enter the string "gmplayer", then OK
[COLOR="Red"]If I get through 4), I assume all this will be the same drill.[/COLOR]
  	
By the way, what does this do, use xine or mplayer or what exactly?

Thanks for the help (and the patience).

---

### Post by Third Thoughts on 2005-11-08
[QUOTE=Ingla]Wow!

I'm a little afraid to try that in case I didn't understand things well. If I mess up something, can I get Firefox back?

May it be clear that I've never done anything like this before so, with your kind permission, I'll ask a couple of dumb questions before I try it:

>>1) In your Mozilla (or Firefox) location bar, enter the URL about:config
[COLOR="Red"]You mean I type "about:config" (like that)?[/COLOR][/QUOTE]
Yes exactly like that
> 
>>2) Right-click to get a popup, select New->Boolean
[COLOR="Red"]Right-Click where...location bar...window?[/COLOR]
You right click in the window
> 
>>3) Enter the string "network.protocol-handler.external.mms", then OK
[COLOR="Red"]This will be a pop-up? I get some place to type a string (copy and paste what you wrote)? [/COLOR]
Yup
> 
Then there's an "OK" to click...or do I type that too?
You click it
> 
4) Enter the string "true", then OK
[COLOR="Red"]Same question: I now have a new place to type and I write "true"? Or is it a choice to highlight? Is this like DOS?[/COLOR]
A new popup will appear, write it in that
> 
>>5) Right-click again, select New->String
>>6) Enter the string "network.protocol-handler.app.mms", then OK
>>7) Enter the string "gmplayer", then OK
[COLOR="Red"]If I get through 4), I assume all this will be the same drill.[/COLOR]

By the way, what does this do, use xine or mplayer or what exactly?
This uses gmplayer
> 
Thanks for the help (and the patience).

As an alternative you can delete the firefox plugins related to totem. If you type about: plugins (no space, I had to put one otherwise it printed a smiley) into the location bar you can get a list of firefox plugins. You should see both Mplayer and Totem plugins. Look under the Totem section for the "File name:" associated with the totem plugins. Then go and delete that file. 
A somewhat related warning. If you use the mplayer plugin that comes from the breezy repository you may have some crash issues. Go here [http://mplayerplug-in.sourceforge.net/](http://mplayerplug-in.sourceforge.net/) to get the latest program. It works like a charm for me.
~Andrew S.

---

