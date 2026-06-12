---
title: "Streaming asf files"
date: 2005-10-27
forum: Desktop Environments
---

### Post by Cybercool on 2005-10-27
Hello,

i'm not getting it working that i can stream asf files.
I installed gxine and win32codecs but everytime when i play a asf file i get libmpeg2 message.

What to do?

Greetings,
Cybercool

---

### Post by gw90se on 2005-10-27
They play fine for me in Totem. Have you tried it?

---

### Post by Cybercool on 2005-10-27
[QUOTE=gw90se]They play fine for me in Totem. Have you tried it?[/QUOTE]


How to get totem started up when opening an asf in firefox??

---

### Post by jrib on 2005-10-27
Some files refuse to work for me while others work fine.  Are you having problems with a scpecific file?  If you post a link I can let you know if it works for me or not.

---

### Post by Cybercool on 2005-10-27
[QUOTE=_jason]Some files refuse to work for me while others work fine.  Are you having problems with a scpecific file?  If you post a link I can let you know if it works for me or not.[/QUOTE]

And i also have problems with playing wmv files!

[http://media5.big-boys.com/content/nikeparidy.wmv](http://media5.big-boys.com/content/nikeparidy.wmv)


And i can't for example play this asf:
[http://www.msm.cam.ac.uk/phase-trans/2002/squash/MOVX001.ASF](http://www.msm.cam.ac.uk/phase-trans/2002/squash/MOVX001.ASF)

Greetingz,
Cybercool

---

### Post by drigloi on 2005-10-27
Neither of these links work for me even under Windows XP. Maybe you shouldn't ask Breezy to play them back for you ;) Maybe my XP is broken, but...

However I suggest you to search the forums after "mplayerplug-in". Due to my opinion it handles streaming media far better then totem/xine/gstreamer stuff. Especially the latest release.

---

### Post by joplass on 2005-10-27
[QUOTE=Cybercool]And i also have problems with playing wmv files!

[http://media5.big-boys.com/content/nikeparidy.wmv](http://media5.big-boys.com/content/nikeparidy.wmv)


And i can't for example play this asf:
[http://www.msm.cam.ac.uk/phase-trans/2002/squash/MOVX001.ASF](http://www.msm.cam.ac.uk/phase-trans/2002/squash/MOVX001.ASF)

Greetingz,
Cybercool[/QUOTE]

Install RealPlayer 10 from realnetworks not from synaptic.  That's what I did and now I can play any file under the sun with Xine.  Xine uses realplayer10 plugins to play such files.  
I will try your files tonight when I get home.

---

### Post by jrib on 2005-10-27
[QUOTE=Cybercool]And i also have problems with playing wmv files!

[http://media5.big-boys.com/content/nikeparidy.wmv](http://media5.big-boys.com/content/nikeparidy.wmv)


And i can't for example play this asf:
[http://www.msm.cam.ac.uk/phase-trans/2002/squash/MOVX001.ASF](http://www.msm.cam.ac.uk/phase-trans/2002/squash/MOVX001.ASF)

Greetingz,
Cybercool[/QUOTE]

The first link gives me a 404 so I tried [http://media5.big-boys.com/content/nikeparody.wmv](http://media5.big-boys.com/content/nikeparody.wmv) and that worked fine in totem, mplayer, and vlc.

The second one plays in both mplayer and vlc but not in totem.  Mplayer and vlc are both really good players.  Give them both a try and see which one you prefer (or keep them both!).

Also, do you have the libmpeg2-4 package installed and have you read: [http://help.ubuntu.com/starterguide/C/faqguide-all.html#codecs](http://help.ubuntu.com/starterguide/C/faqguide-all.html#codecs) ?  I would be sure to install all of those packages listed if you haven't already done so and then try again.

---

### Post by joplass on 2005-10-27
[QUOTE=_jason]The first link gives me a 404 so I tried [http://media5.big-boys.com/content/nikeparody.wmv](http://media5.big-boys.com/content/nikeparody.wmv) and that worked fine in totem, mplayer, and vlc.

The second one plays in both mplayer and vlc but not in totem.  Mplayer and vlc are both really good players.  Give them both a try and see which one you prefer (or keep them both!).

Also, do you have the libmpeg2-4 package installed and have you read: [http://help.ubuntu.com/starterguide/C/faqguide-all.html#codecs](http://help.ubuntu.com/starterguide/C/faqguide-all.html#codecs) ?  I would be sure to install all of those packages listed if you haven't already done so and then try again.[/QUOTE]

Same here.  I was able to play the second one with Mplayer and Totem but the first one gives and error.

---

### Post by Cybercool on 2005-10-28
Ok there it goed.

With gxine i couldn't get it work.
So i deinstalled gxine.
Then i looked what player play now. This was vlc but a little bit buggy.
So i installed vlc.
Then i looked what player played then. This was totem-xine. But it didn't play at all.
So i deinstalled totem-xine.
And then game mplayer that workes perfect.

Als the time al player where started when i looked at a streaming movie.
I saw the corner of the mplayer skin, but on top of that was the totem-xine, on top of that the vlc player, and on top of that the gxine player.

None or less, i made a mess out of it.

Thanks for you're help people.

Greetings,
Ivo Keizers

---

