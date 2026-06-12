---
title: "XMMS and MIDI revisited"
date: 2005-12-22
forum: Desktop Environments
---

### Post by barfos on 2005-12-22
I've been spending a few days on my ubuntu laptop, using my free time for the old 'trying to get stuff working' bit.  Here's how the xmms midi plugin is coming along. I'm going to document all the steps i took while giving you links to other things that sort of helped me, and might help you.  I've experienced similar things that I've heard about around the forum, and some of them i solved.

After looking around on the internet and this forum I found that the best way to get midi to work in general is to get the timidity package from the synaptic package manager.  I think this allows you to play midi files even if your sound card doesnt support midi.  I always thought all sound cards that come with your computer 'supported midi' because on windows I never had trouble playing midi files.  Maybe I'm wrong.  Anyhow it seems that if you have a special sound card for midi this post is for you.

[http://www.ubuntuforums.org/showthread.php?t=8736](http://www.ubuntuforums.org/showthread.php?t=8736)

After you install the timidity package, youll find an important file on your computer "/etc/timidity/timidity.cfg" .  This is an interesting place to put it because 
1: earlier I wanted to get music in [doomsday]("http://www.doomsdayhq.com/") (midi music) working and it looked for /etc/timidity.cfg instead... and
2: later on i will put a link where it says to copy /etc/timidity/timidity.cfg to /etc/timidity.cfg  I guess because thats where the xmms midi plugin looks for it too.  So why the heck is the ubuntu default at /etc/timidity/timidity.cfg :confused: , anyway.....

To get some instruments you can download the freepats package with synaptic, and then edit /etc/timidity/timidity.cfg like it says on this page

[http://www.geocities.jp/midi_organ_net/timidity/](http://www.geocities.jp/midi_organ_net/timidity/)

I think the important thing to add is the dir /usr/share/midi part after the freepats: line at the bottom of timidity.cfg.  Of course I added all three lines just in case! After I did this much, I could play midis by typing timidity [anything.mid] at a terminal prompt.  :D :D :D  Awesome.  Next step would be to get XMMS to play midis.

[note: if you checked out that site, it says to install timidity-interfaces-extra package.  I did this, but it didnt seem to make much difference.  Later, after I completed all possible directions from all sites, I uninstalled the interfaces-extra package and I didn't break anything (can still play midis with timidity command), I also reinstalled it just to see if it would makes xmms-midi plugin, it didnt... anyway ill continue now]

Now it seems we need the XMMS-MIDI midi plugin.  After being annoyed at the lack of support on the xmms site and the crappy documentation that comes with the source, I found a debian package for it.  You can download it [here]("http://vemod.net/debian/dists/sid/packaged/binary-i386/xmms-midi_0.03-1qerub3_i386.deb"), and then type sudo dpkg -i [thepackage] to install it. Then you must copy /etc/timidity/timidity.cfg to /etc/timidity.cfg, like i said above.  All this is according to this post

[http://www.ubuntuforums.org/showthread.php?t=56773](http://www.ubuntuforums.org/showthread.php?t=56773)

I had no problems doing that.  You might have some dependency problems, but you can try to fix it by using synaptic to get the dependecies.

Then I started experiencing strange stuff.  The first time I tried to play a midi it was silent and I couldnt hear anything.  Then xmms froze when i tried to close it.  After
that, playing a midi crashed xmms completely.  I was frustrated and switched gears to trying to get xmms to play SPC files.  [It didn't take long for me to install the sexyspc package for xmms]("http://www.ubuntuforums.org/showthread.php?t=45162").  But xmms crashed when i tried to play an spc.  "Ok, well lets see if mp3 still works!" I said.  It didn't, but at least it didnt crash, it said 'make sure your sound card is configured properly and nothing else is using it'.   I checked the options, and it was set to ALSA and not OSS.  I'm sure mp3 was working before, but I'm not sure what it was
set to.  I wonder if something I did along the way changed that setting, anyway I set it to OSS and.....

mp3 worked again, spc's working great, and as for midi....... nope nothing.  It didn't crash, but I couldn't hear any sound.  The little bars are moving in the XMMS-midi configuration, but no sound. Maybe the plugin can't find the instruments or something, but without the documentation for xmms-midi who knows.

This is the end of my story, thanks for listening, hope my links are useful!

barfos

EDIT: oops its in the wrong forum, sorry

---

### Post by FarEast on 2005-12-22
Hello barfos,

I am very glad to know that there are many users who are inter-
ested in playing MIDI on Ubuntu.  I am the auther of the web that
you pointed in your message:p
 
Trying to play MIDI files on websites as we play them with WMP
on Windows, I also had much interest in "XMMS-MIDI midi plugin".
I had searched on the internet for information, but I did not come
across any...  So I decided to develop a launcher(GUI) myself.

Kind Regards,
FarEast

---

### Post by barfos on 2005-12-22
Wow I'm glad to get such a friendly response.  I still haven't gotten XMMS-MIDI to work, despite trying some stuff.  The original website pointed to at XMMS isn't there anymore, and also XMMS website doesn't seem to have been updated in a few years.

Now I'm going to complain about spc xmms stuff in another post!

Thanks
barfos

---

### Post by FarEast on 2005-12-22
Hi barfos,

I forgot to thank you for the following advice.

> I think the important thing to add is the dir /usr/share/midi part
> after the freepats: line at the bottom of timidity.cfg.

What you wrote is right, so I corrected the web.  Thanks!

FarEast

---

### Post by kmbh on 2006-04-09
Hi barfos,

thanks for your report. I tried it and ... same result. No single beep from a midi-file!

So I starded xmms in a terminal to see if there are some errors. 

```
/etc/timidity.cfg: line 9: syntax error
/etc/timidity.cfg: line 11: syntax error

```
I commended out the 2 lines (10 minutes bevore I did the opposite) and for me it works!

Cheers, 
kmbh

---

### Post by Kuprin on 2006-08-08
This is one of those problems that's been paining me for a couple of years now. I've ALMOST got it - I've got a system with a working MIDI hardware synth, and I want to play MIDI music in the same playlist as everything else, without trying to convince Wine into allowing for MIDI support.

Is there ANY way to do this?

---

