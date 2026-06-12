---
title: "Cut and paste gone?"
date: 2005-11-14
forum: Forum Feedback &amp; Help
---

### Post by earobinson on 2005-11-14
My cut and paste seem to be gone from the message box's (the box you will use to reply to this and tell me that im stupid and it is just because im on a windows computer right now (not by choice) and that computer must have a virus)

Anyone else have this problem?

Thanks

EDIT: cut and paste seems to be back now :)

---

### Post by ubuntu-geek on 2005-11-14
scratches head.. :)

---

### Post by TravisNewman on 2005-11-14
i've always been able to ctrl+c,x,v but I've never had the ability to right click to copy/cut/paste in the post box. Not sure if that's what you're talking about or not.

It only works for me in Internet Explorer.

---

### Post by poptones on 2005-11-14
It's a defect in the javascript. If you use the "quick reply" then after submission of the page you no longer can cut and paste from the mouse. If you reload the page or go to another page it works again.

---

### Post by earobinson on 2005-11-14
well as my edit said it started working again fast, i thought i tryed reloading the page but who knows. I was using firefox on windows xp at work btw.

---

### Post by Dr. Nick on 2005-11-14
I just expeirenced it to with ff in ubuntu. It came back though once i got to another page so it must be a quick reply bug as I had just replied. Just never noticed it before I guess.

EDIT It seems to work fine now even after using quick reply :) Who Knows

---

### Post by earobinson on 2005-11-15
weird, is there anything I can do when this happens to find out if its a firefox, or the forums fault that is causing this error, and help to fix it?

---

### Post by ubuntu-geek on 2005-11-15
Ok so to confirm is this FF in windows or the one with Ubuntu? Also what versions?

this is an edit

---

### Post by earobinson on 2005-11-15
Mine was on windows xp SP2 FF version 1.07 At work

Fake Edit 1 to try and make the bug come back

---

### Post by Dr. Nick on 2005-11-15
Happens to me on quick reply or after editing with FF 1.0.7 on Ubuntu
Ill edit this post from epiphany and see what it does

EDIT

Epiphany seems to work fine. FF will copy paste after using quick rply most of the time, but wont after an edit. Hitting refrsh on the page fixes it and allow copy/paste again. This would lead me to believe its FF not the forums

---

### Post by earobinson on 2005-11-15
I am unable to reproduce the error. This is what I did.
1. Loaded the page in firefox.
2. eddited the above page and added the fake edit line.
3. opened up this quick reply and typed this out then cut and past it.

Dr. Nick is this what you do to make the error happen? If not yould you post the steps to reproduce the error so I can bugzilla it.

Thanks

---

### Post by Dr. Nick on 2005-11-15
I hit quick reply and typed this - **after posting that I can copy and paste** The bold is my 1st edit.

After saving that edit I cant copy and paste until i hit refresh

So the quick reply diesnt mess up copy and paste, it seem that it is the edit that is the problem, but only a problem in FF not epiphany

---

### Post by poptones on 2005-11-15
Good work! I guess it's because I use "edit" so much I didn't notice the diff...

I know it has the problem with ootb ubuntu, cuz that's all I use. I'm using the latest ff in the hoary repository.

**Edit**... and after, cut and paste is grey.

---

### Post by earobinson on 2005-11-15
ok now I guess Ill go test it on some other forums to see if it really is a ff problem

---

### Post by TravisNewman on 2005-11-15
[QUOTE=ubuntu-geek]Ok so to confirm is this FF in windows or the one with Ubuntu? Also what versions?[/QUOTE]
either version, either os. I get the bug on regular Mozilla as well, so it seems to be a gecko thing.,

---

### Post by ubuntu-geek on 2005-11-15
Running Firefox 1.5rc2 on Mac no issues.. Has anyone tested with Firefox 1.5 on Linux/windows? I am not at home atm or I would..

---

### Post by TravisNewman on 2005-11-15
ok yeah it appears 1.5 works in Windows

---

### Post by Dr. Nick on 2005-11-15
1.5 works? I cant try that as I cant get it to run on 64bit :( No big deal Since when its final it will be compiled for 64 aswell. Since it works in epiphany and apparently the new ff 1.5 I guess its just a bug that has been fixed in firefox, thats good to know

---

### Post by ubuntu-geek on 2005-11-16
[QUOTE=panickedthumb]ok yeah it appears 1.5 works in Windows[/QUOTE]
has anyone tested 1.5 in Linux yet?

---

### Post by Dr. Nick on 2005-11-16
Quick Reply: Currently Trying 1.5 in linux on my 32bit computer

EDIT:
After the edit copy/paste no longer works on ff1.5 in linux.
I still have 1.0.7 installed so I am not sure if their is perhaps a config file somewhere from 1.0.7 that 1.5 is using. All of my settings are the same so I know 1.5 is using my 1.0.7 stuff.

Anyone have 1.5 only and not the 1.0.7?

2nd edit.

Hmm this is a bit odd, when I hit edit in FF 1.5 now I get a different dialog, Like the advanced edit and not the quick edit. Epiphany still gives me the quick edit.

I would like someone else to try it as I am starting to think that my FF may be goofed since I have 2 versions installed

---

### Post by ubuntu-geek on 2005-11-16
Lets try this.. In your User CP options choose the style Ubuntu_Brown_v3.5.1 and see if the update fixes the issue.

NOTE: the v3.5.1 style is missing some functions in the customization area so I would consider this beta right now..

---

### Post by Dr. Nick on 2005-11-16
nope, even with the new 3.5.1 FireFox 1.0.7 still behaves as before, unfortunately cant test on 1.5 now

---

