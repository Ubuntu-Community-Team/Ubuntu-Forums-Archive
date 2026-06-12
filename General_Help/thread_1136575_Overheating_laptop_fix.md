---
title: "Overheating laptop fix?"
date: 2009-04-25
forum: General Help
---

### Post by wizardfait on 2009-04-25
I have an HP Pavilion ze4805us that LOVES to overheat. I've found in windows that if I use an application that lowers the CPU speed to 1.7 GHZ or lower, it won't overheat. I have added the panel application to manually change cpu frequencies (Now that it WORKS for my cpu (It didn't before)) and it works nicely...

Now, my question: Is there a way to have ONDEMAND cpu scaling, *BUT* limit it? This application only allows me to set it, or have ondemand for the full range.

This in unacceptable in my opinion.
Is there maybe a configuration file I can modify to tell it which frequencies are allowed or something so I can enable ondemand, but never let it go higher than 1.7GHZ?

Ubuntu 9.04

---

### Post by dtoronto on 2009-04-25
This has been addressed in another post.  

[http://ubuntuforums.org/showthread.php?t=597998](http://ubuntuforums.org/showthread.php?t=597998)

Hope this is what you're looking for

---

### Post by wizardfait on 2009-04-25
Thank you very much, but no. This is NOT what I need.

This is for enabling it, and explaining it... Which it is already enabled, as I can change the frequency, but the issue is that I need it to either report that it can NO LONGER use the higest frequency (Making it use the next one down) or tell the applet to ignore that top one.

Unless that thread answered it and I just totally missed it?

---

### Post by dtoronto on 2009-04-25
I don't know very much about this particular application, I doubt that there is a pre-configured setting for exactly what you're trying to do.  I imagine that you can edit the config files or write a simple script to help you.  Again I don't use this application, so I am not at all familiar with the config set-up but I doubt that it will be a pre-configured setting.

---

### Post by wizardfait on 2009-04-25
I realize there isn't a preconfigured setting, but could you maybe point me to where the configuration files would be for this application? I'm a bit if an Ubuntu noob.

Also, is there maybe a way to trick the device mentioned in that other post, as it points to the processor, but it still is a "file"... Is there maybe a way to override what the device its self says with a file of my own?

All I really need to do is just "delete" the first entry from that file, and I'd be perfectly fine. However another thing that comes to mind, this application registers most, but not all of the different levels my processor can be scaled to... Do you know why? In windows, using RMClock I can scale the multiplier all the way from 1x to (I believe) 24X without ANY instabilities. Yet this application only shows about 7 options I believe. (Including when I cat the available processor speeds)

---

### Post by wizardfait on 2009-04-26
Bump?

---

### Post by Wiebelhaus on 2009-04-26
Disassemble the cooling system and clean out the hair and lent from the copper parts , reapply thermal paste , re seat the heat sink and fan assembly. If your unsure about how to do this use google or take it to a PC repair shop and pay them to do it , We normally charge an hour for everything besides Toshiba's (because most of them are a pain to disassemble) and unless there's a fan failure (which would be addressed while the lap top is disassembled) it's always succesful , you cannot fix this with software nor is it softwares fault.

Cheers.

Oh yea , also they sale fan plates that sit underneath the laptop that help but don't solve the problem , the above suggestion of disassembly is an absolute.

---

### Post by wizardfait on 2009-04-26
> **sx66gns said:**
> Disassemble the cooling system and clean out the hair and lent from the copper parts , reapply thermal paste , re seat the heat sink and fan assembly. If your unsure about how to do this use google or take it to a PC repair shop and pay them to do it , We normally charge an hour for everything besides Toshiba's (because most of them are a pain to disassemble) and unless there's a fan failure (which would be addressed while the lap top is disassembled) it's always succesful , you cannot fix this with software nor is it softwares fault.

Cheers.

Oh yea , also they sale fan plates that sit underneath the laptop that help but don't solve the problem , the above suggestion of disassembly is an absolute.

There's a reason why I asked for the SOFTWARE solution. I have done this before. There is NOTHING wrong with the cooling system. The case design from the factory was poor, and caused the two fans to be totally covered up except for a VERY small area of one of the fans.

YES this can be fixed with software, and YES it is software's fault if it is not designed in such a way that we can't TRUELY control our computer how we wish.

I understand why you'd think what you're thinking for trying to answer my question, but I find it quite offensive that you would assume I don't know what I'm talking about and would rather a solution to a problem I did NOT ask for.
I simply asked for the solution to the software not working as desired, not the problem OF my laptop overheating. I've worked with it long enough to know what will and will not work with it. The ONLY solution to being able to use it and not have it overheat is to have its maximum processing power lowered without doing something drastic like cutting the laptop's case, setting it on a block of ice, or anything else of the like.

I have taken it apart and cleaned it before (Not that there was ANYTHING in it) and I even replaced the thermal paste with a much higher quality. ALL it did was make it lower back to idle temperatures faster, but does not otherwise modify the temperatures as the issue lies withing the fan/vent placement at the factory.

---

### Post by Wiebelhaus on 2009-04-26
> **wizardfait said:**
> There's a reason why I asked for the SOFTWARE solution. I have done this before. There is NOTHING wrong with the cooling system. The case design from the factory was poor, and caused the two fans to be totally covered up except for a VERY small area of one of the fans.

YES this can be fixed with software, and YES it is software's fault if it is not designed in such a way that we can't TRUELY control our computer how we wish.

I understand why you'd think what you're thinking for trying to answer my question, but I find it quite offensive that you would assume I don't know what I'm talking about and would rather a solution to a problem I did NOT ask for.
I simply asked for the solution to the software not working as desired, not the problem OF my laptop overheating. I've worked with it long enough to know what will and will not work with it. The ONLY solution to being able to use it and not have it overheat is to have its maximum processing power lowered without doing something drastic like cutting the laptop's case, setting it on a block of ice, or anything else of the like.

I have taken it apart and cleaned it before (Not that there was ANYTHING in it) and I even replaced the thermal paste with a much higher quality. ALL it did was make it lower back to idle temperatures faster, but does not otherwise modify the temperatures as the issue lies withing the fan/vent placement at the factory.

Your wrong. but good luck.

---

### Post by wizardfait on 2009-04-26
> **sx66gns said:**
> Your wrong. but good luck.

I'm sorry, are you telling ME, THE OWNER OF THE COMPUTER WHO HAS ALREADY DONE WHAT YOU SUGGESTED BEFORE, that I am wrong about MY OWN COMPUTER? Especially when you have NEVER seen it before?

Please, leave.

---

### Post by DeMus on 2009-04-26
> **wizardfait said:**
> I'm sorry, are you telling ME, THE OWNER OF THE COMPUTER WHO HAS ALREADY DONE WHAT YOU SUGGESTED BEFORE, that I am wrong about MY OWN COMPUTER? Especially when you have NEVER seen it before?

Please, leave.

I know you also will be angry to me as well, but sx66gns is totally right. He is trying to help you, but if you are so stubborn then nobody can help you.
The fact that you have bought crappy hardware is no reason to look for software, or different settings, to make it work. Start at the source, which is, according to you, a wrong design. There is too little air-flow to keep the machine cool. Now you want to lower the specs to keep it cool? You paid for a Mercedes and want to drive a Nissan? (no offence) You still have warranty on it, or is too old for that?

When people try to help you there is no need to get angry when you get an answer you don't want to read. Then just ignore it, or say this doesn't work, because ....
People here are willing to help, accept it or don't come here.

---

### Post by wizardfait on 2009-04-26
> **DeMus said:**
> I know you also will be angry to me as well, but sx66gns is totally right. He is trying to help you, but if you are so stubborn then nobody can help you.
The fact that you have bought crappy hardware is no reason to look for software, or different settings, to make it work. Start at the source, which is, according to you, a wrong design. There is too little air-flow to keep the machine cool. Now you want to lower the specs to keep it cool? You paid for a Mercedes and want to drive a Nissan? (no offence) You still have warranty on it, or is too old for that?

When people try to help you there is no need to get angry when you get an answer you don't want to read. Then just ignore it, or say this doesn't work, because ....
People here are willing to help, accept it or don't come here.

First off, no matter what I bought, what the problem is, and what results I ask for, if you are truely trying to help me, you would be answering the question I ask, not offering answers for other questions.

Second, not that it matters, because either way the answer would still be the same: I did not buy this laptop. It was given to me for free. It is MORE than 4 years out of warranty.

One of the main things about linux is taking control of your machine, have the CHOICE! If I CHOOSE to weaken my own computer to solve a problem, I should be able to, and allowed to without getting people insinuating that I'm stupid, and that my solution isn't an intelligent one because of their previous experiences.

So, can I please have people answer the question I ask, rather than justifying themselves and others, or offering me other solutions, unless they're relevant? (Meaning, I will accept other answers like "Oh, use this application instead:" as they are relevant to answering my question. I will not however accept answers like "Oh, just take a dremel tool to the bottom of the case, it's perfectly safe, etc." If I had the ability, and willingness to take such solutions, I would. But the solution I WANT is the one I have asked for.)

Edit: You also say that "The fact that you have bought crappy hardware is no reason to look for software, or different settings, to make it work."

I'm sorry, wouldn't that be a reason TO look for another solution? If the hardware bought obviously doesn't work, and I obviously am not buying a new set of hardware, wouldn't the next thing be to look for alternative solutions? (Software in this case)

If you want to use a car analogy then let me put it this way: If your tire can only handle you going 55MPH without blowing, but you can ONLY either go maximum speed, or stop in your car, but you CAN'T replace the tires... Even if your car CAN go 100MPH, wouldn't the next logical solution be to make your car only go 55MPH?

---

### Post by DeMus on 2009-04-26
> **wizardfait said:**
> First off, no matter what I bought, what the problem is, and what results I ask for, if you are truely trying to help me, you would be answering the question I ask, not offering answers for other questions.

Second, not that it matters, because either way the answer would still be the same: I did not buy this laptop. It was given to me for free. It is MORE than 4 years out of warranty.

One of the main things about linux is taking control of your machine, have the CHOICE! If I CHOOSE to weaken my own computer to solve a problem, I should be able to, and allowed to without getting people insinuating that I'm stupid, and that my solution isn't an intelligent one because of their previous experiences.

So, can I please have people answer the question I ask, rather than justifying themselves and others, or offering me other solutions, unless they're relevant? (Meaning, I will accept other answers like "Oh, use this application instead:" as they are relevant to answering my question. I will not however accept answers like "Oh, just take a dremel tool to the bottom of the case, it's perfectly safe, etc." If I had the ability, and willingness to take such solutions, I would. But the solution I WANT is the one I have asked for.)

Good luck.

---

### Post by Bios Element on 2009-04-26
Flaming people who are helping you isn't going to work. In fact you'll find people won't help you in the future.

---

### Post by Wiebelhaus on 2009-04-26
> **wizardfait said:**
> I'm sorry, are you telling ME, THE OWNER OF THE COMPUTER WHO HAS ALREADY DONE WHAT YOU SUGGESTED BEFORE, that I am wrong about MY OWN COMPUTER? Especially when you have NEVER seen it before?

Please, leave.

Lol , I actually have a 4805 I'm also a authorized HP , Sony , Toshiba , Dell , Asus , Gateway and Acer repair man, I also have MS , *Unix and cisco certifications. And have 7,000+ service orders under my belt , but whatever dude , your the man.

---

### Post by wizardfait on 2009-04-26
> **sx66gns said:**
> Lol , I actually have a 4805 I'm also a authorized HP , Sony , Toshiba , Dell , Asus , Gateway and Acer repair man, I also have MS , *Unix and cisco certifications. And have 7,000+ service orders under my belt , but whatever dude , your the man.

If this were true, then you yourself would see how and know that the fans on this laptop were NOT lined up properly with the vents in the case, and would understand that no matter how clean the inside of the computer is, if you're sucking air from a wall, you're not going to get any air.

---

### Post by Wiebelhaus on 2009-04-26
> **wizardfait said:**
> If this were true, then you yourself would see how and know that the fans on this laptop were NOT lined up properly with the vents in the case, and would understand that no matter how clean the inside of the computer is, if you're sucking air from a wall, you're not going to get any air.

The 4805 I have has been in service for years and I actually used it one summer to track live stock in the sun in 100 degree weather. The laptop was a work horse and was designed well other than it was ugly as sin.

---

### Post by bdoe on 2009-04-26
Let me see if I have all of this straight: You have a laptop that, due to bad hardware design, has inadequate cooling; and you want to be able to have dynamic processor throttling (Ondemand), but limit the top end to well less than 100%, to keep the thing from overheating. Yes?

How such a laptop made it past QA when it was developed is beyond me, but this *is *HP we're talking about :rolleyes:

What you need is an overclocking utility of some sort, except what you'd be wanting to do is _under_clock your processor. Check this link for tips: [http://www.econowics.com/linux/298/tutorial-overclocking-ubuntu-linux/](http://www.econowics.com/linux/298/tutorial-overclocking-ubuntu-linux/)

Okay, I cannot believe even HP would put out such a crappy design, so I'm guessing that, at some point of time in your laptop's life, its CPU had been replaced with a far faster one that exceeds the cooling capabilities of your hardware. The obvious solution to this is to replace the CPU with a slower one. It sucks that you don't have the BIOS options available to desktop systems, otherwise you could just underclock the processor in BIOS and call it a day.

---

### Post by wizardfait on 2009-04-26
> **sx66gns said:**
> The 4805 I have has been in service for years and I actually used it one summer to track live stock in the sun in 100 degree weather. The laptop was a work horse and was designed well other than it was ugly as sin.

Okay. Look at the attached image. THIS is the vent/fan.
Does that LOOK like a laptop who's fan can handle the incredibly-hot-running AMD Athlon XP, running at 2.1 GHZ?

---

### Post by wizardfait on 2009-04-26
> **bdoe said:**
> Let me see if I have all of this straight: You have a laptop that, due to bad hardware design, has inadequate cooling; and you want to be able to have dynamic processor throttling (Ondemand), but limit the top end to well less than 100%, to keep the thing from overheating. Yes?

How such a laptop made it past QA when it was developed is beyond me, but this *is *HP we're talking about :rolleyes:

What you need is an overclocking utility of some sort, except what you'd be wanting to do is _under_clock your processor. Check this link for tips: [http://www.econowics.com/linux/298/tutorial-overclocking-ubuntu-linux/](http://www.econowics.com/linux/298/tutorial-overclocking-ubuntu-linux/)

Okay, I cannot believe even HP would put out such a crappy design, so I'm guessing that, at some point of time in your laptop's life, its CPU had been replaced with a far faster one that exceeds the cooling capabilities of your hardware. The obvious solution to this is to replace the CPU with a slower one. It sucks that you don't have the BIOS options available to desktop systems, otherwise you could just underclock the processor in BIOS and call it a day.

Thank you, however unless I'm missing something, none of these applications will help me.

You are correct. The laptop's cooling system did somehow pass HP's QA. However, this is the STOCK CPU and cooling system.

And yes... Unfortunately whether it was like a desktop BIOS or not, HP decided to cripple this laptop's BIOS utility ABOVE AND BEYOND anything I've ever seen before. It's like the PlaySkool's rendition of a BIOS utility. =\

And again, whether the obvious solution is or is not to replace the CPU, the issue here is money. I want a free (Time not counting as a cost here) solution. As a college student, I don't have money to be throwing around, and if I can find the solution I'm looking for, this will be a free solution that will give me a reasonably powerful computer (Still 1.7GHZ) that I can use without fear of overheating. (Meaning I wouldn't have to do something, then stop every 5 minutes to let it cool a bit, then start up again)

---

### Post by bdoe on 2009-04-26
> **wizardfait said:**
> Okay. Look at the attached image. THIS is the vent/fan.
Does that LOOK like a laptop who's fan can handle the incredibly-hot-running AMD Athlon XP, running at 2.1 GHZ?
*twitch*

Are you absolutely sure that backplate is oriented correctly?

---

### Post by wizardfait on 2009-04-26
> **bdoe said:**
> *twitch*

Are you absolutely sure that backplate is oriented correctly?

Believe me, there is NO other possible way for the bottom part of the case to be oriented and have it still work/fit. I'm not going to go take pictures of the rest of the laptop, but it swoops up at the front... And unless I want my status lights, and wireless button in back, and my ports up front... (Not counting that the motherboard wouldn't cooperate) it's not going to go any other way. :P

---

### Post by Wiebelhaus on 2009-04-27
> **wizardfait said:**
> Okay. Look at the attached image. THIS is the vent/fan.
Does that LOOK like a laptop who's fan can handle the incredibly-hot-running AMD Athlon XP, running at 2.1 GHZ?

Don't forget about the rear.

---

### Post by wizardfait on 2009-04-27
> **sx66gns said:**
> Don't forget about the rear.

First off, not forgetting. This is a fan that sucks from the bottom, and disperses sideways.

Second, your laptop IS different than mine. That is why.

Either you have a different revision, but it was still called a 4805US, or yours is not the 4805US but rather JUST the 4805 or something else.

I'm not stupid, I know my laptop. You just happen to have a different one than I do.

---

### Post by Wiebelhaus on 2009-04-27
> **wizardfait said:**
> First off, not forgetting. This is a fan that sucks from the bottom, and disperses sideways.

Second, your laptop IS different than mine. That is why.

Either you have a different revision, but it was still called a 4805US, or yours is not the 4805US but rather JUST the 4805 or something else.

I'm not stupid, I know my laptop. You just happen to have a different one than I do.

I didn't say your were stupid , I just said your wrong , But your to hardheaded to help so I'm done wasting my time with this.

---

### Post by wizardfait on 2009-04-27
> **sx66gns said:**
> I didn't say your were stupid , I just said your wrong , But your to hardheaded to help so I'm done wasting my time with this.

No, but when you're telling me that I want a hardware solution to what is a DIFFERENT laptop than mine is, and I'm asking for something that you're not helping me with, of course I'm not going to be all gung-ho for going with what you're suggesting. You're answering a question I'm not asking. I even TOLD you that my laptop is different than yours, and by you continuing to try to prove me wrong by showing me pictures of YOUR laptop, you are insinuating that I'm too stupid to know my own computer, and that you don't believe that what I am saying is true, just because YOUR experience is different.

Just because you THINK you have more experience, and you THINK you are more certified/qualified than someone else doesn't mean you ARE or that you are ALWAYS right.

---

### Post by holodila on 2009-04-27
First off, nobody here _MUST_ help you. Just some people are willing to, and you should not offend them. Secondly, it happens that there is no such software. I believe the one you are using now is open source, so why don't you learn C/C++ and computer architecture and write a software yourself? BTW it would be a nice experience. =)

BTW, Maybe this will work? [http://ubuntuforums.org/showthread.php?t=597998](http://ubuntuforums.org/showthread.php?t=597998)

---

### Post by wizardfait on 2009-04-27
> **holodila said:**
> First off, nobody here _MUST_ help you. Just some people are willing to, and you should not offend them. Secondly, it happens that there is no such software. I believe the one you are using now is open source, so why don't you learn C/C++ and computer architecture and write a software yourself? BTW it would be a nice experience. =)

BTW, Maybe this will work? [http://ubuntuforums.org/showthread.php?t=597998](http://ubuntuforums.org/showthread.php?t=597998)

Never mind I found the solution. And there *IS* such software. Cpufrequtils. It's a matter of apt-getting it, then adding to rc.local cpufreq-set -u <Maximum speed>.

^Just so you guys can give this solution to anyone else that needs it rather than giving incorrect information.

---

### Post by abhiroopb on 2009-06-05
I have collated all the various posts regarding this overheating issue into one ubuntuforums post...please help advise there...

[http://ubuntuforums.org/showthread.php?p=7399158#post7399158](http://ubuntuforums.org/showthread.php?p=7399158#post7399158)

---

### Post by pigphish on 2009-12-01
This thread is very entertaining... :D   Bumped up against the couch and eating popcorn :popcorn:

Adding my 2cents ...  You may want to try using cpufreqd and cpufreq 
Then check out the settings in /etc/cpufreqd.conf 
It offers a lot of customization options. 

I am using Karmic Koala 9.10

Good Luck, George

---

