---
title: "Making pcmanfm default file manager"
date: 2009-08-23
forum: Desktop Environments
---

### Post by del_diablo on 2009-08-23
Been to the wiki page of it that covers changing it to thunar, its more than poorly written for a page that is suppose to help people.
I am running Openbox with Pcmanfm. The only time i run into this problem, is when i say to Transmission that it is suppose to open the folder where the files i downloaded. It then proceeds and opens the "search" that my file manager got, but it does not open it.
So how do I change this behaviour to what it suppose to do?

---

### Post by XubuRoxMySox on 2009-08-23
> **del_diablo said:**
> 
I am running Openbox with Pcmanfm. The only time i run into this problem, is when i say to Transmission that it is suppose to open the folder where the files i downloaded. It then proceeds and opens the "search" that my file manager got, but it does not open it.

It's not clear what you are asking here, but I expect that you can open Transmission and tell *it* where to put your downloaded files. 

In Firefox, for example, I have it set up to put downloaded files on the desktop. That way I don't have to search for them, and I can then use PCManFM to drag them into whatever folders I wish.

Perhaps you can do the same with Transmission.

-Robin

---

### Post by del_diablo on 2009-08-24
Ok, its a bit unclear, so i try again: I want to OPEN the PLACE AFTER i am done downloading what the torrent drags down.

So i start a torrent and a few hours laters its done downloading its stuff. Then i want to open that location(ex: ~/Musik/Ramzor) from the client, but then it opens the search for my file manager instead of "opening" the location.

---

### Post by XubuRoxMySox on 2009-08-24
I don't think the problem is in PCManFM, but in the application. And the title of this thread is misleading... I thought you want to make PCManFM your default file manager...

I'm not familiar with that application at all so I don't think I can answer your question. I can only suggest that you pose the question more clearly in the General Help forum.

-Robin

---

### Post by del_diablo on 2009-08-24
> And the title of this thread is misleading

Blame the IRC channal for lacking somebody with knowledge. 

Onto the question:
Then where does Transmission get its information on what is the default filemanager? I know for one that using "nautilus ~/Desktop" and "pcmanfm ~/Desktop" yields the exact same results in both file managers.

> I'm not familiar with that application at all so I don't think I can answer your question. I can only suggest that you pose the question more clearly in the General Help forum.

I would if that was the correct section for the tread. Its not. Properly that is. And that forums tends to be spammed down in a fashion that makes it even less of an idea of posting it since its over the "general help" level.

---

### Post by del_diablo on 2009-08-26
How come NOBODY knew this? So i got a nice hint from the almost dead transmission IRC channal, it got 2 choices of picking the application depending on how its compiled.
I bet its then [xdg-open](http://man.he.net/man1/xdg-open) and the location of the config is ~/.local/share/applications/. or /usr/share/applications/
And also for some weird reason, the wiki on changing file manager is ALSO not talking about this. It should have.

---

