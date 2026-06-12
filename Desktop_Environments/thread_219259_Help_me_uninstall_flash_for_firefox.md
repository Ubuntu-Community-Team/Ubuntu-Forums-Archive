---
title: "Help me uninstall flash for firefox"
date: 2006-07-19
forum: Desktop Environments
---

### Post by IndigoMontoya on 2006-07-19
Help!  I tried to change the volume on a youtube video with the slider and now I get no audio at all (only in youtube - other things work fine).  I have restarted the browser and computer to no avail.  My thoughts are to uninstall and reinstall flash.  SOooo using both apt-get and synaptic I uninstalled everything with the word flash in it (flashnonfree, mozplugin-flash, gstreamerflashplugin - the names are probably wrong, but the idea is there).  But flash still works fine!  I cant get this damn thing uninstalled!  


I saw a post about needing /usr/lib/mozilla-firefox/plugins/libflashplugin.so and /usr/lib/mozilla-firefox/components/flashplugin (or something along those lines) and they are not there!  I know people have had a hard time getting flahs to work, but I think I am the first person who cant break it! ](*,) 

Any ideas on how to uninstall it (so I can then install it again) or better yet, just get my youtube volume restored, would be GREATLY appreciated.

Thanks!

---

### Post by mattisking on 2006-07-19
Are you running Dapper? If so, you need to go here:
/usr/lib/firefox/plugins/

That's where any of the packages will install it. Let me know what's listed there just in case. However, if you've ever ventured to a page where it's installed by popping up and asking you if you've installed it... then you need to look here: ~/.mozilla/plugins/

You'll probably see the files flashplayer.xpt and libflashplayer.so
Deleting those in addition to the ones I mentioned earlier should totally wipe it out on your system.

---

### Post by IndigoMontoya on 2006-07-19
Well that did the trick....kind of.

It uninstalled flash, which is what I really was asking of you, but when I reinstalled flash youtube still wouldnt give me sound (while pandora works fine).  I have tried clearing all my cookies for youtube.  Is there a way that flash is storing settings for youtube, and can I reset them?

Thanks again.

Oh I also tried installing via apt and then removing that and installing via firefox all to the same issues. just fyi

---

### Post by scxtt on 2006-07-19
seems to me youtube isn't compatible anymore w/ the v.7 flash plugin (for sound that is) ...

---

### Post by IndigoMontoya on 2006-07-19
I dont think so.  It is waaaaay to coincidental for that to be true.

I was watching a video last night - sound was fine.  I saw something that looked like a slider for volume control (but the graphic was only partly formed), I tried to turn it up.  BAM! no sound.

---

### Post by scxtt on 2006-07-19
or since v9 was released (for Windows/Mac) they're using it ... meaning 'yesterday' compatible w/ v7 - 'today' not compatible w/ v7 ... and i can see that happening for 2 reasons:

1. i used youtube to watch Seth MacFarlane give his speech @ harvard - i used v7 of flash player in firefox (1.5.0.4)
2. i was at work yesterday, on XP, saw some youtube stuff - seemed to work fine ... i come home, using firefox beta2 and v7 flash = no sound ... even tried it in firefox 1.5.0.3, no dice ...

and i've already seen some flash saying it requires v9 ...

---

### Post by IndigoMontoya on 2006-07-19
Wow! well ok.  I guess that is a wierd coincidence.  

oh well.  I still get video, maybe that will be good enough for most things until monkees fly out of my butt - Oh I mean they release flash 8.5 err 9 or whatever for linux (j/k)

ps that seth macfarlane thing was pretty funny.  I was trying to watch some clips of "an evening with kevin smith"  I have seen it many times, but it always cracks me up!  When he does the prince documentary....well lets just say its comic GOLD!

---

### Post by scxtt on 2006-07-19
yeah, it's a bummer about the whole v9 thing - i hope adobe doesn't sit on their butts too long when it comes to Linux ...

---

### Post by free10 on 2006-07-19
I ran into the same thing today with youtube. It has been working fine for me including today. I tried to adjust the sound up a little "on the partially formed" sound slider and it muted the sound and can't get it back so far. Still working fine on other sites. Considering I had sound on the video I was watching and then lost it at the time I tried to adjust it I don't see it as not having the right flash software problem.--Dwight

---

### Post by IndigoMontoya on 2006-07-20
I agree the coincidence factor is very high.  But I asked a friend and he doesnt have sound either.

---

