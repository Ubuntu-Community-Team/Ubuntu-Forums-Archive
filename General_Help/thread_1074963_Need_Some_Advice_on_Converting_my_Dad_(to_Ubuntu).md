---
title: "Need Some Advice on Converting my Dad (to Ubuntu)"
date: 2009-02-19
forum: General Help
---

### Post by _graphite_ on 2009-02-19
Ok, lately my father's been complaining alot about how slow his 4-year old Windows XP machine is, and I just had the idea to swap in Linux. But I have a couple of questions first.

[LIST]
[*]Will using Ubuntu make it faster than XP? (this will be the main argument in my favor)
[*]His main use for his computer, now, is to check his work email and browse the internet, but he has a page and a half in his IE favorites bar. Whats the easiest way to transfer these over?
[*]He doesn't play any games, really, except for a couple (A hoyle bridge game from 2001-ish, and a Texas Hold'Em game from 2005). Will I be able to run these easily using wine?
[*]Other than speed, what other arguments can i use in the inevitable case he will try to resist?
[*]Finally, should I keep XP on there,  or get it off? (The only scenario I see him needing XP, is for the yearly tax thing, or for a work document that he has to edit that he wouldn't be able to on linux for whatever reason.
[/LIST]

Thanks, to anybody who could help.

---

### Post by spiderbatdad on 2009-02-19
Keep in mind in order to have the best experience with Ubuntu the machine should have at least 512 RAM. For emails, internet browsing, and most apps commonly used on the pc, I think the best argument is not having to be dependent on paid subscrition services that constantly expire...everything from anti-virus to image viewing software is always expiring. Not to mention waiting 5 minutes for windows to finish all its startup serivces and notifications, I find when I turn my parents' computer on.

For things like the hold'em game, it depends. Some of those games are played online in java applet windows. This is no problem provided ubuntu-restricted-extras are installed. I personally don't use wine. I find alternative programs and/or games.

My folks both have Ubuntu on their computers, but to be honest, I don't think they ever boot into. They use windows because it is what they are used to. Whenever they have problems and complain about they way their computers are behaving, I say, That's why I use Ubuntu.

---

### Post by mb_webguy on 2009-02-19
1) If you go with Xubuntu, almost certainly.  Ubuntu or Kubuntu... maybe.

2) You can [export his bookmarks]("http://support.microsoft.com/kb/211089") to an html file, then import them to Firefox in Ubuntu.

3) Probably.  Check out the [Wine AppDB]("http://appdb.winehq.org/") to make sure.

4) He wouldn't have to worry about viruses, spyware, or other malware.  Ubuntu is free.  XP is an outdated OS and no longer really supported by Microsoft, while Ubuntu is in continuous development.  It's highly customizable.  It has a knowledgeable and helpful user community for help and support.  

5) XP needs about 15GB of space for the OS and room for some software.  Ubuntu needs 8 to 10GB for the OS plus software.  And you'll need some more for data.  So if you have at least 30 or 40GB on the computer, then go ahead and keep XP just in case.

A final note:  don't try to "convert" your dad.  Linux is quite capable of selling itself.  And when you push, people tend to push back.  Tying to "convert" someone will generally only make them more resistant to change.  Instead, simply lay out the advantages *and disadvantages* (e.g. that Ubuntu isn't Windows, so there will be some adjustment, and that he won't necessarily be able to use the exact programs he's used to for a given task, etc.), and let him decide for himself.  Most definitely don't go messing with his computer until he's decided that it's what he wants to do.  

Boot up the LiveCD and let him play around with it a bit, with you nearby to answer questions.  That's the best way, IMO, to "convert" him.

---

### Post by bumanie on 2009-02-19
1) Ubuntu should be faster than xp, but the speed difference won't be as noticeable as it would be if your father was using vista
2) Don't use IE, so don't know - but [this]("http://www.askageek.com/2007/04/10/copy-my-favorites-in-ie-to-a-new-computer/") should help, but if you dual boot things like that should be able to to transferred from xp during installation of ubuntu
3) Have no idea about the games - [go here]("http://appdb.winehq.org/") to find out
4) Another argument you could use is that linux doesn't need anti-virus programs etc. Also tell your dad that it is free, so it doesn't hurt trying it.
5) You could dual boot the machine or run xp in a virtual machine such as virtualbox, for the odd times xp is needed, say for tax returns etc. There should be no issue with word documents as open office saves and reads .doc format.

---

### Post by _graphite_ on 2009-02-19
> **spiderbatdad said:**
> 
For things like the hold'em game, it depends. Some of those games are played online in java applet windows. This is no problem provided ubuntu-restricted-extras are installed. I personally don't use wine. I find alternative programs and/or games.


My dad uses an actual hold'em game, probably for directx,  thats offline only. I'll check if its in the wine db, but if not, could it still work in a vm?

---

### Post by mb_webguy on 2009-02-19
> **_graphite_ said:**
> My dad uses an actual hold'em game, probably for directx,  thats offline only. I'll check if its in the wine db, but if not, could it still work in a vm?

Running Windows in a VM is not really any different (in terms of running applications) than actually running Windows, with the exception of a few issues of hardware access.  Wine is a compatibility layer, which basically means that it disguises Linux as Windows -- but the disguise isn't perfect, and some applications may see through it.  But a VM runs the real OS, just on a pretend computer.

Running Windows in a VM allows you to run applications that Wine can't, but it does use considerably more system resources.

---

