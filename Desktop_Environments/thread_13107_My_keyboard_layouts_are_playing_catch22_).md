---
title: "My keyboard layouts are playing catch22 :)"
date: 2005-01-28
forum: Desktop Environments
---

### Post by kiddo on 2005-01-28
Hi there,
 
 I've been using Warty fully for a week now, and I'm happy to say, after my ~15th linux install (counting failures and my web server), that I'm ready to stay here as a desktop station. Great. I registered today only to post something I could not solve (I've spent the last 7 days getting rid of every "bug" that crossed my path :) - the forums were of a great help)
 
 I'm French Canadian, and I use the "canadian french (legacy)" keyboard... normally. That's how it's called in the windows world too anyways. Great. So, to get to the point, I'd normally just need to ...well use it, eh? Doesn't seem so.
 
 I think that happened earlier in gnome (meaning, not only with ubuntu): using "canadian french" or "canadian french (legacy)" alone do NOT give me the proper layout.
 
 However, using a combination of
 - canadian french
 - canadian french (legacy)
 - US english
 
 ...allows gnome to give me the proper layout (shift-3 to make a /, alt-gr-2 to make a @, etc)
 
 Now, if it would only have been that bit of tweaking, no problem. However, the keyboard layouts just go crazy for no apparent reason. They change without notice (for example, I open another gaim window to write something, and then I  start swearing because all my accents are messed up :))
 
 Ever heard of something like this before? Have I missed something?
 I think I'll definitely write down a "paper log" of the keyboard changes, the initial boot state, etc... this is getting confusing.
 
 And.. with this first thread, I also wanted, if they're reading this, to thank deeply the ubuntu team. This is wonderful, and I'll be dist-upgrading to hoary as soon as it comes out :)

---

### Post by kiddo on 2005-01-30
Shameless bump.

---

### Post by fng on 2005-01-30
Maybe make your own custom keyboard layout for gnome.

I didnt make 1 myself, but maybe this can help you : [http://docs.linux.com/article.pl?sid=04/06/03/1558258&tid=26&tid=14&tid=22](http://docs.linux.com/article.pl?sid=04/06/03/1558258&tid=26&tid=14&tid=22)

---

### Post by kiddo on 2005-02-15
The problem was solved by manually editing the xfree86-4 thingy conf, and putting "ca_enhanced" as a keyboard layout. On reboot, gnome asked if I wanted to use xfree's keyboard layout. Said yes, then everything went fine.

---

### Post by TheSavage on 2005-05-29
[QUOTE=kiddo]Hi there,
 
 I've been using Warty fully for a week now, and I'm happy to say, after my ~15th linux install (counting failures and my web server), that I'm ready to stay here as a desktop station. Great. I registered today only to post something I could not solve (I've spent the last 7 days getting rid of every "bug" that crossed my path :) - the forums were of a great help)
 
 I'm French Canadian, and I use the "canadian french (legacy)" keyboard... normally. That's how it's called in the windows world too anyways. Great. So, to get to the point, I'd normally just need to ...well use it, eh? Doesn't seem so.
 
 I think that happened earlier in gnome (meaning, not only with ubuntu): using "canadian french" or "canadian french (legacy)" alone do NOT give me the proper layout.
 
 However, using a combination of
 - canadian french
 - canadian french (legacy)
 - US english
 
 ...allows gnome to give me the proper layout (shift-3 to make a /, alt-gr-2 to make a @, etc)
 
 Now, if it would only have been that bit of tweaking, no problem. However, the keyboard layouts just go crazy for no apparent reason. They change without notice (for example, I open another gaim window to write something, and then I  start swearing because all my accents are messed up :))
 
 Ever heard of something like this before? Have I missed something?
 I think I'll definitely write down a "paper log" of the keyboard changes, the initial boot state, etc... this is getting confusing.
 
 And.. with this first thread, I also wanted, if they're reading this, to thank deeply the ubuntu team. This is wonderful, and I'll be dist-upgrading to hoary as soon as it comes out :)[/QUOTE]
 Thanks a lots man, I was looking for a answer to that problem.

---

