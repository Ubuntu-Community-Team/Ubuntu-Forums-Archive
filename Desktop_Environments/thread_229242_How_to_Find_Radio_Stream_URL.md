---
title: "How to Find Radio Stream URL ?"
date: 2006-08-04
forum: Desktop Environments
---

### Post by latebeat on 2006-08-04
Hi there,

I've been using mplayer to record my favourite radio broadcasts however, there's this new one I want to record and I don't know how to find the stream address so I can pass it to mplayer? It uses javascript to open a hidden asf stream.
The address of the radio program is [here]("http://www.nitroradio.gr/nitroRadio.asp?id=1") and Netstat shows the IP as: 70.85.202.226:80

Is there any way to find the real address of the asf stream ?

thanks
latebeat

---

### Post by editrix on 2006-08-04
I couldn't manage to play it, but according to Kaffeine the address is


[http://1170.85.202.266/nitro4555](http://1170.85.202.266/nitro4555)

NB: I couldn't copy this address, so I had to write it down manually. It may be wrong.

---

### Post by latebeat on 2006-08-04
Well, I have trouble playing it with opera. I can only play the stream with firefox or epiphany and you do have to click play.
However can I ask how did you get that from Kaffeine in the first place (eventhough it doesn't work indeed) ?

---

### Post by moma on 2006-08-04
$ mplayer [http://70.85.202.226/nitro4555?MSWMExt=.asf](http://70.85.202.226/nitro4555?MSWMExt=.asf)

GET command gives these

$ [COLOR="Green"]GET [http://70.85.202.226/nitro4555?MSWMExt=.asf](http://70.85.202.226/nitro4555?MSWMExt=.asf)[/COLOR]
[Reference]
Ref1=http://70.85.202.226/nitro4555?MSWMExt=.asf
Ref2=http://70.85.202.226:80/nitro4555?MSWMExt=.asf

GET is part of "libwww-perl" package.

---

### Post by latebeat on 2006-08-04
Thanks mono! You rock! 

Could you please be a little more specific thought about how you found it? (so I wont need to post to the forums whenever I come across a new stream :))

I mean if I only knew the IP address: 
```
 GET 70.85.202.226
[Reference]
Ref1=http://70.85.202.226/?MSWMExt=.asf
Ref2=http://70.85.202.226:80/?MSWMExt=.asf
```

you still don't get the nitro4555 part? How did you get that?

thanks again!

---

### Post by moma on 2006-08-04
No secrets here.

I opened your url... in Firefox and cliked into "Live Radio...".
Position the mouse-cursor near the "mplayer" (or what ever plugin it is) in the window. The plugin is quite small, but I can partly see "Connecting to server" and "Buffering..." text below it.

Then press right-mouse-button and select "Copy URL" from the popup menu. The big secret ;-)

Paste the URL on the terminal window (again with right-mouse-button menu).
BTW: Good music. From Greece?

GET is handy tool because it reads the URL (webpage or play list,..) and outputs the content in clear text.

---

### Post by editrix on 2006-08-04
I did basically the same as moma. I'm in KDE, so when I hit the "Live radio" button Kaffeine opened. Couldn't play it, but did give a URL it was fetching. Then, I went to "open recent" in Kaffeine, and the URL was there.

---

