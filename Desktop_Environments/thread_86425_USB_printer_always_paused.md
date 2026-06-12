---
title: "USB printer always paused"
date: 2005-11-05
forum: Desktop Environments
---

### Post by Gowator on 2005-11-05
My Samsung printer (ML-1210) keeps going to sleep.  
I have tried configuring through Gnome and KDE and CUPS and although it is detected fine (and has worked on other distro's fine) I keep getting problems connecting to 

```
paused: Unable to open USB device "usb://Samsung/ML-1210": No such device
```

I have deleted and reinstalled using cups, KDE panel AND the Gnome printer tool.

edit skip to the last page if you have the problem where the solution is described.

---

### Post by Gowator on 2005-11-05
hello ?

---

### Post by Gowator on 2005-11-06
??

---

### Post by Gowator on 2005-11-06
Does anyone have any idea other than reinstalling Debian?

---

### Post by Gowator on 2005-11-06
Does anyone have a working USB printer in ubuntu ?  

Does anyone read these forums?

---

### Post by Takis on 2005-11-06
You know, funnily enough, people who regularly browse these forums also tend to have lives, and as such, aren't necessarily checking posts every 5 minutes. It can get quite irritating if you keep bumping your post so often - try to wait at least a day before bumping.

People will also probably not answer if they don't know the answer to your problem, so it's not a matter of people not seeing your post, it's just a matter of waiting till someone who has an idea to read it. Please try to be patient.

---

### Post by Gowator on 2005-11-07
Patient these forums are the worst forums for any distro i have ever used.  !!!!!!

The reason I am desperate is I need to print some legal forms out and I need to either use Knoppix live (so needed to start dowqnloading a while ago) or wiipe Kubuntu off the system...  

Thanks for your answer I now know to wipe Kubuntu off the box ....

edits just like my last simple question: [http://www.ubuntuforums.org/showthread.php?t=64501](http://www.ubuntuforums.org/showthread.php?t=64501)

"EDIT: edited for content and/or scope"

---

### Post by Takis on 2005-11-07
Riiiiight. Admins please lock.

---

### Post by ubuntu_demon on 2005-11-07
Gowator:

I have editted your post. 

Everyone on this forum is a volunteer. You have to show a little more respect. If you won't behave this thread will get locked. Being desperate is no excuse for treating people ill.

If people don't respond they probably don't know how to help you (or they think you are being rude).

---

### Post by Cufishing on 2005-11-07
[QUOTE=Gowator]Does anyone have a working USB printer in ubuntu ?  

Does anyone read these forums?[/QUOTE]
Yes, I have a USB printer that works flawlessly under Brezzy. I also checked the manufacturers web site, and downloaded their version of a Linux drive.
It was also auto detected under CUPS, and also installed and worked fine.

Maybe your MB chipset is not conducive with the new kernel and allows your USB to take a long deep nap.

Have you tried power off/on on your printer?

---

### Post by Gowator on 2005-11-07
[QUOTE=ubuntu_demon]Gowator:

I have editted your post. 

Everyone on this forum is a volunteer. You have to show a little more respect. If you won't behave this thread will get locked. Being desperate is no excuse for treating people ill.

If people don't respond they probably don't know how to help you (or they think you are being rude).[/QUOTE]
So lets get this right takis can **lie** about me and say I was bumping every 5 minutes which is **CLEARLY a lie** but I can't express dissatisfaction that the last 3 questions I have asked NOONE has even TRIED to answer????

Have you tried a search for threads with no answers its over 500!  Im guessing 500 is just the maximum count!  

The last three problems I have posted on these forums have all gone unanswered .. some for several weeks and the liar above then says Im bumping every 5 minutes.. 

If anyone should be modded he needs BANNIG for lying and personal attacks

anyway .... wft do I care I can always install a dsitro with a community behind it instead of one that just makes personal attacks and lies.


edits:

the point is that after waiting 24 hours I bumped my post and then a couple extra times.  I have made posts and waited 1 month and had NO ANSWER... then Takis sets off and starts telling me to just wait :: I WAITED 1 MONTH ON THE PREVIOUS QUESTION HOW LONG SHOULD I WAIT!!!!!!!!!!!!!!!!!!!!


HE THEN STARTS SPREADING LIES ABOUT ME IN ORDER TO PREVENT ANYONE ELSE ANSWERING ME AND THEN DEMANDS TO HAVE THE THREAD LOCKED WHEN ALL HE HAS DONE IS LAUNCH A PERSONAL AND DISHONEST ATTACK ON ME.  

there is no need to not only condone but encourage liars like Takis making personal attacks on me.  

All you have to do is look at the dates .. he is clearly lying and making dishoest personal attacks and should be banned yet you encourage him!

---

### Post by Gowator on 2005-11-07
[QUOTE=Takis]Riiiiight. Admins please lock.[/QUOTE]
Yeah brainbox. I guess if Im in danger of actually getitng a problem solv3ed its best to lock it...

By the way stop lyijng about me!  

Why not spend your time helping someone instead of spreading your hate and lies across the forum!

---

### Post by Gowator on 2005-11-07
[quote="ubuntu_demon"]
Erm which part of this is being rude....??
[/quote]
If you can explain then perhaps I can phrase it differently, perhaps this has a hidden meaning in English ... but to my knowledge this is not a rude question????



[QUOTE=Gowator]My Samsung printer (ML-1210) keeps going to sleep.  
I have tried configuring through Gnome and KDE and CUPS and although it is detected fine (and has worked on other distro's fine) I keep getting problems connecting to 

```
paused: Unable to open USB device "usb://Samsung/ML-1210": No such device
```

I have deleted and reinstalled using cups, KDE panel AND the Gnome printer tool.[/QUOTE]

---

### Post by Gowator on 2005-11-07
@everyone else and thx to Culfishing...

OK, the problem seems to be using the KDE printers settings to edit the PRINTER MANAGER...  when you astart it warns you some directives will be ignored.  This seems to be a problem bertween the ubuntu cupsd setitngs and the KDE system panel.  

Unfortunately after this the /etc/cups/cupsd.conf file is corrupt.  

I needed to share the printer and achived this by editing
/etc/cups/cupsd-browser.conf and changiung no to yes...
then editing the allow/deny of the 
/etc/cups/cupsd.conf by hand and adding my subnet instead of 127.0.0.1.  It accepts a netmask so if you have 192.168.1.x you can use 192.168.1.0/255.255.255.0

Hope that helps someone else.

---

### Post by ubuntu_demon on 2005-11-07
[QUOTE=Gowator]So lets get this right takis can **lie** about me and say I was bumping every 5 minutes which is **CLEARLY a lie** but I can't express dissatisfaction that the last 3 questions I have asked NOONE has even TRIED to answer????

Have you tried a search for threads with no answers its over 500!  Im guessing 500 is just the maximum count!  

The last three problems I have posted on these forums have all gone unanswered .. some for several weeks and the liar above then says Im bumping every 5 minutes.. 

If anyone should be modded he needs BANNIG for lying and personal attacks

anyway .... wft do I care I can always install a dsitro with a community behind it instead of one that just makes personal attacks and lies.


edits:

the point is that after waiting 24 hours I bumped my post and then a couple extra times.  I have made posts and waited 1 month and had NO ANSWER... then Takis sets off and starts telling me to just wait :: I WAITED 1 MONTH ON THE PREVIOUS QUESTION HOW LONG SHOULD I WAIT!!!!!!!!!!!!!!!!!!!!


HE THEN STARTS SPREADING LIES ABOUT ME IN ORDER TO PREVENT ANYONE ELSE ANSWERING ME AND THEN DEMANDS TO HAVE THE THREAD LOCKED WHEN ALL HE HAS DONE IS LAUNCH A PERSONAL AND DISHONEST ATTACK ON ME.  

there is no need to not only condone but encourage liars like Takis making personal attacks on me.  

All you have to do is look at the dates .. he is clearly lying and making dishoest personal attacks and should be banned yet you encourage him![/QUOTE]

If you read Takis' post tou can see that he didn't say that you posted every 5 minutes. He basically said that we are all volunteers and we don't necessarily check posts every 5 minutes. So have a bit of patience after the first bump. He didn't call you names or something.

You replied with a lot of ranting and calling him a lyer. Please show a bit more respect. I'm not banning anyone. But if you continue this behaviour eventually an admin may ban you.

Just be relaxed and people will help you if they can.

---

### Post by FLeiXiuS on 2005-11-07
I refuse to help *******...sorry!  Showing respect to others is a start for answers...

---

### Post by Gowator on 2005-11-07
[QUOTE=FLeiXiuS]I refuse to help *******...sorry!  Showing respect to others is a start for answers...[/QUOTE]
Thats right ,..

if I bump my post after a day or a month its not showiug repect.. I should have realised ....???

Read my first post on this thread and tell me why you REFUSED to help me back then?  

Now read this [http://www.ubuntuforums.org/showthread.php?t=64501](http://www.ubuntuforums.org/showthread.php?t=64501)
Tell em why you REFUSED to help back then....

then read this....
[http://www.ubuntuforums.org/showthread.php?t=79909](http://www.ubuntuforums.org/showthread.php?t=79909) amnd tell me why you REFUSED once again to answer the first post....

Am I meant to beg... what am I not writing to get someone to help?  

You are living on another planet if you think these forums are working.  
I waited over 1 month on  2 posts without any response and then some ass tells me to stop bumping my posts because people will get round to it ... seriously 2 months is way to long ....

Do you really find it surprising that I post and when noone has answered a month later I get sarcastic.  

Let me put it simply...Once its off the first page its lost....  
bumping after a day should be normal because you have OVER 500 unanswered posts....

Ubuntu has more specific problems than a clean distro because its messed about with especially the whole gtksudo disaster but any REAL questions are not answered (in my experience) only noobie questions like "how do I compile a kernel" or similarly mundane non distro specific stuff.  

The problem is you obviously refuse to deal with this
[http://www.ubuntuforums.org/search.php?searchid=2414193](http://www.ubuntuforums.org/search.php?searchid=2414193)

500 unanswered posts in only 5 days....!!!

---

### Post by Takis on 2005-11-07
Gowator, how can we help if we don't know the answer to a question? There's no guarantee anywhere on these forums that a question will be answered, it's not like it's paid technical support or anything. People aren't answering because they don't have an answer - yet.

---

### Post by Gowator on 2005-11-08
[QUOTE=Takis]Gowator, how can we help if we don't know the answer to a question? There's no guarantee anywhere on these forums that a question will be answered, it's not like it's paid technical support or anything. People aren't answering because they don't have an answer - yet.[/QUOTE]


I realise people are volunteers.  I do use other forums and have been a mod on several.  When I was a mod on mandrivausers.org we made an effort to clean out unanswered posts and even bump them to make sure someone would see them and answer them.  If I couldn't answer then often I would pm someone with expertise in that domain.  

Mandrivausers is not so large as Ubuntu forums, nor has it grown so fast.  

> Our members have made a total of 180555 posts
We have 12613 registered members
The newest member is XXXXXX
Most users ever online was 638 on Dec 13 2004, 10:03 AM

I believe the problem here is the right people are not seeing the right posts.  

Perhaps a few people see it who cannot answer then by the time the person who could have answered see's it its already slipped off the top 100 or so posts and they don't see it.  

I beleived this to be specifically a Kubuntu problem.  (indeed it turned out to be so) but it is hard to work out exactly the right place to put it?  hardware? software? 

It is my experience that after a day the chance of the posat being seen and answered is minimal therefore it needs to be bumped.  

There are different classes of question.  How do I change the wallpaper is likely to get 10001 answers but was never a critical issue ... being able to print or connect to the internet etc. are likely critical issues.

If these cannot be answered quickly then people will install something else or go back to Windows or ...

---

### Post by ubuntu_demon on 2005-11-08
[QUOTE=Gowator]I realise people are volunteers.  I do use other forums and have been a mod on several.  When I was a mod on mandrivausers.org we made an effort to clean out unanswered posts and even bump them to make sure someone would see them and answer them.  If I couldn't answer then often I would pm someone with expertise in that domain.  

Mandrivausers is not so large as Ubuntu forums, nor has it grown so fast.  
[/quote]

There is nothing wrong with bumping your post if there isn't any answer after a day. But if you keep bumping you have to realise maybe people don't know and if you then decide to go ranting there is less chance of help.

[QUOTE=Gowator]
I believe the problem here is the right people are not seeing the right posts.  

Perhaps a few people see it who cannot answer then by the time the person who could have answered see's it its already slipped off the top 100 or so posts and they don't see it.  

It is my experience that after a day the chance of the posat being seen and answered is minimal therefore it needs to be bumped.  

There are different classes of question.  How do I change the wallpaper is likely to get 10001 answers but was never a critical issue ... being able to print or connect to the internet etc. are likely critical issues.

If these cannot be answered quickly then people will install something else or go back to Windows or ...[/QUOTE]

We have a new mod bumping tool in place maybe this helps a little bit. We are a big forum and we are growing rapidly. But in practice people here are really helpful if they know how to help.

Doing something with critical classes might be a good idea. But a user always thinks their own problem is critical. And if forum staff would have to mark threads critical how would they judge which thread is critical and which is not ? This also costs a lot of time for the forum staff. Maybe you can elaborate on this in a positive way here :

[http://www.ubuntuforums.org/showthread.php?t=4409](http://www.ubuntuforums.org/showthread.php?t=4409) (instead of being negative)

---

### Post by ubuntu_demon on 2005-11-08
[QUOTE=Gowator]
You are living on another planet if you think these forums are working.  
I waited over 1 month on  2 posts without any response and then some ass tells me to stop bumping my posts because people will get round to it ... seriously 2 months is way to long ....
[/QUOTE]

Most of the users are happy. This is a forum based on volunteers. People try to help eachother. You aren't entitled to help. 

[QUOTE=Gowator]
Am I meant to beg... what am I not writing to get someone to help?  

Do you really find it surprising that I post and when noone has answered a month later I get sarcastic.  
[/QUOTE]

On these forums it isn't common to go ranting if people don't help you. Bumping after a day is ofcourse no problem. If you are nice to people they are nice to you and if they know how to help you they probably will.

---

### Post by ubuntu_demon on 2005-11-08
[QUOTE=Gowator]
I beleived this to be specifically a Kubuntu problem.  (indeed it turned out to be so) but it is hard to work out exactly the right place to put it?  hardware? software? 
[/QUOTE]

So let's get back on topic. What have you discovered about your problem ?

---

### Post by Gowator on 2005-11-08
[QUOTE=ubuntu_demon]So let's get back on topic. What have you discovered about your problem ?[/QUOTE]


The cupssys package contains a /etc/cups/cupsd.conf file which contains some directives which the KDE cups config applet can't handle.  

If you choose configure manager it warns you and says they will be ignored however they are obviously not.  (If you don't want to share the printer wiuth cups then this will not effect you.)

If you do then this prevents cups from starting....
[B]
The best thing is probably NOT to use this in the first place and just edit the cupsd.conf by hand
[/B]
If its too late to fix I  
deinstalled (purge) cupssys and everything related....  and l renamed the /etc/cups directory and reinstalled.  Readded the printer without touching configure manager and then edited /etc/cupsd.conf by hand adding my IP range for my home network.  (searched for every localhost and 127.0.0.1 and added  192.168.1.0/255.255.255.0  (using an example from the 192.168. RFC range)  

eg (The file is huge)  

Listen 127.0.0.1:631
Listen 192.168.1.10:631  (since this si the static IP of the CUPS server on eth0)

and 

BrowseAllow  192.168.1.0/255.255.255.0

etc. etc.

---

### Post by ubuntu_demon on 2005-11-08
so everything is fixed ? good

---

### Post by feathers on 2005-11-08
Strange, I have had the same problem. I thought it was related to the fact that I made the printer accessible for other computers on the net. Same error message but different printer. I solved the problem by removing and purging cups and reinstalling it. I has been working so far but if it happens again, I might think this is a bug.

---

### Post by Gowator on 2005-11-09
[QUOTE=feathers]Strange, I have had the same problem. I thought it was related to the fact that I made the printer accessible for other computers on the net. Same error message but different printer. I solved the problem by removing and purging cups and reinstalling it. I has been working so far but if it happens again, I might think this is a bug.[/QUOTE]


I guess you can also use the CUPS web config tool to add printers.  
Im not sure if its a bug or inconsistency between KDE and the Ubuntu default settings for the CUPS server.

---

### Post by axe on 2006-02-14
Can I just say, I don't know whether you people are still around that posted on this post, thank you!

This was exactly my problem, and only happened to me in the last two days, my printer was perfect, then it would keep going to sleep, never to awaken.   Just like the original poster I had tried to make my printer available to another machine on my network, I used CUPS.

I followed Gowater suggestion of renaming the cups directory and uninstalling then re-installing and my printer now works.  Now I am going to edit the cupsd.conf by hand to see if I can make it available.

Apologies for ressurecting such an old thread, but it was very relevant to me and might be to others, thanks for not closing the post :)

That is if I can figure out how to get my other computer to see this linux box :p

---

### Post by mitticus on 2006-02-17
How did you configure CUPS? Mine keeps asking for a password.

(and please dont ask me if I turned my printer on and off :))

---

### Post by Gowator on 2006-02-19
[QUOTE=axe]Can I just say, I don't know whether you people are still around that posted on this post, thank you!

This was exactly my problem, and only happened to me in the last two days, my printer was perfect, then it would keep going to sleep, never to awaken.   Just like the original poster I had tried to make my printer available to another machine on my network, I used CUPS.

I followed Gowater suggestion of renaming the cups directory and uninstalling then re-installing and my printer now works.  Now I am going to edit the cupsd.conf by hand to see if I can make it available.

Apologies for ressurecting such an old thread, but it was very relevant to me and might be to others, thanks for not closing the post :)

That is if I can figure out how to get my other computer to see this linux box :p[/QUOTE]


Axe .. if you enable local browsing (you need to do this editing the cupsd.conf file by hand or you will enbd up back where you were) (hint you can copy the whole directory of /etc/cupsd when its working and then copy it back if you break it again :D)
1. Enable browsing ...
```

root@ubuntu64:/etc/cups # more [B]cupsd-browsing.conf
#[/B]
# Browsing: whether or not to broadcast and/or listen for CUPS printer
# information on the network.  Disabled by default.
#

Browsing On


```

2. in the cupsd.conf (this is huge so I will give instructions)
Open in an editor (kate, gedit etc) 
Find occurences of localhost and/or 127.0.0.1 (this is the IP used for localhost)
Like
```
Listen 127.0.0.1:631
```
and either replace or add ip's or IP ranges like

```
Listen 192.168.1.10:631
```

you can also use
192.168.1.0/255.255.255.0 (with a netmask to do all 192.168.1.x IP adds)

Allow From 127.0.0.1
Allow From 192.168.1.0/255.255.255.0

etc. etc.
then

/etc/init.d/cupsd restart

---

