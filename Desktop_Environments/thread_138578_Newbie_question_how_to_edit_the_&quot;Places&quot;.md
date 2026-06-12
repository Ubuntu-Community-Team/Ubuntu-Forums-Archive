---
title: "Newbie question: how to edit the &quot;Places&quot; menu?"
date: 2006-03-02
forum: Desktop Environments
---

### Post by mority on 2006-03-02
I was so excited about accessing my Debian server via ssh through Nautilus that I entered a non existing folder in the folder input field in the "Connect to Server" dialog twice. Now there are sitting two broken entries in my "Places" menu wasting space and annoying me. Could anyone tell me how to ged rid of them?

I tried to right click on them but that would just open them and I searched every possible menu in Nautilus. I kinda searched these forums too but didn't find the solution.

---

### Post by akiro.yamamoto on 2006-03-02
Are they visible under Network servers?
If so remove them.

---

### Post by mority on 2006-03-02
Yes, they are, but when I try to remove them it says
> 
Error "Operation not permitted" while deleting "network://foo.bar.com"


I tried to do a "find" on the name of the network in my home directory but couldn't locate it. Where are those menu entries stored in the file system?

---

### Post by Ramses de Norre on 2006-03-02
Can you delete it as root?

---

### Post by mority on 2006-03-02
[QUOTE=Ramses de Norre]Can you delete it as root?[/QUOTE]

Well, to try this I would have to know where those entries are stored in the file system as I can't login to Gnome as root (and I don't want to, too, as there is normally no reason for doing it, is it?).

---

### Post by Ramses de Norre on 2006-03-02
> network://foo.bar.com guess that's the path.

---

### Post by mority on 2006-03-02
[QUOTE=Ramses de Norre]guess that's the path.[/QUOTE]

I think we're talking about cross-purposes a bit.
In my Places menu are entries pointing to a remote server. But the address of the remote server is wrong, so they don't work. Because they don't work I want to delete the entries. Apparently I can't do this through the Gnome/Nautilus interface (because of some permission problem, see above). So I have to know where the entries are stored on my local file system to try and delete them with sudo/root rights.

edit: I just resolved the problem. In "Places" -> "Network Connections" one can right-click on the entry and then "unmount" the network drive.
Stupid me, I should have seen this the first time.
Thanks for all the help anyways!

---

### Post by akiro.yamamoto on 2006-03-02
Good Job ;)

---

### Post by akiro.yamamoto on 2006-03-02
Post edited for Relavance ;) 
My mistake....
Entering TOO many posts at the same time . LOL
:)

---

