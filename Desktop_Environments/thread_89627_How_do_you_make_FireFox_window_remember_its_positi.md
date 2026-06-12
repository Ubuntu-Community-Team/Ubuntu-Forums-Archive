---
title: "How do you make FireFox window remember its position"
date: 2005-11-13
forum: Desktop Environments
---

### Post by Canuckelhead on 2005-11-13
With all of my other apps... They will open in the same size and position that they were in when I last closed them.  Firefox seems to be the exception and its driving me nuts.  I am particular about my desktop and would like it to always be in the same place!  Is there anyone out there who knows how to fix this?  I would also like to know if there is a way to have my startup programs open to specific desktops ... for instance I would like to have xmms open on the second desktop after startup rather than on the first...

Thanks in advance for any insight...

---

### Post by heimo on 2005-11-13
Make sure you have write permissions to ~/.mozilla/firefox/*.default/localstore.rdf file. Use chmod u+w [filename] to give yourself write permissions. That's the file where firefox keeps information of its window position.

How to start applications on specific workspace, use devilspie:
[http://ubuntuforums.org/showthread.php?t=75749](http://ubuntuforums.org/showthread.php?t=75749)

---

### Post by Canuckelhead on 2005-11-13
Hey thanks alot hopefully this will help me keep my desktop feng shui...  As I said ... having it random drives me bonkers!

---

### Post by Canuckelhead on 2005-11-13
Still no luck with firefox... it always opens at the same size ... but never in the same position.  It seems to be always open on the left side... Is there anything that it activly avoids covering? icons? desklets ????

---

### Post by SickTwist on 2005-11-13
I think that this feature (or lack thereof) is application dependent, meaning that in order for a program to remember its size and/or position it must be programmed that way. This is not something that is handled directly by the window manager.

---

### Post by keforex on 2007-11-15
You know, this issue of windows not being on the same spot and the same size as the last time I used them is really a BIG annoyance.

Why is this such a big issue to be solved? I've been searching this forum and I can't find a definite solution for this simple but very irritating problem.

In Windows for example, when I put a window at some place on the screen and at the size I want, it will be always there, no matter how many times I boot the system.

People have different needs, and in my case I NEED all windows to remember their size and position. Why there is not such a simple global "check mark" option that says "remember windows sizes and positions" ??

I work with two screens, a 30" and a 19", and having to move all my applications and resize them back to where I want them every single damn time I start Ubuntu is one of the biggest flaws I ever seen.

Any suggestions besides having to install yet another package?

---

### Post by jmap82 on 2008-03-08
Same problem as stated above... less passion.  Has anyone come up with anything yet?

---

### Post by keforex on 2008-03-23
Anybody?.... Please read my post #6 - I now have two 30" monitors at 2560x1600 and the damn windows will not remember their size and place. ANNOYING!!! No wonder Bill Gates is a billionaire.

---

### Post by gaemon on 2008-03-26
I'm afraid this thread is too old, but here it goes.
Searching on bugzilla shows this jolly ol' bug:

[https://bugzilla.mozilla.org/show_bug.cgi?id=209342](https://bugzilla.mozilla.org/show_bug.cgi?id=209342)

it was FIXED & CLOSED on firefox 1.7.5. it seems revived in 2.0.
I dunno if this bug persists in upcoming 3.0...

ps. this is my first post on this forum. sorry for n00b formatting.

---

