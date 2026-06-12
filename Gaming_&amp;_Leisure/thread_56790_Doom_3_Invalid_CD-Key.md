---
title: "Doom 3 Invalid CD-Key?"
date: 2005-08-14
forum: Gaming &amp; Leisure
---

### Post by seethru on 2005-08-14
In my quest to get WoW working, I decided I'd check to make sure OpenGL, and my sound, was indeed working fine by installing something that would run natively in linux.

Well, Doom 3 loads, sound is a bit choppy in alsa, and non-existant in oss, which I've heard I can fix in the config, HOWEVER, it refuses to accept my cd-key. I received my copy of Doom 3 w/ my BFG 6800GT, and the input window in linux doesn't have the same amount of spaces. I'm quite baffled, and starting to get annoyed w/ all this lol.

---

### Post by Slugger on 2005-08-14
[QUOTE=seethru]In my quest to get WoW working, I decided I'd check to make sure OpenGL, and my sound, was indeed working fine by installing something that would run natively in linux.

Well, Doom 3 loads, sound is a bit choppy in alsa, and non-existant in oss, which I've heard I can fix in the config, HOWEVER, it refuses to accept my cd-key. I received my copy of Doom 3 w/ my BFG 6800GT, and the input window in linux doesn't have the same amount of spaces. I'm quite baffled, and starting to get annoyed w/ all this lol.[/QUOTE]
 It should give the same amount of spaces try again you might of missed something

---

### Post by J.K.Makowka on 2005-08-14
You can also put in the CD-Key into a textfile in:
/home/user/.doom3/base

doomkey for the base Doom3 and xpkey for the expansionpack.

It needs to be the first 16 digits of your cdkey not seperated by anything (maybe in capital letters).

Last but not least, if you have a newer version (>=1.2 I think) than there is a automatic connection to the id-software Cd-key authentification server made upon start-up (which is disrespecting my privacy rights, since I am are not activly stating a multiplayer game or anything, which would require these sort of things)
So if your CD-key isn't legit or because of some other reason (I am not accusing you of software piracy, it could be just that your CD-key is somehow already in use or something like that), it will be also refused.
You can prevent this automatic connection, by installing Firestarter, and dissallowing connections to:
idnet.ua-corp.com:27650
Multiplayer will not work then of course ;)

---

### Post by seethru on 2005-08-14
[QUOTE=J.K.Makowka]You can also put in the CD-Key into a textfile in:
/home/user/.doom3/base

doomkey for the base Doom3 and xpkey for the expansionpack.

It needs to be the first 16 digits of your cdkey not seperated by anything (maybe in capital letters).

Last but not least, if you have a newer version (>=1.2 I think) than there is a automatic connection to the id-software Cd-key authentification server made upon start-up (which is disrespecting my privacy rights, since I am are not activly stating a multiplayer game or anything, which would require these sort of things)
So if your CD-key isn't legit or because of some other reason (I am not accusing you of software piracy, it could be just that your CD-key is somehow already in use or something like that), it will be also refused.
You can prevent this automatic connection, by installing Firestarter, and dissallowing connections to:
idnet.ua-corp.com:27650
Multiplayer will not work then of course ;)[/QUOTE]

hmmm, my cd-key is 15 digits and 5 digits after a /. Let me demonstrate.

xxx-xxxxx-xxxx-xxx /xxxxx

so are you saying I should use the digits within xxx-xxxxx-xxxx-xxx and then the first one in /xxxxx?

edit: just tried firestarter, no luck, I'm still getting invalid key.....

edit again: I decided to check my Doom 3 install on my windows partition. I copied over the doomkey file (from my windows partition), and it still asked me for a cdkey. I decided I'd check to make sure I could play doom 3 online in Windows, and yes I can...so I opened the doomkey file and the key inside does not match the numbers printed on the back of my jewel case.

---

### Post by J.K.Makowka on 2005-08-15
Have you contacted you graphiccard manifacturer? Not sure about BFG, but there have been a few cases lately where those graphiccard versions where not 100% compatible with the store versions.

Your key definitly seems strange, since it should have 16+2 digits.

---

### Post by seethru on 2005-08-22
[QUOTE=J.K.Makowka]Have you contacted you graphiccard manifacturer? Not sure about BFG, but there have been a few cases lately where those graphiccard versions where not 100% compatible with the store versions.

Your key definitly seems strange, since it should have 16+2 digits.[/QUOTE]
 finally fixed this today, I noticed another sticker INSIDE the case covered by a cd...

However, sound is not working at all now, unless I run it w/ +set s_alsa_pcm plughw:0,2, and then it's choppy :/

pcm device "dmixer" works fine in Cedega, however in doom3 if I have s_alsa_pcm set to dmixer I get no sound. I've killed ESD also.

```
------ Alsa Sound Initialization -----
dlopen(libasound.so.2)
asoundlib version: 1.0.8
opened Alsa PCM device dmixer for playback
failed to set 44.1KHz rate: Invalid argument - try ( +set s_alsa_pcm plughw:0 ? )
close pcm
```

---

### Post by alsimoes on 2005-09-21
I have a similar problem...

```
------ Alsa Sound Initialization -----
dlopen(libasound.so.2)
asoundlib version: 1.0.8
ALSA lib pcm.c:2068:(snd_pcm_open_noupdate) Unknown PCM dmixer s_driver alsa
snd_pcm_open SND_PCM_STREAM_PLAYBACK 'dmixer s_driver alsa' failed: No
such file or directory
dlclose
WARNING: sound subsystem disabled

--------------------------------------
```

---

### Post by skolnick on 2007-01-25
> **J.K.Makowka said:**
> You can prevent this automatic connection, by installing Firestarter, and dissallowing connections to:
idnet.ua-corp.com:27650
Multiplayer will not work then of course ;)

I had the same problem, but I did not install any firewall. Just added the following entry to my /etc/hosts file:

idnet.ua-corp.com 192.168.100.200

of course, there is no such IP on my LAN, and made sure that /etc/nsswitch.conf had the entry:

hosts: files dns

and voila! doom 3 single player working fine (but multiplayer does not work :()

Regards.

---

### Post by RomeReactor on 2007-01-25
This solved my sound problems with Doom3: Make a a launcher (right-click on the desktop) and put this on the "Command" section:

```
nice -n19 /home/sho/games/doom3-demo/doom.x86 +set s_driver oss
```

And replace the game's location with your own.

---

