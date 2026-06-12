---
title: "Switched from DVI to HDMI KVM switch and now get odd behaviors."
date: 2022-10-08
forum: Desktop Environments
---

### Post by nosmadar on 2022-10-08
I recently swapped out my existing KVM switch that handled DVI displays for one that handled HDMI displays [Tripp-Lite: B005-HUA4] and I swapped out my DVI monitor for an HDMI monitor [ASUS LDC HDMI].  Suddenly my Linux PCs started exhibiting some unwanted behavior.

I have two Linux boxes attached to this KVM Switch, running: Ubuntu  18.04.6(Intel cpu), and Ubuntu 22.04.01 (AMD cpu) and they both now exhibit a couple of really Annoying behaviors.
I did do a test ,where I hooked the Ubuntu 18.04.6 pc directly to a  Keyboard, Monitor and mouse and...Lo and Behold, the annoying behaviors are gone. I can confirm that it's the KVM switch

1) When I have text in the text editor and I hold down the secondary mouse key and drag it over some text to select it, a small window appears over the text which appears to be magnifying the text.  What is this and how do I get RID of it?  I have attached a picture, had to take it with my Phone. 

2) Sometimes I now see Tooltips for Applications (Rhythmbox, Gedit, FileManager) that just sit there even when that application is minimized. I can't get rid of them unless I open the pull up the window for that application again and press the Escape key.

3)  "Native" windows (Gedit Text Editor, File Manager) will No longer allow it's windows to be moved off screen.  As opposed to Libre Office.  So I can take a spreadsheet window and drag it so only half of it is showing, the rest is off screen. 
I have attached screen shots of both symptoms (one is from my Phone, that was the only way to capture it).


I looked at the "Universal Access" menu under System Settings and the only feature I have enabled is Repeat Keys. 
And....I turned off "Repeat Keys"..and the Tool Tips now appear, but do not linger until the Escape key is pressed.
<grrrrrrrrrr>  (I like my 'Repeat Keys' it makes it harder to type things like:   "grrrrrrrrrrrrrr..."  :)   -- trying to maintain a sense of humor about all of this.

Any ideas about what to look at?
Is there anything else I can do in Linux or do have to chase this with the KVM Switch manufacturer.

Thanks,
Rob

[ATTACH=CONFIG]291103[/ATTACH][ATTACH=CONFIG]291104[/ATTACH][ATTACH=CONFIG]291105[/ATTACH]

---

### Post by DuckHook on 2022-10-14
A very late reply, but for what it's worth:

The DVI standard is a computer monitor standard. Though now showing its age, it is simple, direct, efficient and was developed to pass video signals from display cards to monitors as accurately as possible. Due to this clear mission, it lends itself to good, honest engineering and doesn't give much trouble.

The HDMI standard is a media industry standard. It is complex, convoluted, inefficient and was developed, not for veracity, but to encrypt content against pirating. It was originally designed for low bandwidth TVs, is hostile to computer monitors, and is basically poor, compromised engineering that gives lots of trouble.

Accordingly, an HDMI signal is a fussy little beast that requires careful handling and even then can still be easily corrupted, often in ways that are devilishly hard to trace or diagnose.

Your KVM switch is likely not passing the HDMI signal properly. Even costly high&#8209;end KVM switches are known to fail because the HDMI standard is designed to resist exactly the sort of signal splitting/copying/hijacking techniques that KVM switches need in order to do their magic.

You can bug your KVM switch manufacturer (as you stated) but good luck with that, or you can consider a few other alternatives.

[LIST=1]
[*]Go back to DVI if this is possible.
[*]Use DP, which, like DVI, was designed from the ground up for monitors. Almost all video cards have Display Ports these days, as do most computer monitors. You would have to change to a DP KVM switch though.
[*]Try a different KVM switch and hope for the best.
[*]Forego the KVM switch and hook directly to the monitor. Some monitors have multiple HDMI ports. There's nothing you can do about the keyboard and mouse, but I work around the problem by physically unplugging those two inputs from one computer and plugging into the other. Linux systems are designed to handle such hot unplugging/plugging elegantly.
[/LIST]

---

### Post by nosmadar on 2022-10-16
Not too late at all...

Thanks! 
You have solved two mysteries with one answer.

First:  I've always wondered what DP was for if we had HDMI?  To an unfamiliar eye, the plugs look almost the same - I was very puzzled when I got my most recent laptop update from my employer.

Second: what to do about my problem - I will probably pester the KVM switch manufacturer since my audio output doesn't work either, and then give up and switch to DP.   I need to get an different KVM switch anyway since likely they won't be able to do anything about the audio.  And the old DVI KVM switch was only a 2-port and i need at least 3 now so, no going back.

---

### Post by DuckHook on 2022-10-16
One of the frustrating "tricks" that HDMI uses to discourage signal hacking is that it will pass video but not audio. This has happened to me on some occasions for reasons as simple as a substandard HDMI cable or a loose HDMI port connection. As mentioned, HDMI's anti-piracy measures have the effect of making the platform extremely brittle. The slightest deviation from a pure signal is treated as a hacking attempt.

If you have DP on both card and monitor, then you are better off using DP. It is more robust, more versatile and has better throughput. On more recent DP standards (which all new-ish card and monitor OEMs adhere to), you can even daisy-chain monitors (though you need the right monitors, cards and cables). That's because the DP signal is not encrypted and doesn't carry any anti-piracy baggage. It is also better designed because it was put together by engineers; not media industry flywheels and lawyers.

Leave the HDMI for your TV and Bluray player/streaming box. They use HDMI because they don't have any other choice. Where the choice exists, avoid HDMI.

---

