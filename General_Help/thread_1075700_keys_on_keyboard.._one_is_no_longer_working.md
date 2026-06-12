---
title: "keys on keyboard.. one is no longer working"
date: 2009-02-20
forum: General Help
---

### Post by forestwalkerjoe on 2009-02-20
Ok.. i have a wubi installed on my win XP home system.. its Ubuntu 8 10 and for the most part.. this is a very nice install. 
I have over the past few days , suddenly found a problem. I am sure there is a setting that will work this out .. some place.. but i have hunted and cant see anything that will help. 
As to my keyboard issue.. i am sure its simple enough.. for one of you who can figure it out. 
All the Keys work fine. It did have a problem with no number keys and numbers locking.. but i found that and set it up to work. 
On my standard Dell Multimedia keyboard.. which IS logged in the keyboard area.. every thing works.. Except if i am using RIGHT or LEFT SHIFT to create  a cap on the letter c. i am typing the letter c in lower case because i cant get it to use caps. i have tried with two fully working keyboards.. but each fails.. this problem doesn't happen in the windows side of my duel boot. it is also a recent issue. it was not so when i first installed a few weeks ago. So in one of the Updates.. i am sure.. some thing defaultedly changed and now i am at a loss to get it back. 
Please someone.. Do help me out.. i can hit caps lock and i get nothing.. for that letter only. AS YOU MAY SEE HERE>> I cAN DO ALL BUT THE LETTER c in caps. BTW.. it doesn't do the letter see in small by itself.. what i means is.. if i am not using caps lock or shift.. it types the letter c very nicely.. but i am used to typing Left shift then letter c to get a temporary c in cap. 
i am sure if i could find it.. there has to be a place to reset it to a default. 
Please.. any ideas? I type a lot.. and i can not keep going back to fight with this and correct it so that caps for the letter c are corrected. 

FWJ

---

### Post by Saggy Peanuts on 2009-02-20
I think I understand what your problem is. A bit of a strange one actually.
Im guessing that you've checked the model in System->Preferences->Keyboard hasnt changed.
I also have a Dell keyboard and I havent come across this problem. The model that I am using is Generic 105-key (Intl) PC

---

### Post by unutbu on 2009-02-20
SCIM is a keyboard input utility which can affect the way key presses are handled. Are you using SCIM? 

