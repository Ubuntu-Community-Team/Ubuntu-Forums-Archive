---
title: "e-mail custom directories possible?"
date: 2006-06-25
forum: Desktop Environments
---

### Post by dgermann on 2006-06-25
Hi--

Here is what I would like to do. Is it possible? What do I need to do to make it happen?

I get e-mail for some specific projects I am working on. Call them Project ABC and Project XYZ. I also get the usual run of general e-mail, not related to my various projects.

I would like to have all the e-mail for Project ABC to be in the /projects/ABC directory, and all for XYZ to be in the /projects/XYZ directory. General e-mail can reside wherever the e-mail client wants to put it.

Ideally, the e-mail that says in the subject line it is for ABC will automagically go directly to the ABC directory. If that is not possible, then I should be able to easily export it to that folder.

So, is this possible? How? What client would be best for this--Evolution, Thunderbird, something else?

Thanks!

---

### Post by aysiu on 2006-06-25
I'm pretty sure every email client can do this, but I know for sure Thunderbird has filters you can set up.

---

### Post by dgermann on 2006-06-26
aysiu--

Thanks for the quick reply.

What I see when I click where you indicated is the ability to move the message to something called "local folders," which looks to me to be something stored in /home/username/.mozilla-thunderbird or something like that--rather than in a project directory such as /project/ABC.

I think I saw something about Thunderbird keeping a database of all messages.

What looks to me like it might do something similar would be an export function, which I have seen in Evolution.

Or perhaps I could do a soft link to the other directory from under .mozilla-thunderbird?

Am I missing something?

Thanks, aysiu!

---

### Post by aysiu on 2006-06-26
Hm. I guess I see your point.

I was thinking of filtering to different email accounts, but you could create different folders *within* local folders and then symlink them somewhere else, I suppose.

---

### Post by dgermann on 2006-06-26
aysiu--

Thanks.

Maybe someone else has an idea and will chime in here, or maybe we have found all the possibilities.

Thanks for your help!

---

