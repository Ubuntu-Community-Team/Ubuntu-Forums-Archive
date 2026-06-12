---
title: "Midi help"
date: 2007-03-30
forum: Education &amp; Science
---

### Post by groeswenphil on 2007-03-30
Hi Group,

For some years I've been working on a web site for my school children.

It's to help them with their music.

It presents them with a piece of music manuscript and a midi file to play along to.

[http://www.btinternet.com/~groeswenphil/](http://www.btinternet.com/~groeswenphil/)

Thing is though, how do I get those midi files to sound in Firefox?

Yours,
Phil

---

### Post by tatimmer on 2007-03-30
I dont know how to play a midi in Firefox.

You need either a hardware synth that can convert the on-off messages to a wav file or a soft synth like "Timidity". I use Timidity from the command line but there are other interfaces. It can convert the midi to a wav on the fly and play it thru your sound card.

You can install the following packages:
sudo apt-get install timidity
sudo apt-get install freepats

freepats is a set of sound patches used to create the wav file. The sound quality is very good. Much better than Windows media player.

---

### Post by tentwelveeight on 2007-03-30
I don't have Ubuntu on this computer so I can't test out whether this works or not, but I'd suspect your problem lies with not specifying which player should handle the embedded midi files in firefox. You can read about how to do that [here]("http://kb.mozillazine.org/Video_or_audio_doesn't_play"). You'll need to install [quicktime]("http://www.apple.com/quicktime/download/") and [configure the settings]("http://kb.mozillazine.org/Quicktime#Quicktime_browser_settings"). (I'm assuming your using the embed tag in your html, if not you can read about that [here]("http://www.angelfire.com/fl5/html-tutorial/music.htm").

Finally, if that doesn't work you can always convert the midi files into mp3 files and use a [flash player such as odeo's]("http://odeo.com/audio/236298/players") to embed the mp3 files in the webpage. You can see an example of a page I've made that uses this strategy [here]("http://hartmanbot.com/webpages/edtec/standards/technical.html").

Let me know if that doesn't solve your problems. BTW, great idea! -joe

---

### Post by groeswenphil on 2007-04-01
Thanks for that.

I've just spent some hard earned cash downloading Swish Jukebox..........once again, it works perfectly in Firefox (Windows and Ubuntu) but doesn't work in I.E.6., at least the page that I made didn't work.
I'm interested in Odeo. Is it a Windows or Linux item?
Do the files work in Windows I.E.6.?

Thanks for the help,
Phil

---

