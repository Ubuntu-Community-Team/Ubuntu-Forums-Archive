---
title: "Problem with TeamSpeak 2RC2"
date: 2005-08-14
forum: Gaming &amp; Leisure
---

### Post by direwolf on 2005-08-14
I have tried multiple times to install Teampseak2RC2 and unfortunately haven't had any luck getting it to run. I have seen various threads on sound issues once it runs, but I haven't even gotten that far yet. 

I go through the install (gui), and install it to the default directory /opt/TeamSpeak2RC2/. 

When I try to run it from the terminal an alert box pops up with the error message "Privileged Instruction". In the terminal, the error produces the following output: 
"Runtime error 221 at 08124224
./TeamSpeak: line 8: 16491 Illegal instruction     /opt/TeamSpeak2RC2/TeamSpeak.bin $*"

In the client log (~/.teamspeak/TSClient.log) there is the following: 
"12-08-05 22:43:01,10831,WARNING,All,TMainForm.FormCreate,Ex ception EPrivilege: Privileged instruction" 

Any help getting to TeamSpeak to run would be greatly appreciated. 

Best regards

---

### Post by Bloke on 2005-08-15
Have you tried extracting the files into your home directory?

I have always installed it that way, and have not had issues. Also, during the extraction (installation) I tell the installer not to create links for gnome / kde, rather I create a link manually.

---

### Post by direwolf on 2005-08-17
same error

---

### Post by Bloke on 2005-08-17
have you re-downloaded the [FILE](ftp://ftp.freenet.de/pub/4players/teamspeak.org/releases/ts2_client_rc2_2032.tar.bz2)?

---

### Post by direwolf on 2005-08-18
yep.  ](*,)

---

### Post by Calizza on 2005-09-04
I am also having these problems. I am a newbie to Ubuntu and Linux in general. I have set Ubuntu up as a dual boot with WindowsXP pro. 
One of the first things I wanted to do was get Teamspeak going. I downloaded the program, extracted it in my home folder and installed from the GUI. I can get TS to pop up one time if I go to preferences->sound and disable 'enable server startup'. At this time TS will come up but it will then freeze and I must use the FORCE option to get it to quit, and then it will not come up again...ever. I tried reinstalling TS and even the whole Ubuntu disto to no avail.

I would love to be one of the people to say they no longer need windows, I hope most applications do not turn out this way.

System specs: 
AMD 2500+ Barton
1gig pc3200ddr
Chaintech motherboard
Chaintech soundcard


I would appreciate any help
Thank you, 
Calizza

---

### Post by evilghost on 2005-09-04
[QUOTE=Calizza]I am also having these problems. I am a newbie to Ubuntu and Linux in general. I have set Ubuntu up as a dual boot with WindowsXP pro. 
One of the first things I wanted to do was get Teamspeak going. I downloaded the program, extracted it in my home folder and installed from the GUI. I can get TS to pop up one time if I go to preferences->sound and disable 'enable server startup'. At this time TS will come up but it will then freeze and I must use the FORCE option to get it to quit, and then it will not come up again...ever. I tried reinstalling TS and even the whole Ubuntu disto to no avail.

I would love to be one of the people to say they no longer need windows, I hope most applications do not turn out this way.

System specs: 
AMD 2500+ Barton
1gig pc3200ddr
Chaintech motherboard
Chaintech soundcard


I would appreciate any help
Thank you, 
Calizza[/QUOTE]

I can actually help you with this one.  The first problem you have is that your soundcard doesn't support hardware mixing and TS is trying to lock /dev/dsp which is already in use by ESD, or ALSA.  TS pukes, when you Force-Quit, you think you've stopped the application but in reality it's still running, well, TeamSpeak.bin is.  Basically, you need to open a terminal and type "killall TeamSpeak.bin" which will kill the zombie/defunct TeamSpeak.bin processes.  Usually when it vomits you'll end up with about 8 or so TeamSpeak.bin processes running.

The crux of the problem is that TS is still using the old method to acquire/lock a sound device, instead of using something like ALSA or OSS.  What this means is that if you don't have a card that is capable of hardware mixing you are out of luck running any application outside of TS with sound.

The key is to acquire a sound card with the emu10k1 chipset, if you have Sound Blaster Live 5.1 around you should be able to use that.  Newer Sound Blaster Live 24bit cards do not support hardware mixing.

What you see, and may not be aware of, is an increasing trend towards software mixing, where the vendor provides trash hardware under the guise of increased functionality and performance.  You'll see terms like "DirectSound", which simply mean you're offloading hardware mixing functions on the processor; software mixing.  It's a step backwards, but in reality, at what point is a 2.8 or 3.0Ghz processor fully taxed, even when playing robust games?  Win32 uses DirectX to software mix the sounds, consuming additional CPU resources.

I hope this helped.

---

### Post by Calizza on 2005-09-06
Thank you for the reply.

looks like I will need a new soundcard :(

---

### Post by evilghost on 2005-09-06
[QUOTE=Calizza]Thank you for the reply.

looks like I will need a new soundcard :([/QUOTE]

Consequently, I do have a surplus of emu10k1 cards I procured from E-Bay in an effort to help solve this exact same problem on some other folks systems like my father and brother-in-law, both who use TS.  I'm also a TS user and run a TS server for friends/family.

I'd be willing to send one your way for $15 (which is inclusive of shipping) if you PM me your address.

I sent one to Kemotaha, two are on the way to DancingSun, and am keeping three for me as hot-spares/direct friends.  That means I effectively have 5 available.

Note:  Not trying to make a profit, just wanting to break-even and help other Ubuntu users out.  The emu10k1 is a semi-rare card to find.

---

