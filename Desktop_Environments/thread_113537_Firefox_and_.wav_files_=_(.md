---
title: "Firefox and .wav files = :("
date: 2006-01-06
forum: Desktop Environments
---

### Post by endy on 2006-01-06
I can't seem to get Firefox to play nice with pages that have embedded .wav files. It constantly asks to install a plugin but never finds one and just repeats asking.

I have mozplugger installed and can see in the "/etc/mozpluggerrc" file has settings for .wav files but if I go to the "about: plugins" page in Firefox the mozplugger plugin shows up but nothing is mentioned about wav.

Any ideas?

---

### Post by dcstar on 2006-01-06
[QUOTE=endy]I can't seem to get Firefox to play nice with pages that have embedded .wav files. It constantly asks to install a plugin but never finds one and just repeats asking.

I have mozplugger installed and can see in the "/etc/mozpluggerrc" file has settings for .wav files but if I go to the "about: plugins" page in Firefox the mozplugger plugin shows up but nothing is mentioned about wav.

Any ideas?[/QUOTE]
Mozplugger needs a program installed to play the .wav files - you can see what it tries to use in /etc/mozpluggerrc under the wav entry.

I installed the "bplay" package from Synaptic for my wav function, give that a try.

---

### Post by endy on 2006-01-06
Thanks for the tip, I tried it but it unfortunately didn't work :( 

I should have said that I also amended the mozpluggerrc file to use "aplay" to play the wav files (I made sure aplay plays them), here is the section of the mozpluggerrc:

```

audio/wav:wav: Microsoft wave file
audio/x-wav:wav: Microsoft wave file
audio/x-pn-wav:wav:Microsoft wave file
audio/x-pn-windows-acm:wav:Microsoft wave file
    controls: aplay "$file"
    controls: play "$file"
    controls: wavplay -q "$file"
    controls noisy: bplay "$file"
    controls: splay "$file"
    HELPER(xmms -e -p "$file")
    repeat noisy swallow(alsaplayer): alsaplayer -q "$file"
```

Either way, nothing "wav" wise shows up in the "about: plugins" page, I can't figure out what's needed :S

---

### Post by dcstar on 2006-01-06
[QUOTE=endy]Thanks for the tip, I tried it but it unfortunately didn't work :( 

I should have said that I also amended the mozpluggerrc file to use "aplay" to play the wav files (I made sure aplay plays them), here is the section of the mozpluggerrc:
.......[/QUOTE]
Here are the screenshots of my about: plugins (with the wav stuff):

---

### Post by endy on 2006-01-07
I got it, I amended the wav section in my /etc/mozpluggerrc file to the following (basically set up aplay and commented the others out):

```
audio/wav: wav: Microsoft wave file
audio/x-wav: wav: Microsoft wave file
audio/x-pn-wav: wav: Microsoft wave file
audio/x-pn-windows-acm: wav: Microsoft wave file
       repeat noisy swallow(aplay): aplay -q "$file"
#    controls: play "$file"
#    controls: wavplay -q "$file"
#    controls noisy: bplay "$file"
#    controls: splay "$file"
#    HELPER(xmms -e -p "$file")
#    repeat noisy swallow(alsaplayer): alsaplayer -q "$file"
```

Then I had to delete the  ~/.mozilla/firefox/pluginreg.dat file to have Firefox reload the settings and it works!

---

### Post by stratotak on 2006-01-07
just my opinion ,,but i find that using mplayer with the w3 codecs pretty much plays most video formats i want to watch..that along with realplayer for sites that require either windows media player or quicktime or realplayer..like  atomfilms.com...just in my experience mplayer with w32 codec sand mplayer mozilla plugins is all i reall need...

---

### Post by endy on 2006-01-07
I will probably regret setting this up as I'm sure there will be some horrible web pages with embedded wav files out there but I need it as I have a page set to monitor a group of servers and as part of the page it plays a wav sound file if a daemon stops responding or the server is under heavy load.

I am looking for a better solution but for now getting wav files working in Firefox will do :)

---

### Post by dcstar on 2006-01-07
[QUOTE=endy]I got it, I amended the wav section in my /etc/mozpluggerrc file to the following (basically set up aplay and commented the others out):
......
Then I had to delete the  ~/.mozilla/firefox/pluginreg.dat file to have Firefox reload the settings and it works![/QUOTE]
That last bit is always a problem, sometimes it is necessary, sometime it isn't.....   :???:

Anyway, good to see that it is now working!

---

