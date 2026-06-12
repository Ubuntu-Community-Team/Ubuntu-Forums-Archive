---
title: "dvbtools and other missing software"
date: 2006-06-04
forum: Desktop Environments
---

### Post by elmarko on 2006-06-04
I've just installed 6.06 on my Athlon 64 3000+ system, although I've used a 32bit install because with Breezy, my DVB-t cards didnt seem to like being run under 64bit all that much.

Is the fact that 6.06 is relatively new the reason that I can find none of the software I need for dvb-t in the package lists? I cant find dvbtools, xine or xine-ui, etc. I did find Kaffiene but without the aforementioned dvb support it's kinda useless.

I think the card is working ok (It's an Avermedia 771, worked fine under Breezy), there's no errors in /var/log/messages and it looks like everything got installed fine, I just dont have the software to use the damn thing :)

Any ideas? I'm not too experienced with installing from source but I'll have a go if thats the only way.

edit: seems to be compiled in, actually. It's just getting it to all load automaticaly im not too sure about. I just had to modprobe a bunch of stuff myself.

---

### Post by kaamos on 2006-06-04
You must enable the universe & multiverse repos to get those packages.

This is for 5.10, but you should get the idea -> [https://wiki.ubuntu.com/AddingRepositoriesHowto?highlight=%28repositories%29#head-5be95103ff75d442c031184440fc53892140eead](https://wiki.ubuntu.com/AddingRepositoriesHowto?highlight=%28repositories%29#head-5be95103ff75d442c031184440fc53892140eead)

---

### Post by elmarko on 2006-06-04
You are a huge pile of awesome. Thanks.

Now I just have to find out why this card seems to be really misbehaving in Kaffiene :( All the playback is jerky and I have no sound. The sound works in other areas, just not playback with the dvb-t card.

The EPG works, I'm seeing data for the now/next programmes etc.

And now I've tried it in Xine, I can confirm it doesnt work in that either. I get very jerky picture and no sound at all. Perhaps there IS something wrong with those drivers after all but I don't know where to start :(

edit: glxgears is slower than a very slow thing. perhaps I'm missing some drivers here

---

### Post by elmarko on 2006-06-04
Time to update the thread.

NForce and Nvidia drivers installed, glx works ok, and now my video playback is not choppy.

The problems I'm having now are:

1) No sound at all with DVB playback
2) After 10 or so seconds, I lose the DVB stream completely and have to restart whichever video app im using to play it

This is the same thing that used to happen under 64bit breezy and I thought the 64bit kernel was the problem, but it would appear not.

Does anyone have any idea how to get this Avermedia 771 card working properly because I'm very close to tearing my hair out, cutting my losses, and installing XP-MCE :(

---

### Post by elmarko on 2006-06-05
Pity bump.

Current situation:

Ubuntu detects and installs my DVB-t card. Avermedia 771. Gets detected as some weird Zarlink MT352 card, but seems to work. Ish.

I get no sound at all from the stream (sound works in other areas of Ubuntu) and the stream from the card is lost after a few seconds, no matter what application I use to play from the card.

Amusingly, before I installed the Nvidia drivers, even though video playback was choppy, and I still had no sound, the stream never got lost from the card. It was just unwatchable :)

Same thing used to happen under Breezy 64bit and I thought 64bit was the problem. This time I've used 32bit, and it's the same. So it's not that.

Dodgy drivers? Something I'm not doing right? I am pretty stuck and aren't as experienced as I would like to be. I will consider all options and try and answer any questions!

Thanks.

---

