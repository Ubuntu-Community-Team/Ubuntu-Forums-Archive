---
title: "Problems installing CVS Cedega"
date: 2005-04-21
forum: Gaming &amp; Leisure
---

### Post by Sabator on 2005-04-21
A friend of mine told me I could use what appears to be a free version of Cedega to play Windows games, and he gave me this link:

[http://www.linux-gamers.net/modules/wfsection/article.php?articleid=45](http://www.linux-gamers.net/modules/wfsection/article.php?articleid=45)

I performed steps 1 to 3 fine, but I couldn't find the script that it talks about in step 4 anywhere on my computer. Has anyone else done this? If you have, what profile did you use during installation?

---

### Post by nahkapaavali on 2005-04-21
I think it means when you type *cvscedega* it starts a script that creates fake windows folder.

---

### Post by Sabator on 2005-04-21
[QUOTE=nahkapaavali]I think it means when you type *cvscedega* it starts a script that creates fake windows folder.[/QUOTE]
 I tried that, it said cvscedega was an unrecognized command

By the way, what's the difference between this and the version of Cedega that costs money? There must be some problems with it...

---

### Post by nahkapaavali on 2005-04-21
[QUOTE=Sabator]I tried that, it said cvscedega was an unrecognized command[/QUOTE]

Ok. So if i were you i would double check the depencies what it needs and then try again. 

>  By the way, what's the difference between this and the version of Cedega that costs money? There must be some problems with it...

Don´t know exactly but i´ve heard that cvs lacks some copyright code and some dll files. To consumer it appears as non working games :D

---

### Post by Sabator on 2005-04-21
Sorry, I'm still kinda new to Linux. What do you mean by dependencies? And what do you mean by "non-working-games"?

---

### Post by jovian on 2005-04-21
I believe you need to run the script itself thought its not called cvscedega. When I did it the script name was/is WineCVS.sh i ran and followed the diretion on screen and it works fine for me :)
ps cedega was previously called winex which was based from wine
the difference between the free cedega and the non free are that non-free you have voting rights to which games they work on to ensure support and there is a graphical interface and an extra installer program that makes installing a game pretty much insert disk run the program. There may be a couple other things but I don't remember exactly what they are

---

### Post by nahkapaavali on 2005-04-21
[QUOTE=Sabator]Sorry, I'm still kinda new to Linux. What do you mean by dependencies? [/QUOTE] 
I mean programs and libraries which are in step two. 
wget
fontconfig
freetype2
freetype2-devel
etc... 

> And what do you mean by "non-working-games"?
I mean they are not working no matter what. New games usually or really old and unintresting ones.

---

### Post by Sabator on 2005-04-21
*sigh*

I ran WineCVS, and I have all the dependencies. But AFTER WineCVS is finished installing, I don't see a cvscedega script!

argh, it would be so much easier if there was a .deb package of this or something...

EDIT:  I just hunted down a version of regular Cedega off amule. Mission accomplished, good afternoon, good evening and goodnight.

---

### Post by jdodson on 2005-04-21
[QUOTE=Sabator]*sigh*

I ran WineCVS, and I have all the dependencies. But AFTER WineCVS is finished installing, I don't see a cvscedega script!

argh, it would be so much easier if there was a .deb package of this or something...

EDIT:  I just hunted down a version of regular Cedega off amule. Mission accomplished, good afternoon, good evening and goodnight.[/QUOTE]

hey now, the cedega folks frequent this form.  i would not be so quick to admiting piracy.  i "LINKED" to a site that i thought contained a cvs build.  a developer PM'ed a day or two later and said thier layers might be contacting me if i didnt remove the "LINK".  i was a new mod at the time and thought it was a legit cvs build.  they didnt say "hey you know that isnt cvs"  they just threatened legal action. 

dont mess with cedega.

** EDIT ** a follow up.  i was so upset for them calling me a "software pirate" that i PM'ed the developer like 6 times vocing my frustration.  no response.  basically it was a "TAKE IT DOWNE YOZ PIRATE OR ELSE WHEEEL SUUEEEE!!!!!!!!!!!!1111" no response, no follow up, just legal threats.  i do not priate any software!! it is all legit, so when someone calls me one, i take offense at it.

---

### Post by nahkapaavali on 2005-04-21
[QUOTE=jdodson]hey now, the cedega folks frequent this form.  i would not be so quick to admiting piracy.  i "LINKED" to a site that i thought contained a cvs build.  a developer PM'ed a day or two later and said thier layers might be contacting me if i didnt remove the "LINK".  i was a new mod at the time and thought it was a legit cvs build.  they didnt say "hey you know that isnt cvs"  they just threatened legal action. 

dont mess with cedega.[/QUOTE]

Chees. I think that cedega should make a clear point where it differs from cvs so people would know better when they are doing illegalities :)

---

### Post by jdodson on 2005-04-21
[QUOTE=nahkapaavali]Chees. I think that cedega should make a clear point where it differs from cvs so people would know better when they are doing illegalities :)[/QUOTE]

i know you cant copy around the binary of cedega, i thought the site i was linking to provided a cvs binary.  

the difference in cvs VS. the file they sell you is that they include proprietary vendor CD protection code(along with other little bits) therefore the binary they provide is not free, as in cost or freedom.  its all perfectly legal under the LGPL, which is how wine is licensed.

so when you build from cvs, you are getting cedega minus the proprietary bits and cd copy protection code, etc.

---

