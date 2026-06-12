---
title: "gam_server memory leak still unresolvable"
date: 2006-03-08
forum: Desktop Environments
---

### Post by adam.stokes on 2006-03-08
Yes i know people have this issue everywhere, my biggest gripe is that so many users are seeing this issue but non of the ubuntu team is able to reproduce this?? Its there and it hogs up memory considerably and it brings my system down to a crawl..

I am trying to get around this issue without having to do source compiles but still having no luck. 

I've appended 'noinotify' within the kernel line but gam_server just keeps on polling and polling and memory is being taken up by the minute.

I am reluctant at just pointing gam_server to /dev/null, however, I do use kde so Im not sure how much of a benefit gam really has on it.. hopefully none.

I am aware the next version of gnome will be using direct inotify so we can get rid of fam/gam completely..

but until then has anyone come up with a workaround at all? ive searched the forums, google, over and over but only came up with the above. Oh also tried limiting the poll to just /tmp within /etc/gamin/gaminrc but still problem persists :(

---

### Post by danish_demon on 2006-03-08
i also have experienced problems with this and the only thing i've ever done is go in the task manager and shut it down.  not a very good solution, but it at least (temporarily) helps.

---

### Post by adam.stokes on 2006-03-08
yea ill run a pkill on it but it just comes right back :(

---

### Post by stoeptegel on 2006-03-10
This thing is leak! 938MB of RAM usage here :(
Where do i need this process for?

---

### Post by stoeptegel on 2006-03-10
This is ridiculous, it goes up with 0.5 MB per second! Me goes back to Hoary, sorry guys, too many bugs.

---

### Post by unnes on 2006-04-27
I noticed that my machine was very slow as well, and saw gam_server taking up 400+mb of RAM.

What does this process even do? Is there any of preventing it from running? There don't seem to be any immediate negative effects of killing it.

---

### Post by stoeptegel on 2006-04-27
I filled a bugreport for this RAM usage more than a month ago.
There was one person to confirm this bug two weeks ago or something, but i also can't detect any procedure from the devs.

Sadly enough i have left breezy for this bug and started using dapper. 

But dapper has a bug with this gamin process too (10-12% cpu use constantly), and for what i know has been there from at least flight 4 until the current beta.(happened me two days ago again)
I seriously hope there will be some action on these bugs. And i hate to say, but i think on some parts we are losing it.

---

### Post by unnes on 2006-04-27
Actually poking around a little bit, I found the OP's blog, where he linked to the following thread:

[http://ubuntuforums.org/showpost.php?p=551050&postcount=9](http://ubuntuforums.org/showpost.php?p=551050&postcount=9)

I followed the instructions, and it seems to work fine now -- no memory issues. Apparently the Dapper version of gam_server has fixed the leak.

---

### Post by stoeptegel on 2006-04-27
[QUOTE=unnes]Apparently the Dapper version of gam_server has fixed the leak.[/QUOTE]

Doubt it, since this CPU bug in dapper popups up rarely here(but if is it active it's constant 10-12% CPU) and i haven't a gamin update seen coming by. 
But lets hope it's fixed yes.

---

