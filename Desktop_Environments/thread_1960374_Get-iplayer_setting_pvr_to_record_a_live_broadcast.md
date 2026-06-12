---
title: "Get-iplayer: setting pvr to record a live broadcast"
date: 2012-04-17
forum: Desktop Environments
---

### Post by XEtedBear on 2012-04-17
I'm trying to setup cron/get-iplayer pvr to record each of a set of regular broadcasts on BBC Radio 3, but I've reached the limit of my understanding. The discussions and examples I see in on-line documentation all seem to imply that the pvr function will, in essence, make a copy of a previously broadcast BBC programme (TV or Radio) which the BBC have now stored as a file that could be viewed again using their iPlayer.

I don't want to do this. It would be more straightforward just to use the -get function of get-iplayer to download this stored file except that the BBC stores these files at a medium level of quality in MP3 format. In contrast, when I capture the programme using my HiFi-quality FM tuner as it is being broadcast, I can set whatever quality I like - up to that of the broadcast, without any lossy compression methods for example. The only problem is that I have got to be there to start and stop the recording - inconvenient.

The more I think about it, pvr seems the wrong way: even if I could figure out how to set it up to capture a live broadcast, this would still be the feed put onto the web by the BBC, which will use the same, medium-to-poor-quality, recording of the iplayer files.

Maybe I should just setup cron to start Audacity at the required time - except that a lot of additional manual intervention would be requited to setup, record and save an Audacity project - all of which I would expect pvr to do.

So what's the solution?

---

### Post by Myrddin Emrys on 2012-04-17
'get_iplayer --type radio' should give you a high quality 320 kbps AAC with Radio 3. While this is indeed lossy compression, do you find it's subjectively worse than an analogue to digital conversion from your FM tuner?

---

### Post by XEtedBear on 2012-04-17
> **Myrddin Emrys said:**
> 'get_iplayer --type radio' should give you a high quality 320 kbps AAC with Radio 3. While this is indeed lossy compression, do you find it's subjectively worse than an analogue to digital conversion from your FM tuner?

No, I don't, not at my age. It would be unwise to argue that I can tell any difference - objectively. Subjectively, emotionally of course I think that FM is miles better - it must be, it's BBC engineers after all in charge of the companders; they know what they are doing, don't they? Oh, they've all retired you say?

Anyway,it's a moot point: surely this quality of signal is not available, digitally, from the BBC, is it? I thought that all those files stored by the BBC and accessible via get-Iplayer (or indeed BBC iPlayer) were MP3 at 192Kbps - or worse. Certainly I can hear the difference between recordings I capture through FM/Audacity and those same programmes listened to via iPlayer. The latter are, I am sure, perfectly acceptable to the yoof market listening via their iPhones - but that's not quite the same as a high dynamic range broadcast even through today's severely under-invested analogue FM service.

I haven't heard a convincing argument that DAB is any better, yet.

And, as I forgot to say, I thought that get-iplayer is an 'after the fact' tool - I can't listen (or, more importantly, record) live, as it were, with it, can I?

---

### Post by Myrddin Emrys on 2012-04-17
> **XEtedBear said:**
> Anyway,it's a moot point: surely this quality of signal is not available, digitally, from the BBC, is it? I thought that all those files stored by the BBC and accessible via get-Iplayer (or indeed BBC iPlayer) were MP3 at 192Kbps - or worse.

I believe it varies by station - hardcore classical gets the best stream :-)

[http://www.harbeth.co.uk/usergroup/showthread.php?1258-World-s-highest-quality-on-line-classical-music-feed-%28BBC-Radio-3%29](http://www.harbeth.co.uk/usergroup/showthread.php?1258-World-s-highest-quality-on-line-classical-music-feed-%28BBC-Radio-3%29)

[http://www.bbc.co.uk/radio3/hd-sound/](http://www.bbc.co.uk/radio3/hd-sound/)

get_iplayer seems to be able to access 320kbps Radio 3 recordings 'after the fact' with the '--type radio' argument (or at least vlc thinks the get_iplayer output has this bitrate). Some sort of re-coding goes on after the programme is downloaded by get_iplayer, but I think this is just swapping the container.

Example of a 320k iPlayer URL:

[http://www.bbc.co.uk/iplayer/episode/b01g4syn/The_Early_Music_Show_Martin_Peerson_and_John_Milton/](http://www.bbc.co.uk/iplayer/episode/b01g4syn/The_Early_Music_Show_Martin_Peerson_and_John_Milton/)

It's possible non-UK IP addresses don't get all the 320k stuff, and I've also seen some older discussions suggesting only the live stream was at this bitrate (maybe this has now changed?).

> **XEtedBear said:**
> I haven't heard a convincing argument that DAB is any better, yet.

Me neither!

> **XEtedBear said:**
> And, as I forgot to say, I thought that get-iplayer is an 'after the fact' tool - I can't listen (or, more importantly, record) live, as it were, with it, can I?

There is also live stream support, but I never use it this way:

[http://linuxcentre.net/get_iplayer-gets-live-bbc-iplayer-stream-support](http://linuxcentre.net/get_iplayer-gets-live-bbc-iplayer-stream-support)

---

