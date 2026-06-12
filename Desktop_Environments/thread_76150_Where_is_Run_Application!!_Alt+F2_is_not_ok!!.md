---
title: "Where is Run Application!?! Alt+F2 is not ok!!"
date: 2005-10-14
forum: Desktop Environments
---

### Post by qewl on 2005-10-14
Wow Breezy is really starting to make me want to pull out hair (like warty did!)

I don't understantd why Run Application is now gone from the menu, as most new apps don't have menu icon. Having to use the keyboard is a pain and just another key combination new users will have to memorize. Simplifying the desktop does not mean getting rid of stuff! Especially things many of us use everyday..  >:0

I've never before had to use Alt+F2 - does anyone know what the command is for a terminal to add Run Application back to the menu. ? :(

---

### Post by Wolki on 2005-10-14
[QUOTE=qewl]I don't understantd why Run Application is now gone from the menu, as most new apps don't have menu icon. Having to use the keyboard is a pain and just another key combination new users will have to memorize. Simplifying the desktop does not mean getting rid of stuff! Especially things many of us use everyday..  >:0[/quote]

First, most applications do add a menu entry nowadays, if one doesn't (and it is a graphical app) please file a bug.

Now, I don't see why having to use a keyboard is a problem in this case, since you will have to type into the run dialog anyways. Removing the mouse option will actually make you faster (once you've unlearned the old behavior), since you don't have to shift your hand from your keyboard and back.

> I've never before had to use Alt+F2 - does anyone know what the command is for a terminal to add Run Application back to the menu. ? :(

I'm not sure there is a way, but you can add a panel starter for it from the "Add to Panel" dialog.

---

### Post by SqdnGuns on 2005-10-14
Chill out FFS...........why not "add to panel" the "run application"?

---

### Post by Dr. Nick on 2005-10-14
EDIT
Dang you 2 how do you type so fast. we all posted at about the same time with the same thought on a solution lol
_______________________________________________________________________________________

I know this doesnt answer your question specifically but it may help for the time being. If you are using gnome (I assume so) find a empty spot on the panel , right click and hit add to panel, scrool to utilities at the bottom and add "command line". That may help better than the "run application" why it is gone I dont know, maybe someone else will

---

### Post by liquidtenmillion on 2005-10-14
I agree, there is no reason at all for it to be in the menu.  This is not an Ubuntu Breezy change, it is a Gnome 2.12 thing.  I'd say 95% of the people use alt+f2 anyway.

I don't see how the keyboard is unacceptable, since you would have to use the keyboard anyway to type the command in.

---

### Post by Stormy Eyes on 2005-10-14
Run Application was removed from GNOME by the GNOME developers, and I've heard the decision to do so described as removing "a relic of a bad menu system". If you want, you can open a terminal and do **sudo apt-get install gmrun**. Once gmrun has been installed, you can create a desktop icon (or a panel button) to launch gmrun.

---

### Post by dannotdan on 2005-10-14
Thank you Stormy Eyes, that sounds like the most elegant solution.

I agree with Wolki that Alt-F2 isn't that difficult when you are already planning to type your program name, but that key combination isn't exactly common knowledge among the newbies. I've been using Linux for maybe 2 years now, and I always used the menu "Run App" selection. I didn't learn about Alt-F2 until my menu option disappeared in Gnome 2.12 and I had to scramble for like half an hour before I found it.

---

### Post by qewl on 2005-10-14
[QUOTE=Wolki]First, most applications do add a menu entry nowadays, if one doesn't (and it is a graphical app) please file a bug.

Now, I don't see why having to use a keyboard is a problem in this case, since you will have to type into the run dialog anyways. Removing the mouse option will actually make you faster (once you've unlearned the old behavior), since you don't have to shift your hand from your keyboard and back.



I'm not sure there is a way, but you can add a panel starter for it from the "Add to Panel" dialog.[/QUOTE]

 Thanks guys. I'm sorry I didn't mean to be mad- I had just spent 45 min trying to get a hdd to mount (finally by sudo creating a directory in media and doing it from there)
I added a run icon to my panel and am happy again!- i like the run box cuz I can just click from previous choices instead of having to type. Didn't know it was there, but was afraid to look as my screen keeps blanking out on me:

[www.humans.com/whatsgoingon.png](www.humans.com/whatsgoingon.png)

I just installed latest nvidia drivers and it hasn't happened since, but that was still only a few min. ago, so I don't know yet. But if nothing else I can run without having to type..

---

### Post by Stormy Eyes on 2005-10-14
[QUOTE=dannotdan]Thank you Stormy Eyes, that sounds like the most elegant solution.[/QUOTE]

No problem. I use gmrun to provide a "Run Program" prompt in minimal window managers like Blackbox and Openbox.

---

### Post by Dr. Nick on 2005-10-14
[QUOTE=qewl]

[www.humans.com/whatsgoingon.png](www.humans.com/whatsgoingon.png)

I just installed latest nvidia drivers and it hasn't happened since, but that was still only a few min. ago, so I don't know yet. But if nothing else I can run without having to type..[/QUOTE]

Hope it stays correct, Ive never seen that before, If it continues your card may be getting hot? I dont know, looks sort of like artifacting but dont know why it would. Hopefully the nvidia drivers fix it for you as thats just weird

---

