---
title: "how do I make conky wait to start"
date: 2011-04-25
forum: Desktop Environments
---

### Post by wildmanne39 on 2011-04-25
Hi everyone,how do I make conky wait to start? I have read the post how to do it but when I try it says file not found. Can anyone help with this please? If you tell me how please be exact because I have tried several time and failed. Thanks to everyone in advance.

---

### Post by Rasa1111 on 2011-04-25
You mean when your machine boots up?
To have conky wait a bit so the rest of the desktop can load, and then have conky pop up? 

To do so..
Open a text editor, (such as Gedit)

copy and paste this into your open Gedit document..

```
#!/bin/bash
sleep 30 && conky ;
```

(change the "30" to however many seconds you want it to wait)

Then save the document named as > .conky-startup.sh
and save it to your home folder. 

Then go to "startup applications", choose "add" , and for the command, use the same thing as you named the file..
> .conky-startup.sh

Hope it helps.
If you need me to elaborate a little, feel free to ask.

---

### Post by wildmanne39 on 2011-04-26
Hi, thank you for your help. I can not get conky to start now, is does that script have to be made executable? and if it does how would I go about doing it. Thank you very much for your help.

---

### Post by Rasa1111 on 2011-04-26
> **wildmanne39 said:**
> Hi, thank you for your help. I can not get conky to start now, is does that script have to be made executable? and if it does how would I go about doing it. Thank you very much for your help.

No problem.. :)

ahh yes, You are right, Im sorry for forgetting that part.

Yes you need to make it executable. 

To do so...

Just go to the file, (if you named it what I said, it will be hidden in your home folder)

So go to your home folder,
press Ctrl H to show hidden files...
and find the file you just made..

Right click that file, go to "Properties"
and then to the "permissions" tab, and check the box that says "allow executing file as program"
[ATTACH]190043[/ATTACH]

Sorry for being forgetful! lol :P

---

### Post by wildmanne39 on 2011-04-26
Hi, thank you, I did exactly what you said and made the changes, but it still did not start or it is under my background where I can not see it, before creating the wait to load script it would start but it covered my background and I could not see any thing or click on anything one my desktop. I am new with conky, I copied someone else's script to get me started then I am going to make adjustments. There is several parts to this script it covers most of the screen can you tell me can all of that go in one .conky file or do I have to have I say like for the weather separate from the part that monitors my system? Thank you very much for your help so far.

---

### Post by Rasa1111 on 2011-04-26
hmmm...

 I am not the most well versed in conky myself..
and I often have to ask for help myself when things go wrong in conky.. lol

 I can only share the info that I have personally used 
(which isn't much) and that works for me.
Such as the conky startup script, or changing colors/text/background images, Simple things like that.

 But when problems occur.. 
I am probably as lost as you my friend! (Im sorry) lol

From what I do know..
Im pretty sure you do not need another .conky file for the weather. 

The weather section can (and usually does) go in the same file as the rest of the conky. 

 I however, am also having problems getting the weather in my conky.  
 I know what I need to do to get it in there, I just don't know exactly how to use all the code and stuff required for it. 

 **But** if I were to add the weather to my conky ,
All I would have to do is add another few lines to my .conky file, 
Not add or start a new file for it. 

 I guess we will wait to see if anyone more knowledgeable with conky pops in here, and if not...

I would suggest posting in one of the "conky" threads,
with your conky script, and maybe a screenshot of your setup and a description of your problem, and what you'd like done. 

 This is how I always get help with my conky! lol
Someone is usually around that is happy to help others get their conky setup properly. 
 and I am grateful for them! <3

 I will point you in the right direction if we don't get any other visitors to the thread. 

Sorry I cannot help more. :???:
But from my experience here..
*Someone* *will* be able to help and get you going! 
*fingers crossed* lol <3

Good luck my friend.
(here is my conky)~ that I got help with to make right! ;) <3

---

### Post by wildmanne39 on 2011-04-26
Hi, thank you for all your help you have been great, I will keep trying, I usually figure it out one way or another. Thanks again.

---

### Post by stinkeye on 2011-04-26
Post your config so I can test it.

---

### Post by wildmanne39 on 2011-04-26
Hi, thanks to everyone that helped me I figured out why I could not get it to start on boot, I really appreciate everyone's help.

---

### Post by Rasa1111 on 2011-04-27
good news!
So it's all working properly now?

 You said you'd figure it out, and you did! Nice job! :D

---