If not, try this:
[http://ubuntuforums.org/showpost.php?p=6649186&postcount=4](http://ubuntuforums.org/showpost.php?p=6649186&postcount=4)

As mentioned in that post, note that the suggested "solution" will reset all of your GNOME preference settings (such as background wallpaper and anything set in System>Preferences). If it fixes your keyboard problem, you'll have to redo your GNOME preference settings.

If it doesn't work, there are instructions in the same post for recovering your current GNOME preference settings, so it is a pretty safe thing to try.

---

### Post by forestwalkerjoe on 2009-02-20
well in my messin arround i messed up my sound system now. i had to have help to get the glitch in the 810 system to work out. 
BUT the good news is.. your link to the rename and reset Gnome.. worked. 
I am now rebuilding every thing i had in my desktop.. including my Ubuntu special effects.. which even though it was turned off.. reset and defaulted those too. 
there is a link to the page i had used to solve the pulse sound issue.. so i will go work on that.It hard to say thank you.. not because you didnt solve my issue.. but because it took hours of messing arround to get the sound on my system.. and now i have to go back and do that again.
BUT.. thank you anyway. I have the letter C back in Caps with shift again. I hope it doesn't disappear again when i do another system update/ download thing. 
FWJ

EDIT: i am still 5 hours later , working on the sound issue. 
I can not figure out what is up with this. I was able to finaly get the sound to come back on.. and then fix the issue with the flash player in Firefox.. but.. every time i reboot.. i lose it all again. Some one please .. please help me. 
I am getting very frustrated with the system here.

---

### Post by unutbu on 2009-02-20
Hi forestwalkerjoe, I am happy to try to help you with the audio problem, but I am not really that knowledgable about fixing sound issues.

Can you explain in more detail what you have tried? 

Do you believe sound was lost because of the renaming of .gconf and .gnome2? Or was it something else which caused the problem?

Which version of Ubuntu are you using? Hardy? Intrepid?

Please post the output of 
```

ls -ld   .gnome2   .gconf
```
This will allow us to check that the permissions are set correctly, at least at the top level.

Have you tried going to System>Pref>Sound and changing to ALSA (instead of Autodetect, OSS, or PulseAudio Sound Server)? Does sound work on this setting? If so, then reboot and see if it sticks. 

If that does not work, it would be best to start a new thread in the Absolute Beginner Forum with a title that includes the words "Pulse Audio". That way, people more knowledgable than I will take a look at your problem. Post a note here that you have done so and I'll find the new thread and try to help there.

---

### Post by forestwalkerjoe on 2009-02-21
> **unutbu said:**
> Hi forestwalkerjoe, I am happy to try to help you with the audio problem, but I am not really that knowledgable about fixing sound issues.




<<<<>>>>    Can you explain in more detail what you have tried? 


---------------------------------------------------------------------------------------------------------------------------
I am not good at describing exactly what i am doing.. but i will try. 
Ok.. bare with my lack of good terms here. I will tell you what i DO know works.. and see if you can help me KEEP it that way. 
My system is affected by the sound system glitch in 810 Intrepid. 
the only Solve i was able to get to work.. is the pulse audio fix. 
i had to Go to sounds.. set all sound playback stuff to Detect and the capture to pulse audio. the hardware default was Dell sound blaster (ALSA). then i had to open the Pulse audio Device chooser in APPS AUDIO/video.. and make sure it is running. I see it in the tray above near the Netconnection and volume area. so far.. if it connects.. there is no sound at all. except system sounds when i log in. 
BUT.. if i turn that off.. it asks for a connection.. gives a address.. which i learned i could errase.. but the sounds work. Even the Flash player sounds..which has been a problem for many in this version of Ubuntu. OH.. if i click on the icon that is for pulse audio .. it has a pull down.. default server, sink and source. i have to set the first one to OTHER.. default will not work. each of the other two must be on default. Then i need to open the manager.. and say disconnect. poof i have sound. BUT once i reboot.. the applet for PULSE AUDIO doesnt load.. and IF by some chance it does.. it reverts to its own defaults. It connects to some sort of server.. which overrides the sound properties that DO work. i have to Hit manager.. disconnect.. also HIT Default server area and choose other.. and so forth.. then it comes back. I have no idea how to Save these settings that work.. so they continue to work. Before i messed these up.. Today.. these were not working after the install.. i spent 8 or more hours a day for 3 days trying to fix them. and this link i will put in here.. was the [final solve]("http://ubuntuforums.org/showthread.php?t=789578"). I have retried this and its not changing anything this time. 



Do you believe sound was lost because of the renaming of .gconf and .gnome2? Or was it something else which caused the problem?

------------------------------------------------------------------------------------------------------------------
NO. i was hunting for the answer and messing with settings that seemed to make sense.. before i found your Help. 
--------------------------------------------------------------------

Which version of Ubuntu are you using? Hardy? Intrepid?
---------------------------------------------------------
810 Intrepid off disk i bought from Ebay. 

Please post the output of 
```

ls -ld   .gnome2   .gconf
```
This will allow us to check that the permissions are set correctly, at least at the top level.
-------------------------------------------------------------------------------

OUTPUT:
rj@ubuntu:~$ ls -ld   .gnome2   .gconf
drwx------ 5 rj rj 4096 2009-02-20 23:15 .gconf
drwx------ 8 rj rj 4096 2009-02-20 23:15 .gnome2
rj@ubuntu:~$ 


Have you tried going to System>Pref>Sound and changing to ALSA (instead of Autodetect, OSS, or PulseAudio Sound Server)? Does sound work on this setting? If so, then reboot and see if it sticks. 

If that does not work, it would be best to start a new thread in the Absolute Beginner Forum with a title that includes the words "Pulse Audio". That way, people more knowledgeable than I will take a look at your problem. Post a note here that you have done so and I'll find the new thread and try to help there.



----------------------------------------------------------------------------------------------------------------
I have already put in a thread or two in the past week or more on this sort of issue.. and got very little help. the link above was the best bet.. i just want to know how to save the settings that do work.. or find out WHY they are reverting to the other defaults on reboot. 
It was not doing that before i did the config thing. BUT the rest of my system is working much better now that we have done that. 
from what i understand.. pulse audio is a must in this version of ubuntu.. and flash has a change in it that requires some things for it to work on the Firefox browser in 810 as well.


FWJ

---

### Post by unutbu on 2009-02-21
I have read through your description of the problem carefully, and have thought and searched for a solution but have come up blank. I realize it is very frustrating when computers behave like this -- they are supposed to save us time, not waste it. :-/

Here are the two best options I can come up with:
[list]
[*]Create a NEW thread in the Absolute Beginner Forum. It is important that it be new, so as to ensure that a member of the Unanswered Post team gets a look at it.
[*]Save your data onto your Windows partition (outside of Wubi), or on external media like a USB flash key. Then reinstall. Since you said you had sound working before, this might be the easiest way.
[/list]

Good luck.

---

