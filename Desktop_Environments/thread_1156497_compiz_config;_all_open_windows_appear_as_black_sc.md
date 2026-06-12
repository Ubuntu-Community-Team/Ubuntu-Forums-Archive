---
title: "compiz config; all open windows appear as black screen"
date: 2009-05-11
forum: Desktop Environments
---

### Post by Byrdmk on 2009-05-11
I am pretty new to Ubuntu but have really enjoyed this new version.  I installed compiz config and was playing around with some of the "effects."  There is one effect that I believe is called Blur Windows (or something to that effect, and the icon next to it I think was some form of red circle). 

When I checked the box next to it, problems started.  Any open window appears as black screen.  The screen becomes black bit by bit, until totally black.  

Is there any way I can restore compiz config to its default settings so I can see my desktop again?  Some way I can do this via command line, because I cannot see the desktop.  Sorry if I'm unclear, I am desperate for some help.  Speak slow, as I am relatively dumb when it comes to this. 

Thanks, anyone...

---

### Post by Byrdmk on 2009-05-12
bump im begging

---

### Post by darth_borehd on 2009-05-13
I have the EXACT same problem.  I'm still trying to fix it myself.

---

### Post by darth_borehd on 2009-05-15
I think I found the answer!  This worked for me:

> 
$ gconftool-2 --recursive-unset /apps/compiz
$ gconftool-2 --recursive-unset /schemas/apps/compiz
$ gconftool-2 --unset /apps/gnome-compiz-preferences

---

### Post by Viruk on 2009-05-22
Thanks very much darth_borehd. I had exactly the same problem when I set blur windows and this got my desktop back. 

Does anyone know if there is a way to unset a particular option so that if a problem like this occurs again I don't have to go back to square one with the setup of compiz?

---

### Post by Grey Melon on 2009-06-07
darth_borehd,

I also had this exact issue arise and your solution worked for me as well. Thank you very much.

---

### Post by krazyd on 2009-06-07
What graphics card / driver are you guys using?

---

### Post by jubxie on 2009-06-16
Intel 3100 here. Same issue w/ the blur setting. Thanks for fix.

---

### Post by dj_bridges on 2009-07-07
Thanks for the tips - sorted out the issue perfectly!

Anyone know if a bug has been filed for Blur Windows???

---

### Post by kevmackim on 2009-07-13
darn! and i just reinstalled coz of this problem.thanks anyway

---

### Post by lagamemnon on 2009-08-25
I had this problem and found the answer in another post here that I can't find now, but to fix it, when you're in gnome and all logged in and all the windows are black:

1. Hit control-alt-f2
2. enter in:
metacity --replace --display :0 &

3. hit control-alt-f7

this turns of compiz and uses metacity. Go back into your compiz manager and turn off the bad effects.

This is a really annoying problem if this happens to you, they should really have a timer thing to make sure the effect works or it reverts.

---

### Post by fidel.cashflow on 2009-10-19
I'm also having the same problem with blur windows and I've tried entering the following

gconftool-2 --recursive-unset /apps/compiz
gconftool-2 --recursive-unset /schemas/apps/compiz
gconftool-2 --unset /apps/gnome-compiz-preferences

----------------------------------------------------------------

I enter the above commands after booting into ubuntu 9.04 in recovery mode. I enter them into the root shell prompt. However, when I boot into the GUI everything seems okay until I open a window; the screen fills a black rectangle wherever the OS tries to paint. Can somebody please help me I need to use ubuntu!! btw I'm an ubuntu noob please help I want to learn more so I can contribute to the open source communityyyyyyyyyyy

---

### Post by fidel.cashflow on 2009-10-19
Nevermind! I just saw page 2 and I tried lagamemnon's solution and it worked. Thanks man

---

