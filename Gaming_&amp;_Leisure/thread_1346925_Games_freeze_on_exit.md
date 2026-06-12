---
title: "Games freeze on exit"
date: 2009-12-05
forum: Gaming &amp; Leisure
---

### Post by h2z on 2009-12-05
I've been playing Battle for Wesnoth and Teeworlds but when I exit those games, they freeze. Being a native windows user, I launch system monitor, goto running processes and while looking at the game's process, under "waiting channel" it says "futex_wait". I was only able to do this with wesnoth since I run it in windowed mode, when in full screen I have to revert to terminal login and reboot from there (since I haven't figured how to 'kill' the game from terminal). Is there any fix for this problem? 

I've tried reading the futex manual but I couldn't understand much (if not all) of it...

---

### Post by h2z on 2009-12-10
bump anyone??

---

### Post by 5nak3 on 2009-12-10
as far as running from terminal goes if you go into terminal 1 using ctrl+alt+f1 on system freeze

you can run the command "top" to see the programs using the most cpu.

then if you press "k" you can select with program ID to kill by typing in the 4 digit number associated with it and finalizing this via "y" when asked to kill with signal 15.

Alternatively if you know for instance teeworlds is the problem you can run the following command

"killall teeworlds" again after doing the whole ctrl+alt+f1 login sequnce. Obviously the killall command will change depending on what program you are trying to kill. Also keep in mind if you are not 100% sure on the name of the program use the tab button so as the computer can help give you some suggestions so for instance if you typed "killall tee" and then press tab you should find that the command will be auto corrected to show "killall teeworlds" (assuming teeworlds is currently running)

Now onto the problem of freezing. I remember I had this same problem upon exit when i first install Karmic. I am not 100% sure on the fix as I sorted it out a couple of months ago however, I'm pretty confident that the problem is with an SDL library:

To fix this you should run:

"sudo apt-get install libsdl1.2debian-pulseaudio"

Doing this should install the SDL for pulseaudio as opposed to the already installed ALSA module and thus allow you to play and exit without any problems.

Please keep in mind that these are my experiences using only teeworlds, so your mileage may vary but I'm pretty sure that this should sort out your problems.

---

### Post by h2z on 2009-12-14
This seems to have fixed the Teeworlds problem. I had "libsdl1.2debian-ALL" installed previously...

---

### Post by 5nak3 on 2009-12-14
So i take it everything is running as it should be now?!

If so could you please mark the topic as solved so as other forum members know that  you have the solution.

Cheers!

---

### Post by h2z on 2009-12-14
Allready marked with "solved". I have only played wesnoth three times since this fix and no crashes yet, hopefully it stays like this :)

---

### Post by PhoneixS on 2010-01-06
> **5nak3 said:**
> as far as running from terminal goes if you go into terminal 1 using ctrl+alt+f1 on system freeze

you can run the command "top" to see the programs using the most cpu.

then if you press "k" you can select with program ID to kill by typing in the 4 digit number associated with it and finalizing this via "y" when asked to kill with signal 15.

....

.

Thank you very much. I had had the same problem.

Now, I know that ctrl+alt+f1 is for something more than write jokes :D.

---

### Post by Rugiero on 2010-06-17
> **5nak3 said:**
>  I'm pretty confident that the problem is with an SDL library:

To fix this you should run:

"sudo apt-get install libsdl1.2debian-pulseaudio"

Doing this should install the SDL for pulseaudio as opposed to the already installed ALSA module and thus allow you to play and exit without any problems.

Please keep in mind that these are my experiences using only teeworlds, so your mileage may vary but I'm pretty sure that this should sort out your problems.


Thank you very much it works for me in tux racer..

---

