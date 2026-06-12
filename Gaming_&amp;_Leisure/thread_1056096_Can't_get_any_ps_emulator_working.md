---
title: "Can't get any ps emulator working"
date: 2009-01-31
forum: Gaming &amp; Leisure
---

### Post by myromance123 on 2009-01-31
Hey there, Ima just bout to give up on trying to play ps1 games on a ps1 emulator on ubuntu 8.04...  :(

   I've been at this nearly all night. At first I had pcsx (and had the bios) but everytime I tried to run a game (be it through the cd drive or an image) the thing would just disappear...

  So I searched around and then followed Kethinov's guide [http://ubuntuforums.org/showthread.php?t=159987]("http://ubuntuforums.org/showthread.php?t=159987"), after 2 hours of trying this and that with it I thought I had it going but trying to load the images just wont work (dont even get me started about trying the cd drive!), it looks like its about to play and then it just terminates and this is what it gives me:

```
OmniJoy Init: You are using v1.0.0 build 8
Sound device not available!
XRequest.144: BadDrawable (invalid Pixmap or Window parameter) 0x3c00007
Missing ATI render-texture extension!ATI Technologies Inc.
RADEON X600 Series
Error OmniJoy Controller 1: No such file or directory
Segmentation fault
```

So I'm guessing using a ATI RADEON x550 graphics card is a major boo-boo.
 (Heck even before that I had tons of segmentation faults from not having this or that libs and packages...eventually I solved them)

  :-({|= 

So I tried my hand at using pSX. It looked simple enough. I followed this guy's guide [http://maketecheasier.com/guide-to-playstation-emulator-on-ubuntu/2008/03/19]("http://maketecheasier.com/guide-to-playstation-emulator-on-ubuntu/2008/03/19")

 [-X But who woulda thunk it?! It completely trips up on me when I try to set the BIOS...and hey how helpful, it doesnt give me any errors or nothing(Im running it through the terminal) it just goes ahead and vanishes to infinity and beyond!! [-(
 I checked around at it seemed as though I cant use pSX unless pulseaudio is removed, files names are changed and/or pulseaudio is somehow disabled..

=; It took me a day just to get my sound working because of pulseaudio so the heck Im not going to mess with it after getting it to finally work.

Yeah I know there's ePSXe and I have yet to try that one but Im not gonna waste good bed time on trying another possible failure.. I'll give it a go in the mornin (its way past midnight already...)


Has, by some miracle given down by The Almighty, anyone gotten either pSX or pcsx working on ubuntu 8.04 using an ATI graphics card and able to play actually ps1 cds or play using cd images??

 Would any of you be so KIND and MERCIFUL as to lead me to the path of ps1 GAMING ON UBUNTU!??!?!

Thank you for your time( I will reply to (if there is anyone to reply to) any repliers of my thread after I wake up from my calming slumber)

 Hey if you know for sure theres no way to get this running for me then let me know so I dont waste my time. 

  I have a ps1 but the stupid memory slot randomly deletes my saves so hours of gaming or mins of gaming or days of gaming will suddenly vanish and my ps2 doesnt like ps1 memory cards so I cant save....

Also welcome are workarounds to playing ps1 games on ubuntu with ATI without emu's (give me all you got!!! SERIOUSLY!!)

[-o< May the Ubuntu ps1 community hear me [-o<

---

### Post by myromance123 on 2009-02-01
Bump.

 I tried epsxe too, and it gives the usual "I'll just disappear and not run" event when I try to run games be it with an image or cd.

 Guess I'm on my own here eh?
I'll check back once in a while hoping that someone will help me...
   Other than that I'll just try half heartedly now ...

---

### Post by dfreer on 2009-02-01
All I can help with is pSX. On Ubuntu 8.10, you need to stop pulseaudio in order for pSX to work. On a 64-bit install, you will also need to install ia32-libs and the 32-bit libgtkglext libraries.

It isn't removing pulseaudio, it's just stopping it. IIRC:
```
killall pulseaudio
```
Should stop pulseaudio (check your running processes to make sure), and then:
```
pulseaudio -D
```
Should start pulseaudio again. If nothing else a reboot will restart pulseaudio.

---

