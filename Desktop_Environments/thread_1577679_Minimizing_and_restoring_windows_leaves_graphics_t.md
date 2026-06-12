---
title: "Minimizing and restoring windows leaves graphics trail on screen"
date: 2010-09-19
forum: Desktop Environments
---

### Post by koma77 on 2010-09-19
Since 10.04 I get a strange graphics bug whenever I minimize or restore a minimized window.

I'm attaching a snapshot of what it looks like.

I'm using gnome, an nVidia card and have desktop effects enabled.

I just want to know if anyone else is having the same problem?

---

### Post by greenstar on 2010-09-20
Try reducing your desktop effects to "Normal" or "None". If your nVidia chipset is onboard graphics, it might be a bit weak for "Full" effects, especially if it uses shared memory and/or you have other graphically demanding effects enabled (like compiz or similar).

---

### Post by dredmond on 2010-09-25
Hi, I get a very similar problem - however it was previously running fine with compiz on extra.

Strangely, it only happens on half the screen!

Any ideas would be much appreciated.

Matt

---

### Post by koma77 on 2010-09-25
For what it's worth, my problem occurs on the whole screen.
But I agree, your problem looks very similar to mine.

What graphics card do you have?

---

### Post by Gonzalo_VC on 2010-09-25
> **koma77 said:**
> ...What graphics card do you have?

I would say it's a graphic card or chipset issue. I have run Ub 10.04 and others in different machines and never had this problem.
By chance you two (dredmond and koma77) have similar gr. cards?
Did the "restricted drivers" utility suggested some download or alternatives? Maybe it's a good idea to try some other option there.

---

### Post by dredmond on 2010-09-26
I agree - but I think it's strange that this is the first time this has happened.

I've got an integrated graphics card of some description on my rebadged twinhead h12y.

This problem is unique to my desktop account, if I sign in as guest then it doesn't happen, is there some way of completely resetting my desktop settings to default? I tried disabling compiz and restarting but the mess is still there.

TIA

Matt

PS nothing in restricted drivers

---

### Post by greenstar on 2010-09-26
> **koma77 said:**
> For what it's worth, my problem occurs on the whole screen.
But I agree, your problem looks very similar to mine.

What graphics card do you have?

Does this happen on all user accounts or just yours? 

If it's just yours, see my reply to dredmond below. 

If it's all user accounts, see if you have the option to use an older video driver from the repo's/Restricted Drivers or maybe try enabling backports to get an older driver. 

I have a laptop that had some problems with the newest nvidia driver in the repos, using an older driver fixed the problems.

> **dredmond said:**
> This problem is unique to my desktop account, if I sign in as guest then it doesn't happen, is there some way of completely resetting my desktop settings to default? I tried disabling compiz and restarting but the mess is still there.

TIA

Matt

PS nothing in restricted drivers

If it's isolated to your user account, you can create a new user account and then copy your stuff to the new account. 

If you like, after you backup your user directory (/home/username), you  can delete the original user account and recreate it easily. I had to do this  to correct an odd, hard to track down issue with my wife's user account  at one point.

After creating the new user account, copy your user directories back one  at a time. By this I mean, don't just copy everything back at once.  You'll want to restore some things but not others. 

Example: copy your Mozilla Firefox profile folder that's in  ~/.mozilla/firefox/ (Hitting Ctrl-H will display hidden folders in  Nautilus). The profile folder will have a random name - mine, for  example, is yfggw1ks.default. Yours will be different but equally  random. This copies over your firefox settings, history, bookmarks,  extensions, passwords, etc.

Then copy your Mozilla Thunderbird directory if you use Thunderbird  (you'll want the whole directory, not just the profile folder) by  copying ~/.thunderbird 

And so forth for any other user directories that you want to keep. Others that come to mind are:

Filezilla at ~/.filezilla
Evolution at ~/.evolution

When I do a fresh install, I just back up the entire user directory for  each user and restore in this way which allows me to be up-and-running  as quickly as possible with my settings and data intact.

---

### Post by Superdarion on 2011-02-28
I have the same problem as you do. Minimizing leaves a trail of the window and when I restore, sometimes only 3/4 of the window shows up.

If I move a window around the area, everything goes back to normal. Sometimes just clicking there works too.

I'm in a Dell xps16 laptop with an Ati hd 5730, I believe, so it shouldn't have anything to do with nVidia. Also, I haven't moved the drivers since I installed lucid and this problem only started recently. I assume it happened after a small upgrade to some library, but I don't know for sure.

I don't know what the problem is, but disabling the window animations from compiz fixed it completely. All other effects seem to work properly, only the animations (for minimizing and restoring) cause the issue.

---

### Post by koma77 on 2011-02-28
Good to hear that I'm not alone.

Currently I'm just living with the (rather ugly) graphics trails bug.
It's interesting to see that it is not driver related.

I wonder what it could be... I mean, it's related to compiz (or whatever it is called), it's driver independent and it only happens to very few people.

Tricky!

I want to use the desktop animations, so switching them off is not the solution for me.

---

### Post by koma77 on 2011-04-03
I think I finally managed to find out what this problem comes from.

It is a specific Compiz plugin that caused this for me.

It is the "minimize effect" under the "effects" category in the CompizConfig manager.

Disabling that effect made the problem go away!

:)

---

### Post by Copper Bezel on 2011-04-03
I've had this problem, too, when I was using a specific animation (Glide 1 with rotation settings) for close and minimize. It only happened if the window was maximized or resized above a certain size, and changing the animation step slightly improved it. Try just using a different animation for the Minimize effect in Animations. A more complex animation is more likely to lag and stutter and thus more likely to leave artifacts.

---

