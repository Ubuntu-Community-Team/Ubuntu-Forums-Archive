---
title: "Problem with Neverwinter Nights!!!"
date: 2006-03-12
forum: Gaming &amp; Leisure
---

### Post by WackToMack on 2006-03-12
Hello everyone!  I have a problem playing with my Neverwinter Nights installation.  I followed the "Installing From An Existing Windows Install" directions found [HERE]("http://nwn.bioware.com/downloads/linuxclient.html").  Everything seemed to go real smooth.  Then I ran the game.  It ran perfectly.  It was updated to the latest version too.  So, I played it for a while, just following the game tutorial and then BAM!  Everything froze.  I had to manually restart my computer by pressing the RESET button.  So I waited for my system to boot up again and ran the game again.  Everything was good for a while but then it froze again.  So I tried one more time and it froze yet again.  Everytime it froze I was in a different spot in the game.  I don't kow why it's doing this or how to fix it so that's why I'm asking you for help.  I can't live without this game, that's why I'm so desperate.  My hardware specs are:

AMD Athlon XP 2800+
ATI Radeon X800XT w/ 256 MB
1 GB RAM
200 GB HDD Master
80 GB HDD Slave
Running Ubuntu "Breezy" 5.10

Oh, and if this helps, in the game's graphics options, I have the graphic detail set to maximum.  I'll try it in other modes too, to make sure that's not the problem.

---

### Post by sharperguy on 2006-03-12
I had this problem too.

I think you need to install the fglrx drivers for your graphics card.

Not that i'm entirely sure because im not sure about that card but heres the link:
[http://ubuntuforums.org/showpost.php?p=423584]("http://ubuntuforums.org/showpost.php?p=423584")


make sure you follow the instructions EXACTLY because when I tried it the first time it didnt work and i spent ages looking for a fix, but i gave up and tryed the whole process from the beggining again and it just worked.

---

### Post by WackToMack on 2006-03-12
[QUOTE=sharperguy]I had this problem too.

I think you need to install the fglrx drivers for your graphics card.

Not that i'm entirely sure because im not sure about that card but heres the link:
[http://ubuntuforums.org/showpost.php?p=423584]("http://ubuntuforums.org/showpost.php?p=423584")


make sure you follow the instructions EXACTLY because when I tried it the first time it didnt work and i spent ages looking for a fix, but i gave up and tryed the whole process from the beggining again and it just worked.[/QUOTE]

Hmm... I have already installed the fglrx drivers for my card.  Well, I think I have done it correctly... is there any way to check?

---

### Post by WackToMack on 2006-03-12
NVM... found out how to check...

> wacktomack@Linux:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X800 XT Generic
OpenGL version string: 2.0.5642 (8.22.5)
It looks alright... any other ideas on how to fix my game?

---

### Post by sharperguy on 2006-03-12
no soz.

It just works for me.

Try running glxgears and seeing what happens.

---

### Post by WackToMack on 2006-03-12
Results:

> wacktomack@Linux:~$ glxgears -printfps
57505 frames in 5.0 seconds = 11500.627 FPS
63456 frames in 5.0 seconds = 12691.094 FPS
63566 frames in 5.0 seconds = 12713.072 FPS
63584 frames in 5.0 seconds = 12716.732 FPS
63640 frames in 5.0 seconds = 12727.903 FPS
63566 frames in 5.0 seconds = 12713.091 FPS
63573 frames in 5.0 seconds = 12714.467 FPS
63536 frames in 5.0 seconds = 12707.175 FPS
63609 frames in 5.0 seconds = 12721.800 FPS
63594 frames in 5.0 seconds = 12718.654 FPS

wacktomack@Linux:~$

I don't know what could be wrong... everything looks good to me...

---

### Post by willis on 2006-03-15
I've been playing neverwinter nights for awhile in linux... and just recently i've started having freezes every 5 minutes or so.  i think it might have to do with an upgrade of the ati fglrx driver but i'm not sure how.

it's really a pain, as nwn is such a good game.

---

### Post by Coelocanth on 2006-03-15
One thing to check: turn off the shiny water option. ATI cards and shiny water do not play well together in NWN. This has solved crashing issues for many others. Hope it works for you guys.

---

### Post by leech on 2006-03-15
It's kind of funny that the shiny water does that to ATI cards, since the first cards to support the shiny water in Neverwinter Nights were the ATI cards.  Though that is the Windows version of the game.  Everything works flawlessly with nVidia cards.  I even had the game working with three screens in linux with the Matrox Parhelia (which still to this day won't play UT2004, at least last I checked a few months ago).

Leech

---

### Post by iheartmuseums on 2006-06-06
I'm having similar problems - play the game for 15 mins or so fine, and then it lags terribly and freezes up. It's only happened since I switched to Dapper, so it's a bit frustrating. 

fglrxinfo gives me this:
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9250/9200 Series DDR Generic
OpenGL version string: 1.3.1072 (X4.3.0-8.25.18)


and glxgears gives me this:
10262 frames in 5.0 seconds = 2052.325 FPS
11667 frames in 5.0 seconds = 2333.292 FPS
12658 frames in 5.0 seconds = 2531.584 FPS
12471 frames in 5.1 seconds = 2431.640 FPS
12193 frames in 5.0 seconds = 2438.202 FPS
11156 frames in 5.0 seconds = 2231.040 FPS


Which seems *really* slow. Any ideas?

---

