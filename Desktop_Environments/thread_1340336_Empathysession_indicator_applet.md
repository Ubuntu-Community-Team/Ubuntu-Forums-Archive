---
title: "Empathy/session indicator applet"
date: 2009-11-28
forum: Desktop Environments
---

### Post by cespinal on 2009-11-28
Fellas. im having a little problem with Empathy:

It wont integrate with the session indicator applet. So the horrible green balloon is there, sitting on the notification area, and I would like to have integrated with the session applet, ala jaunty. 

My GF has not had any problems with that..her applet works ok and I can't tell why. 

Any hints??? I read something about switching back to a previous version and deleting the ppa: telepathy... but I have no clue on how to do that.

---

### Post by cespinal on 2009-11-29
bump

---

### Post by kemsiro on 2009-11-29
i got the same problem after i updated empathy !!!
anyone ?

---

### Post by cespinal on 2009-11-29
There have been some bu reports about this. There is some solution having to do with deleting empathy and the ppa:telepathy repository, so you can install an earlier version. 

.....I have no clue on how to proceed in that regard.

---

### Post by Coder543 on 2009-11-29
I too made the mistake of upgrading my telepathy/empathy...

Here's what I did.

Remove all empathy packages. (empathy* and libempathy*)

this will also remove indicator-session and indicator-applet-session

Now, i cleaned my deb cache

Then I installed empathy and the indicator stuff

Then I told indicator-messages to reinstall

Then I killed gnome-panel (you can just log out/in or reboot)

And the applet worked happily ever after (so far)

---

### Post by cespinal on 2009-11-30
Thaks for the reply!

I followed your steps and unluckily, the ugly green orb is still there... maybe I'm missing something. Would you please confirm me how to clean the deb cache?

---

### Post by kemsiro on 2009-11-30
@Coder543: thanks man, i got it fixed.

---

### Post by cespinal on 2009-11-30
hey kesmiroooo!!!!! 

Would you pease tell me what you did? specialy the cleaning the cache thing... I thining I did something wrong

---

### Post by kemsiro on 2009-11-30
@cespinal:
what i did is just following his guide
- uninstall the package using synaptic
- remove the cache -- i used ubuntu tweak to do so
- reinstall the package
- pkill gnome-panel

that's it.

---

### Post by cespinal on 2009-11-30
Nothing.... tried it 3 times in a row... even changing the steps 

Any other way to do this??? :( 

I think I keep downloading the lates verion of empathy... If that is what causes the problem..

---

### Post by kemsiro on 2009-11-30
oh and be sure to remove the empathy unstable repo in the sources.lst

---

### Post by cespinal on 2009-11-30
how to do that :(?

I mean... I dont see any "telepathy" or "empathy" repo listed there...

---

### Post by kemsiro on 2009-11-30
did u use any app like ubuntu tweak to add the unstable empathy repo?

---

### Post by cespinal on 2009-11-30
nopes... I use ubuntu tweak, but I did not use it to install the unstable empathy repo...As a matter or fact, I have been trying to downgrade empathy using synaptic. 

However, I did use ubuntu tweak to erase the cache as you suggested. 

Thanks for taking your time to help me sort this out BTW :)

---

### Post by kemsiro on 2009-11-30
that's weird
i thought your case was same as mine ( i updated empathy to a unstable version using tweak)

if so, check in the preferences -> notifications of empathy and make sure "user message indicator" is checked

---

### Post by cespinal on 2009-11-30
well.... THAT MADE IT!! HAHAAAAAAAAAAAAAAAA!!! THANKS!!!!!!!

---

### Post by kemsiro on 2009-11-30
no prob.

---

### Post by madchine on 2010-03-01
This has been a much more recent occurence for me. Some upgrade in January/february introduced this and it's frankly bizarre that Ubuntu hasn't weeded this out seeing as they've started this whole 'me-menu' thing... If you're gonna integrate, do it properly, I say, or don't do it at all :/

Anyway, the proposed solution doesn't do it for me, though followed to the letter - maybe because I'm simply using the official repos and not an experimental one? Any more recent experiences with this?

---

### Post by Coder543 on 2010-03-01
I would check your empathy settings per Kemsiro's recent comment that worked for cespinal... mine's been working fine. (i haven't checked it in about a week or week and a half because i switched over to KDE's netbook variant... and the green icon looks very nice when mixed with KDE's icons. (since there is no indicator-applet in KDE similar to the GNOME one) lol)

And honestly, I think they did a decent job, since this was the first version. I would venture to bet that integration for the next release will be more solid, although I'm currently planning on getting an Apple iPad... so i may not be seeing as much of Ubuntu as I do now. (although I will still think its amazing, and recommend it to friends and family as needed. Plus i should be installing it on some school laptops tomorrow)

I wish you the best of luck with this issue, if there is a step i described in my initial response, you can ask me about it, but that was what worked for me. I'm not sure how to help with any other empathy/indicator applet integration issue. I probably should have written out the terminal commands i used to accomplish those steps, but that was a long time ago and i've since forgotten the *exact* commands that I used.

Ubuntu has served me well, and i'll still be using it on one or two computers, but I really want an iPad... contrary to what most of the internet seems to think, I am pretty sure it will be amazing, and will serve my needs... although I'll have to use one in person before I decide to buy it.

---

