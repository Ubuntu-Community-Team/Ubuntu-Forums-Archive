---
title: "Problem Running Neverwinter Nights (original CDs + SOU + HOTU)"
date: 2010-07-12
forum: Gaming &amp; Leisure
---

### Post by Struwelpeter on 2010-07-12
Hello there,

I've read Bioware's instructions and "Read before posting" recommendations. But nwn doesn't work. I wonder whether I could persuade a  friendly soul out there to help me try to find out what I'm doing wrong.

Here's  how I'm doing it:

1. I create a /nwn directory  (/home/myusername/nwn/)
2. I extract nwnresources129.tar.gz to /nwn
3.  I extract nwclient129.tar.gz to /nwn
4. I extract the four ZIP files  from the SOU disc to /nwn
5. I extract the three ZIP files from the  HOTU disc to /nwn
6. I extract nwclienthotu.tar.gz to /nwn
7. I  extract English_linuxclient169_xp2.tar.gz to /nwn
8.  I run sudo  chown -R username:username /home/myusername/nwn/
9. I run sudo chmod  -c -R 777 /home/myusername/nwn/
10. I do a md5 checksum test using  Bioware's data, and get "ok" for all files.
11. I run ./fixinstall  and I get no error messages at all.
12. Then I run ./nwn and get this  message:

Fatal signal: Segmentation Fault (SDL Parachute Deployed)
X  Error of failed request:  BadLength (poly request too large or internal  Xlib length error)
  Major opcode of failed request:  65  (X_PolyLine)
  Serial number of failed request:  13
  Current  serial number in output stream:  14

I never get any error message  while extracting, nor at any other stage. I always have the "overwrite  all" option checked on when doing extractions. I use Archive Manager to  do those extractions. I'm running Ubuntu Lucid Lynx.

I deleted  everything and re-did all those steps three times, now, and I still get the same "Fatal signal" message.](*,)    

I'd be most thankful for any insight as to what I could be  doing wrong!

Cheers,

S.p.

---

### Post by hikaricore on 2010-07-12
I remember having problems with NWN at first too, then I think I found this:

[http://nwn.bioware.com/forums/viewtopic.html?topic=656261&forum=72](http://nwn.bioware.com/forums/viewtopic.html?topic=656261&forum=72)

Sorry if it's info you've already gone through but that's all i remember.

---

### Post by oldrocker99 on 2010-07-12
A Segmentation Fault usually has something to do with a video driver...

:guitar:

PS--you DID modify the nwn script, right?

Here's how mine looks:
#!/bin/sh

# This script runs Neverwinter Nights from the current directory

export SDL_MOUSE_RELATIVE=0
export SDL_VIDEO_X11_DGAMOUSE=0

# If you do not wish to use the SDL library included in the package, remove
# ./lib from LD_LIBRARY_PATH
export LD_LIBRARY_PATH=:./miles:$LD_LIBRARY_PATH <--this is what works
#export LD_LIBRARY_PATH=./lib:./miles:$LD_LIBRARY_PATH <--this is the original line
./nwmain $@

---

### Post by Struwelpeter on 2010-07-12
> **hikaricore said:**
> I remember having problems with NWN at first  too, then I think I found this:

[http://nwn.bioware.com/forums/viewtopic.html?topic=656261&forum=72](http://nwn.bioware.com/forums/viewtopic.html?topic=656261&forum=72)

Sorry if it's info you've already gone through but that's all i  remember.

Thanks, but yeah, I had seen it. And that doesn't help much, as I don't have Diamond Edition (nor can I purchase it in my country, alas).


> **oldrocker99 said:**
> A Segmentation Fault usually has something to do with a video driver...



Oh? And... how do I fix it?

> PS--you DID modify the nwn script, right?

Here's how mine looks:
#!/bin/sh

# This script runs Neverwinter Nights from the current directory

export SDL_MOUSE_RELATIVE=0
export SDL_VIDEO_X11_DGAMOUSE=0

# If you do not wish to use the SDL library included in the package, remove
# ./lib from LD_LIBRARY_PATH
export LD_LIBRARY_PATH=:./miles:$LD_LIBRARY_PATH <--this is what works
#export LD_LIBRARY_PATH=./lib:./miles:$LD_LIBRARY_PATH <--this is the original line
./nwmain $@

I hadn't modified it, no!
But now I have, and I still get exactly the same message :-(

---

### Post by Struwelpeter on 2010-07-12
Erm... Changing that line as Oldrocker suggested implies that I should have my SDL files... where?

---

### Post by JDShu on 2010-07-12
are you using nvidia? About a year ago I found out that I had to use an older nvidia driver to get nwn to work.

---

### Post by hikaricore on 2010-07-13
> **JDShu said:**
> are you using nvidia? About a year ago I found out that I had to use an older nvidia driver to get nwn to work.

This should not be the case as I've been running it just fine with every nvidia driver released in the last couple years.
I'm not saying it's impossible, but it's unlikely that the driver version is to blame.

---

### Post by Struwelpeter on 2010-07-13
> **JDShu said:**
> are you using nvidia? About a year ago I found out that I had to use an older nvidia driver to get nwn to work.

Nah, my video card is an ATI Radeon X1250. Oldish and clumsy, but I ran NWN under Windows with it just fine.
At any rate, I think it would be worthwhile trying to tamper with the driver a bit. But since I'm a Linux newbie, I have to ask: how do I do it?

---

### Post by Struwelpeter on 2010-07-13
As Oldrocker had guessed, the problem indeed was the video driver! I apparently had installed the wrong one. Now it runs alright.
Thanks everybody for their replies!

Cheers,

S.p.

---

