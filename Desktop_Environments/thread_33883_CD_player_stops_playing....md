---
title: "CD player stops playing..."
date: 2005-05-12
forum: Desktop Environments
---

### Post by YourSurrogateGod on 2005-05-12
Ok, I've had this problem before in Gnome but I don't know why it keeps repeating itself. Every time that I put in my CD in order to listen to some music (it's a CD that I bought, not some cheap crap that I burned), the CD playing program simply stops playing the CD... it just stops and refuses to respond to any other form of user input. The software is the default that came with my Ubuntu installation (Applications -> Sound & Video -> CD Player), sorry that I can't give you the exact name I can't find it :roll: . I have to use Force Quit in order to have the application exit.

---

### Post by joncooper on 2005-05-12
Is it a copy protected CD by any chance?

Post the output of "dmesg" in a terminal, there might be some debug info to shed some light on the situation...

---

### Post by YourSurrogateGod on 2005-05-12
[QUOTE=joncooper]Is it a copy protected CD by any chance?[/quote]
How would I find that out exactly? I have this one CD that requires an executable to run while playing the music, but that's not the case here, so I guess it's not...
[quote=joncooper]Post the output of "dmesg" in a terminal, there might be some debug info to shed some light on the situation...[/QUOTE]
Sorry, I don't follow. How would you get this information? What's dmesg?

---

### Post by YourSurrogateGod on 2005-05-15
Does anyone else know what a dmesg is?

---

### Post by bruizer on 2005-05-15
Pretty good explanation of dmesg here:
[http://linuxgazette.net/issue59/nazario.html](http://linuxgazette.net/issue59/nazario.html)

Something else that you can try is opening a terminal, run "gnome-cd", and then try playing your cd. You will get more info sent to the terminal which you can post here. As soon as you get the error, type "dmesg | tail", and post that output as well.

---

### Post by bruizer on 2005-05-15
Also, for some more info after the error occurs, open /var/log/messages and see what jumps out at you.

---

### Post by kombipom on 2005-05-26
I'm having the same problem and it is with $#%ing "copy controlled" CDs.  They used to be OK in Linux so I started buying them again but now the swines appear to have done something else to stop me listening to the music I have paid for! (sorry for the rant).

starting gnome-cd from the command line gives 
** (gnome-cd:9839): WARNING **: Generic IO error

Output of dmesg | tail is

ide: failed opcode was 100
end_request: I/O error, dev hdb, sector 1090820
hdb: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdb: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdb, sector 210632
hdb: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
hdb: media error (bad sector): error=0x30
ide: failed opcode was 100
end_request: I/O error, dev hdb, sector 1091836

How do I get Ubuntu to ignore the extra data and just "see" the audio CD file system like a dumb CD player does?

---

### Post by feloc on 2005-07-26
My cd-player (gnome-cd) now also stops playing, it finds the cd ok but when it should start playing it, it just stops.

What should I do??

---

