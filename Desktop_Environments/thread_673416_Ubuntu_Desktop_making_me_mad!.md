---
title: "Ubuntu Desktop making me mad!"
date: 2008-01-20
forum: Desktop Environments
---

### Post by TristanS on 2008-01-20
Hi Ubuntu users!

I recently install Ubuntu 7.10 (Gusty) and have to say I was very pleased with it to begin with. However, now.... sadly, its making me mad! Being a windows user before this, I understand how OS's can act a bit dumb, but Ubuntu.... well, is killing me.

To start off, on the day I installed it, I installed all updates, my Nvidia graphics card driver with Envy, a media player (for dvds) and deluge torrent client. Then the few days after that were heaven... until one day, a nvidia logo flash up during boot (just before the login screen) and then my resolution went completely whack, forcing me to reconfigure the x server, which fix it. Now, recently ubuntu seems to enjoy moving all my "Toolbar" icons around, like the sound icon, network, shut down etc, for no apparent reason. Making me spend the time replacing everything in its place, only for it to shuffle everything again 2 days later and so on. WHATS HAPPENING HERE! im going crazy. 

Other things happen to, like window hiding themselves under toolbars, closing randomly, and other stuff.

EDIT: forgot to mention that I have also installed the Compiz-Fusion-Manager and changed some settings, like desktop cube etc... if this has anything to with it?

Please help a newbie. Thankyou.

---

### Post by zipperback on 2008-01-20
> **TristanS said:**
> Hi Ubuntu users!

Hello!


> **TristanS said:**
> 
I recently install Ubuntu 7.10 (Gusty) and have to say I was very pleased with it to begin with. However, now.... sadly, its making me mad! Being a windows user before this, I understand how OS's can act a bit dumb, but Ubuntu.... well, is killing me. 

Linux is NOT Window$. You cannot reasonably expect it to act the same. Not a flame against you, but many people who make the switch to Linux from Window$ have similar complaints about it not being the same as Window$.


> **TristanS said:**
> 
To start off, on the day I installed it, I installed all updates, my Nvidia graphics card driver with Envy, a media player (for dvds) and deluge torrent client. Then the few days after that were heaven... until one day, a nvidia logo flash up during boot (just before the login screen) and then my resolution went completely whack, forcing me to reconfigure the x server, which fix it. Now, recently ubuntu seems to enjoy moving all my "Toolbar" icons around, like the sound icon, network, shut down etc, for no apparent reason. Making me spend the time replacing everything in its place, only for it to shuffle everything again 2 days later and so on. WHATS HAPPENING HERE! im going crazy. 

I had a similar problem with Ubuntu when I had activated my desktop effects in Compiz, it was happening to my top tool bar panel, and interestingly it was happening on the right hand side next to the system clock. It was pretty strange really. And it was happening when I used the ATI proprietary driver. I don't really care about using the desktop affects myself, so it isn't an issue for me.


> **TristanS said:**
> 
Other things happen to, like window hiding themselves under toolbars, closing randomly, and other stuff.

EDIT: forgot to mention that I have also installed the Compiz-Fusion-Manager and changed some settings, like desktop cube etc... if this has anything to with it?



YES. See my information above....

I don't think it's an Ubuntu issue, but rather a Compiz issue.

-zipperback
:popcorn:

---

### Post by eltama on 2008-01-20
If it makes  you feel better (probably not), I have the same problem with the icons in the upper panel.
When using compiz usually (but not always) if I maximize a window it takes just a portion of the screen and I if I move a window using the menu "Move to Another Workspace" that is not in the first workspace to say workspace 3, it will always move it workspace 1. So I just don't use Compiz.

---

### Post by US41 on 2008-01-20
I have noticed the same impacts on my desktop. Icons move around on the right, and the Nvidia logo suddenly started appearing.

Here's when it happens: when something causes your desktop resolution to change periodically, the system draws the desktop smaller and your icons are pushed in to make them visible. Then, when you fix it, they are left behind in their new locations. 

The Gnome desktop manager is not as stable as "that famous operating system shell from Redmond." It doesn't handle resolution changes as easily, and it doesn't recognize hardware for various reasons. 

I've used linux on and off for years, and I've seen this kind of thing many times. I noticed a few days ago a fix was pushed out to change the way the graphical server (X.org) works, and then another patch came out to back it out. The Nvidia boot time graphic appeared around that time.

Also check to see if you are doing anything like trying to watch full screen video... that can cause resolution change and as the resolution snaps back and forth the icons will get pushed around.

I wouldn't blame Compiz. I don't think this has anything to do with it.

---

### Post by TristanS on 2008-01-20
Wow, thanks for the help.

I will disable compiz & desktop effects for a few days, and see if that has anything to do with the problems im facing. If that doesn't do it, ill pay very close attention to when It happens, especially during watching videos full screen (yes i do) and see if thats the problem. Ill report back if I find anything that definitely causes this issue.

> Linux is NOT Window$. You cannot reasonably expect it to act the same. Not a flame against you, but many people who make the switch to Linux from Window$ have similar complaints about it not being the same as Window$.

PS: I wasn't comparing Micro$aft Window$ to Linux, i was just saying that I have had my fair share of Window$ glitches & bugs, and wasn't really expecting Linux to have them... oh well. lol

Anyway.
Peace out & thanks

---

