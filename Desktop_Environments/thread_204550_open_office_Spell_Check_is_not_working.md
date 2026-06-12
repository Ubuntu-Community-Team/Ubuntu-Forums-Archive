---
title: "open office Spell Check is not working"
date: 2006-06-27
forum: Desktop Environments
---

### Post by majeshps on 2006-06-27
I am facing an issue with openoffice 2 word processor Spell Check .
     The Problem is like this,
                            Spell check option will not work at some time.May be if user is log off
and login again it will start working.I have changed the Language settings to English(USA)
and English(UK).The same issue I am facing at Some time..Seems like a Bug.

---

### Post by TigerWolf on 2006-06-27
Open your document - select all of the text and then Format > Charachter > then select the language of the new dictionary you installed.

---

### Post by majeshps on 2006-06-27
Thanks

---

### Post by gmatt on 2007-05-18
ok so I got the same problem, and I'm googling it (im actually running OO on Mac OS X, but I hate OS X and wanna get Ubuntu but ATI cards suck under linux) and there is all this **** out there about this problem following the first few links all these bs explanations about OO being a complex piece of software and ****, and man this problem was making me pull out my hair cause I dont care how complex something is if it dont work. Anyways, I see the ubuntu forums google link and something inside me tells me this is gonna have the answer. And bam it did it worked. Holy **** you guys are worth gold per every lb of ur body. man I love this forum and I love linux and i love the community. You guys reach out beyond linux ;)

---

### Post by wjp.reg on 2007-07-05
Dito;

D'ya think google came up with a link to the openoffice forum (let alone a solution) ?

NOT!

cudos to the ubuntu community :-)

---

### Post by bsawler on 2007-07-12
To fix the problem, you need to go to** File > Wizards > Install New Dictionaries **

I did this on 2 machines, and it fixed this silly problem.

---

### Post by JacobRogers on 2007-08-17
> **bsawler said:**
> To fix the problem, you need to go to** File > Wizards > Install New Dictionaries **

I did this on 2 machines, and it fixed this silly problem.t ju

That just worked for me, for whatever reason when I installed Ubuntu through Wubi Open Office didn't have the dictionary installed.  And you'd think you could select which dictionary you wanted from the spell checker menu, but when it doesn't have a dictionary you can't access the spell checker menu because it will just say there are no spelling errors and close.

:mad:

---

### Post by mprobertson on 2007-08-19
yeah that last one's a bug. should be fixed.

---

### Post by Hagar Delest on 2007-08-20
For spell checking issues, see here : [[Tutorial] Spell check and Language configuration](http://www.8daysaweek.co.uk/forums/viewtopic.php?t=758).

---

### Post by ireneshusband on 2007-08-21
Every time I do the File > Wizards > Install New Dictionaries thing Openoffice crashes.

---

### Post by Hagar Delest on 2007-08-21
Try to run OOo with sudo just to run the wizard. Or install them manually.

---

### Post by unique_stephen on 2007-09-16
and for me. 
First day using ubuntu - I'm a total n00b. These forums have been fantastic

---

### Post by sfsetse on 2007-09-24
Spell checking for OpenOffice under Ubuntu is enabled by installing the approprate myspell dictionary and restarting OpenOffice. Use either Synaptic or apt-get to install them.

The myspell packages I have installed to enable both English and German spell checking are:
myspell-de-de myspell-en-us

---

### Post by galleonway on 2007-10-31
> **TigerWolf said:**
> Open your document - select all of the text and then Format > Charachter > then select the language of the new dictionary you installed.

I had the same problem in Gutsy. You have to select a language with the "abc" in front of it. Using Tools > Options route doesn't work.

---

### Post by GlennW on 2007-11-05
I'm having the same issue. No spellchecker! When I do click the ABC (not the one with the wavy red line), the spellchecker box opens, with nothing in it, and a little dialogue box overtop saying the spellcheck is complete! I've noticed that in the larger box underneath there is a place at the bottom where you can choose the dictionary language. I can't because as soon as I close the smaller box (spellcheck complete) everything disappears. 

I've gone through many related threads and followed everything but to no avail. The File>Wizard>install new dictionaries doesn't work since when I choose English, some small box pops up where I can't even ready the text and there are no options to increase the box size to continue the wizard. When I close the box, the wizard disappears. So much for that!

Under Tools>Options>Languages, I've got everything set to canadian/canada and enabled where possible.  Under Tools>Options>Writing aids, I've got the canadian dictionary checked as well as everything else appropriate. 

Also, Format>Character>Font, English (Canada) is there.

Why no spellchecker/dictionary?

---

### Post by Hagar Delest on 2007-11-06
Have you read my tuto (previous page of this thread) ?

---

### Post by GlennW on 2007-11-06
> **Hagar de l'Est said:**
> Have you read my tuto (previous page of this thread) ?

Yes, in fact, I've read most every thread regarding the OOo dictionary issue. I've followed your advice not only here in this thread but your input on the OOo threads too. Still, no dictionary. 

My suspicion is that with so many people having similar, if not identical, problems, there must be a bug/flaw somewhere. A big part of the problem for me is that I'm such a noob! If I had some more experience (although I'm rapidly gaining it here) I would be able to better convey my situation to you.

