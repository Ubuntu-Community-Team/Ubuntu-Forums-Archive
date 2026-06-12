---
title: "Evolution and spam filtering"
date: 2005-04-17
forum: Desktop Environments
---

### Post by bobdave on 2005-04-17
Some time ago, I read that Hoary would include Bogofilter for use with Evolution to filter spam and it appears to be installed by default.

I'm under the impression, though, that it won't currently work with Evolution.  Can anyone clarify this?

---

### Post by André on 2005-04-19
Hi,

i can't clarify this. But i can tell you that i also have the feeling that spam filtering is not working.

I clicked unwanted now for some days on similar mails but my mail is not filtered in any way.

Am i doing something wrong or is this a bug??

Greetings 
André

---

### Post by Alexander Kirillov on 2005-04-19
[QUOTE=André]Hi,

i can't clarify this. But i can tell you that i also have the feeling that spam filtering is not working.

I clicked unwanted now for some days on similar mails but my mail is not filtered in any way.

Am i doing something wrong or is this a bug??

Greetings 
André[/QUOTE]
 You need to make sure that spamassasin is installed. This is the tool evolution uses for actual filtering.

---

### Post by GeneticFreek on 2005-04-19
I've had spamassassin installed and running for a couple months now, and I still get no filtering. When I press the junk button, it will state "learning junk" in the status bar, but nothing filtered as of yet. Is there somewhere to check the spamassassin options directly or to check that it is doing what it is supposed to be doing?

---

### Post by André on 2005-04-20
Hi,

i have Bogofilter installed. Shouldn't this be enough??

Greetings
André

---

### Post by Alexander Kirillov on 2005-04-20
[QUOTE=André]Hi,

i have Bogofilter installed. Shouldn't this be enough??

Greetings
André[/QUOTE]
 On my machine (fresh install of Hoary), evolution definitely uses spamd (which is a demonized version of spamassasin) - checked using process monitor. Package dependencies for evolution list "Recommend: spamassassin" and say nothing about Bogofilter. Thus,  I am not sure if Bogofilter playes any role at all - would appreciate any clarification of this. My advice is, install spamassassin.

---

### Post by bobdave on 2005-04-20
I'm sure I heard about plans to make Bogofilter work with Evolution because it was superior to SpamAssassin in some way (less resource intensive, perhaps).  If this is planned for the future, I'd think about avoiding SA and using filters in Evolution to throw mail through Bogofilter.

Is SA a good spam solution for the desktop?  It's available in universe, right?

---

### Post by Alexander Kirillov on 2005-04-20
Seems that indeed, there are plans to replace SA by bogofilter but they are not implemented yet. See these bugs: [bug 6989](https://bugzilla.ubuntu.com/show_bug.cgi?id=6989) 
 and [bug 3192](https://bugzilla.ubuntu.com/show_bug.cgi?id=3192)

---

