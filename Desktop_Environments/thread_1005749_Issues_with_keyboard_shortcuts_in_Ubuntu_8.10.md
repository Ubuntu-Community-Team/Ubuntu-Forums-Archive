---
title: "Issues with keyboard shortcuts in Ubuntu 8.10"
date: 2008-12-08
forum: Desktop Environments
---

### Post by Montblanc_Kupo on 2008-12-08
Fairly new fulltime linux user, but learning fast. :)

I hope this is the right section, I'm not entirely sure where the problem is so I wasn't entirely sure where to post the question.

I have two user accounts installed on My ubuntu 8.10 (2.6.27-10-generic, GNOME 2.24.1)

I have been using ctrl-alt-del to log out and ctrl-alt-L to lock the screen since install... recently those stopped doing...  well.. anything.

I have created 3 custom keyboard shortcuts bound to commands (2 apps, and one command)... but I double checked and none of those shortcuts are showing that they are the same as the two defaults (I wouldn't have intentionally set them to be the same... but who knows what can happen in the dark underbelly of the OS...heh). I checked in ccsm and gconf just to make sure... and they both read the same (same setting I believe).

So... I'm assuming that there is a keyboard shortcut that is conflicting... but I manually checked **every** setting in compiz for conflict, and in System > Preferences > Keyboard Shortcuts they are still listed correctly.

The other snafu is that I created a second user account a while ago to use for gaming (no tweaks, no compiz, etc... kept it lean to reduce memory and cpu usage for 3D games)... the keyboard shortcuts still work as expected in that account.

So... it's definitely making me think that it's some setting I have changed in my main account and not like... a hardware conflict or something... but I'm not sure where to check.

Any advice on resolving the conflict or tracking down the issues would be appreciated. If additional information is needed... let me know what to provide since I didn't know what else to list.

Thanks in advance.

---

### Post by Montblanc_Kupo on 2008-12-09
Wow... 32 views and not even a "geez noob... push the magic button" lol. Did I stump the linux community with My first question?

I swear, I have been searching the forum and on google already and haven't found anything.

Ctrl+shift+esc is supposed to force kill windows isn't it? That key combination doesn't seem to do anything either.

Anyone? Anywhere? Any clue? heh

oh... and *bump*. lol

---

### Post by Montblanc_Kupo on 2008-12-13
Wow...

---

### Post by treepolitik on 2008-12-21
> **Montblanc_Kupo said:**
> Fairly new fulltime linux user, but learning fast. :)

I hope this is the right section, I'm not entirely sure where the problem is so I wasn't entirely sure where to post the question.


I would also describe myself as a "fairly new full-time Linux user."  When in doubt and particularly when it's not challenging code/vocabulary, I would post this sort of thing in the Beginner Forum.  It's always a good idea to take some "general education," too, so to speak.

> **Montblanc_Kupo said:**
> 
I have been using ctrl-alt-del to log out and ctrl-alt-L to lock the screen since install... recently those stopped doing...  well.. anything.

I have created 3 custom keyboard shortcuts bound to commands (2 apps, and one command)... but I double checked and none of those shortcuts are showing that they are the same as the two defaults (I wouldn't have intentionally set them to be the same... but who knows what can happen in the dark underbelly of the OS...heh). I checked in ccsm and gconf just to make sure... and they both read the same (same setting I believe).

So... I'm assuming that there is a keyboard shortcut that is conflicting... but I manually checked **every** setting in compiz for conflict, and in System > Preferences > Keyboard Shortcuts they are still listed correctly.


So, let me get this straight.  You made 3 custom shortcuts.  You found that they didn't match with the system defaults, of which there are 2.  With all due respect, I'm not sure what you mean: How can 2 default shortcuts correspond to 3 custom shortcuts?  

I read it again and saw that you were talking about 2 applications.  So "two applications and one command."  If I am reading correctly, you assigned 3 custom shortcuts to each of the 2 programs.  Then you created a command that works in both programs and allows you to use the 3 custom shortcuts in both of those programs.

Going back to what you said before, when you said "none of the shortcuts are showing that they are the same" as their corresponding commands in the two defaults, you were saying that you thought everything was ok.  

Then you checked in ccsm and gconf, and found out that it was not ok, because your shortcuts did appear to read the same as the defaults.  

But then with the menu, it said that everything was ok, and that your shortcuts work, despite that they actually *don't* work.
 
> **Montblanc_Kupo said:**
> 
The other snafu is that I created a second user account a while ago to use for gaming (no tweaks, no compiz, etc... kept it lean to reduce memory and cpu usage for 3D games)... the keyboard shortcuts still work as expected in that account.

So... it's definitely making me think that it's some setting I have changed in my main account and not like... a hardware conflict or something... but I'm not sure where to check.

Any advice on resolving the conflict or tracking down the issues would be appreciated. If additional information is needed... let me know what to provide since I didn't know what else to list.

Thanks in advance.

By any chance did you install programs that each have their own rules for regular keyboard shortcuts?  That's all I can think of for now.  Sorry I couldn't be of more help.

---

### Post by Montblanc_Kupo on 2008-12-27
> I would also describe myself as a "fairly new full-time Linux user." When in doubt and particularly when it's not challenging code/vocabulary, I would post this sort of thing in the Beginner Forum.

Yeah, I wasn't entirely sure where this fit because I'm not exactly sure what the cause is... 

> It's always a good idea to take some "general education," too, so to speak.

Not sure what you're getting at, but I've been testing, reading, trying, poking, playing, opening, closing, and operating. It's becoming like a Daft Punk song. I have tried researching and reading a bunch... but that's what forums are for are they not... information exchange and learning?

> So, let me get this straight. ...

Yeah, I could have worded that better. What I was saying was this. I created 3 custom keyboard shortcuts. super+N to open a new nautilus window. super+F to open a new firefox window. ctrl+shift+del to empty the current user account's trash. I was trying to say that I had made 3 shortcuts, but that I intentionally made sure that they didn't correspond to any system defaults before I assigned the keys for them. Hopefully that is more clear about what I meant heh. I did manually go through all the assigned keyboard shortcuts in compiz and checked the command keybindings in compiz (and gconf just to double check) to make sure nothing was conflicting and found no conflicts.

> By any chance did you install programs that each have their own rules for regular keyboard shortcuts? That's all I can think of for now.

I suppose it's possible... but the only things that I have running at startup that isn't default from install are compiz, emerald theme manager, and firestarter firewall. I tried turning these off and it didn't seem to make a difference.

> Sorry I couldn't be of more help.

I appreciate the effort... I know it's a squirrely problem since it could be so many different things.

---

