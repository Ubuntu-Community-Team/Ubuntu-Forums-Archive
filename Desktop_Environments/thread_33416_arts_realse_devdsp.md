---
title: "arts realse /dev/dsp"
date: 2005-05-10
forum: Desktop Environments
---

### Post by dave9191 on 2005-05-10
I use skype from time to time. But skype is slow to make or accept calls when it cant get hold of the sound card and if it takes too long it will give me an error message. Ive tried running skype with the artsdsp command but i get choppy sounds and people cant hear me. 

What I want is a command that will release or pause the arts service from using /dev/dsp so that i can make the call and then continue to use sound in kde. would killing artsd do the trick, or would that leave a lot of unhappy programs willing to explode?

---

### Post by vdrmrt on 2005-05-11
Type in the console "artsdsp skype" this makes skype use the sound server.

---

### Post by dave9191 on 2005-05-12
[QUOTE=vdrmrt]Type in the console "artsdsp skype" this makes skype use the sound server.[/QUOTE]


Like I said in my first post Ive tried to use the artsdsp command but get choppy sound and my mic doesnt work.

---

### Post by engos on 2005-05-12
exactly the same problem to me :(

---

### Post by dave9191 on 2005-05-12
I found this on the skype website :) 
> 
aRts (Advanced Real-time Synthesizer)

This is KDE default. Whenever your aRts sound works, it means that Skype should, too. The only trick is to run Skype through artsdsp program.

You should start Skype as follows: in the directory where skype executable is located, type:

artsdsp -m ./skype

If your microphone does not work, or you get Segmentation fault when calling, check the full-duplex setting of aRts - in KDE Control Center | Sound & Multimedia | Sound System on Hardware tab there should be a Full duplex option, set it to on ("[x]"), then restart aRts and Skype.

If you hear echo and using aRts, try to decrease your aRts sound buffer size, go to Control Center | Sound & Multimedia | Sound System and decrease Sound buffer size to something under 200ms on General tab in Skip Prevention section.


That seems to have fixed the choppy sounds a bit and my mic works. Full duplex wasnt ticked. But now i have a 30 sec delay with my voice getting to the other end and the other end gets thru instantly. I dont know if it the skype network messing up, or arts being funny.

---

### Post by dave9191 on 2005-05-12
[http://www.skype.com/help/guides/soundsetup_linux.html](http://www.skype.com/help/guides/soundsetup_linux.html)

Might be useful too :)

---

### Post by fdoving on 2005-05-12
[QUOTE=dave9191]I use skype from time to time. But skype is slow to make or accept calls when it cant get hold of the sound card and if it takes too long it will give me an error message. Ive tried running skype with the artsdsp command but i get choppy sounds and people cant hear me. 

What I want is a command that will release or pause the arts service from using /dev/dsp so that i can make the call and then continue to use sound in kde. would killing artsd do the trick, or would that leave a lot of unhappy programs willing to explode?[/QUOTE]
 If you just want a plain answer to your question; the command is 'artsshell suspend'.

- Frode

---

### Post by dave9191 on 2005-05-12
[QUOTE=fdoving]If you just want a plain answer to your question; the command is 'artsshell suspend'.

- Frode[/QUOTE]

Thank you so much. I started messing about with killing artsd and having some weird effects on other apps. This is brilliant :D

---

