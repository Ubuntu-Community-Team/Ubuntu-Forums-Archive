---
title: "How do I make dosbox exit when returning to c:&gt;?"
date: 2006-01-03
forum: General Help
---

### Post by daller on 2006-01-03
Hi There,

I use dosbox (from the repos) to setup a lot of DOS games for my littlesister!

Those are:

Supaplex
Jazz Jackrabbit

When I exit the game, I get to a "console" where I have to type "exit" and press enter, to return to KDE... (exit dosbox)

Is there a way to do this automatically?

And as an other question - If you know the games - do you know any linux alternatives to these games?

---

### Post by ape on 2006-01-03
From the dosbox manpage:

 -exit  dosbox  will  close  itself  when  the  DOS program specified by
              fileends.

   
Looks like you just need to start dosbox with the -exit argument.

---

