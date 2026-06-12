---
title: "[SOLVED] Frets on fire not working."
date: 2008-06-17
forum: Gaming &amp; Leisure
---

### Post by diwas on 2008-06-17
Guys..i downloaded Frets on Fire in Ubuntu as well as in XP. In both the cases it is not working.

Ubuntu(7.10):
When i click the icon of the game nothing happens. Just nothing.

XP(Service Pack 2):
When I click the icon it executes and a song (instrumental) is played in the background and the following error comes:
(it is in the attachment)...if u cannot view it:


Traceback (most recent call last):
File "c:\users\proj\cx_Freeze-3.0.3\initscripts\console.py", line 27, in?
File "src/FretsOnFire.py", line 79, in ?
File "src\GameEngine.py", line 376, in run
File "src\Dialogs.py", line 1153, in showMessage
File "src\Dialogs.py", line 1043, in_runDialog
File "src\GameEngine.py", line 366, in run
SystemExit: 1



I want to play the game in both Ubuntu and XP...i need in both of them....please help me out.

---

### Post by diwas on 2008-06-20
....

---

### Post by FrozenFox on 2008-06-20
Let's get something straight here.

These forums are here because people are willing to give their time and energy to help others with their problems.

However, nobody is paid to help you. Nobody is obligated to help you in any way.

**Nobody.**

Replying to your own thread in a sarcastic tone such as that at the community who would otherwise attempt to help you if they knew the answer is extremely rude, backwards, and completely unwelcome. I was going to try to help out after I read the first post, but the second changed my mind. Perhaps you should try contacting the author themselves and ask for support, or be productive and file a bug report with ubuntu. Next time, try bumping it with a less hostile comment, such as "Bump" or "Any suggestions, then?".

---

### Post by diwas on 2008-06-21
Im sorry but i was frustrated about this. I couldnt do anything. I contacted the author but i dont know why they are not replyin.

Im sorry again...

Anyways thanks.


Hmm it worked with XP. I had to reduce the colour depth to 16bit from 32. I dont know why. Then the game executed. But it was way too slow. I reduced all the video and audio properties to the minimum level. After that the menu items were fast enough but the game was too slow. The sound and graphics were far apart from each other. So in short it wasnt playable.
Talkin abt ubuntu it hasnt worked still. The same problem continues with it.

---

### Post by Zimmer on 2008-06-23
Frets on Fire Requirements

    * 128 MB of RAM
    * A fairly fast OpenGL graphics card with decent drivers
    * Windows:Direct X compatible sound card

Not sure your 64mb integrated graphics comes into the category of a fairly fast OpenGL graphics card.
So I guess that could be the answer..
(Saw your plea for help on the 'Hey Guitar Players, Let's chat'  thread )

Regards
Zimmer

---

### Post by wootah on 2008-06-23
> **diwas said:**
> Guys..i downloaded Frets on Fire in Ubuntu as well as in XP. In both the cases it is not working.

Ubuntu(7.10):
When i click the icon of the game nothing happens. Just nothing.

XP(Service Pack 2):
When I click the icon it executes and a song (instrumental) is played in the background and the following error comes:
(it is in the attachment)...if u cannot view it:


Traceback (most recent call last):
File "c:\users\proj\cx_Freeze-3.0.3\initscripts\console.py", line 27, in?
File "src/FretsOnFire.py", line 79, in ?
File "src\GameEngine.py", line 376, in run
File "src\Dialogs.py", line 1153, in showMessage
File "src\Dialogs.py", line 1043, in_runDialog
File "src\GameEngine.py", line 366, in run
SystemExit: 1



I want to play the game in both Ubuntu and XP...i need in both of them....please help me out.

You have python all installed? I think the graphics card should be somewhat ok to play. I have an integrated 64mb GForce 4 and it runs things quite nicely. Try executing frets on fire from the command line. That should dump out a bunch of stuff for us to further diagnose with.

I believe the command is just [B]fretsonfire.

[/B]PS: I guess I missed all the nasty stuff above.

---

### Post by diwas on 2008-06-23
Thank you Zimmer and wootah for ur time.

As i said earlier it runs in XP, but not nicely, so it should run in ubuntu too wid more speed than in XP, i believe. Thus graphics card should not be a problem.

Wootah, by sayin "You have python all installed?" what do u mean? What and where should i install python. If python is not the default package in 7.10, i dont think i have installed it manually. 

Thank you.

---

### Post by wootah on 2008-06-25
> **diwas said:**
> Thank you Zimmer and wootah for ur time.

As i said earlier it runs in XP, but not nicely, so it should run in ubuntu too wid more speed than in XP, i believe. Thus graphics card should not be a problem.

Wootah, by sayin "You have python all installed?" what do u mean? What and where should i install python. If python is not the default package in 7.10, i dont think i have installed it manually. 

Thank you.

Hmm, looks like I jumped the gun. Python is a default package in Ubuntu. As I mentioned before, in Ubuntu, open up the terminal and type **fretsonfire**. If/when it crashes, you will see output in the terminal.

---

### Post by diwas on 2008-06-26
Error is attached.

Actually i had installed pulse audio and after that the audio was out. And now i think that this is the only reason FOF isnt workin!

---

### Post by wootah on 2008-06-26
> **diwas said:**
> Error is attached.

Actually i had installed pulse audio and after that the audio was out. And now i think that this is the only reason FOF isnt workin!

That looks like the issue here! I would start troubleshooting your sound now and see where you get with that. Try creating a separate thread and mark this one as solved.

---

### Post by diwas on 2008-06-26
Sorry but, how am i supposed to mark as solved? I tried for other posts too but couldnt.
And yes, i will create another thread. Thanks for the support.

---

### Post by wootah on 2008-06-26
No prob. At the top under thread tools (right side) is marked as solved. Good luck with the sound :)

---

### Post by diwas on 2008-06-27
Done!!
The link yo my sound problem is : [http://ubuntuforums.org/showthread.php?t=841654](http://ubuntuforums.org/showthread.php?t=841654)

I hope i will get response.

Thank you again!
I have whole lot of threads to mark as solved now!! hehe

---