Yet after all of this I'm completely stymied. Any further suggestions Hagar?

---

### Post by qrof on 2008-03-24
> **Hagar de l'Est said:**
> Try to run OOo with sudo just to run the wizard. Or install them manually.

this worked for me... sudo openoffice and ran the wizard.

thanks :)

---

### Post by Crushyerbones on 2008-04-09
> **GlennW said:**
> Yes, in fact, I've read most every thread regarding the OOo dictionary issue. I've followed your advice not only here in this thread but your input on the OOo threads too. Still, no dictionary. 

My suspicion is that with so many people having similar, if not identical, problems, there must be a bug/flaw somewhere. A big part of the problem for me is that I'm such a noob! If I had some more experience (although I'm rapidly gaining it here) I would be able to better convey my situation to you.

Yet after all of this I'm completely stymied. Any further suggestions Hagar?

Same. Infact, myspell won't work at all. (Firefox does though. does it use myspell?)

Also, emesene spellchecker tells me I need gtkspell. :mad:

---

### Post by a94060 on 2008-07-16
> **sfsetse said:**
> Spell checking for OpenOffice under Ubuntu is enabled by installing the approprate myspell dictionary and restarting OpenOffice. Use either Synaptic or apt-get to install them.

The myspell packages I have installed to enable both English and German spell checking are:
myspell-de-de myspell-en-us

thank you my friend for this, now my dictionaries started working. Luckily i looked at the forums within 30 mins of the problem,otherwise i would have started getting mad.:lolflag:

---

### Post by phoenix42 on 2008-07-17
> **sfsetse said:**
> Spell checking for OpenOffice under Ubuntu is enabled by installing the approprate myspell dictionary and restarting OpenOffice. Use either Synaptic or apt-get to install them.

The myspell packages I have installed to enable both English and German spell checking are:
myspell-de-de myspell-en-us

This worked for me, thanks

---

### Post by tyk on 2008-07-21
thanks worked for me too.
tyk.

---

### Post by wormser on 2008-07-22
> **TigerWolf said:**
> Open your document - select all of the text and then Format > Charachter > then select the language of the new dictionary you installed.

This was the final step that worked for me.

I installed with CA instead of US.  To get spell check to work I had to change the system language under System> Administration> Languages.  I then downloaded the dictionary in Open Office under Wizards> Install New Dictionaries.  Then the solution in the quote worked.

What a pain it was.  Hopefully this helps somebody else.


**EDIT:**

I spoke to soon.  The Dictionary Language will not stay.  I can run spell check once and it resets.  Any ideas?

---

### Post by Hagar Delest on 2008-07-23
Yes, modifying the language on the characters is a direct formatting, to be avoided. See here: [[Tutorial] Spell check and Language configuration](http://user.services.openoffice.org/en/forum/viewtopic.php?f=7&t=67).

---

