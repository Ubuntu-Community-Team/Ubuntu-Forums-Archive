---
title: "arts borked?"
date: 2005-12-28
forum: General Help
---

### Post by snowsquirrel on 2005-12-28
why won't this let me post?  is my post too long?

~S

---

### Post by snowsquirrel on 2005-12-28
It seems I am only allow to make short posts, so I will break it up.

I want to enable full duplex with artsd, so I can record sound.  So I run 'kcmshell artsd' and check 'full duplex'.  Which causes the kcmshell to lock up.  Wait... wait... ok, now logout.  That hangs, until I manually kill all instances or artsd and artsshell.

---

### Post by snowsquirrel on 2005-12-28
Login, I get a message saying knotify has problems, would I like to disable arts? I say no, and I get no error message.  But I notice that I don't get any kde sounds (i.e., I can play xmms, but I can't I don't get the usual alert-bings.)  

pgrep -lf shows two instances of artsd running, both mine, both with option -d. Hmmm....  Lets kill those.  Check again, two more! 

Hmm....  Ok, lets just disable it and see what is going on. 'Run kcmshell arts' disable sound. Logout, just for safety, hangs, until I kill all artsd processes.

---

### Post by snowsquirrel on 2005-12-28
Login in, pgrep shows 2 artsd's trying to run with a -d.  WTF? pstree shows that initd is launching artds, two at a time, only two pids apart.  Why?  I know my soundcard supports full duplex, with alsa (Turtle Beach Santa Cruz via cs46xx).

---

### Post by snowsquirrel on 2005-12-28
Getting desperate.  Even though I have sound disabled, I will disable full duplex via kcmshell arts.  Hitting 'ok' hangs it.  'ps' shows two artsd (suprise, suprise), and an artsshell, all in mode sleep.

While I am snooping through process trees, I also notice that I always have two instances of gpg-agent running.

Ok, getting frustrated, must get help.   If this is not the place to get help, does anyone know of a place that might know about this sort of thing?

~S

---

### Post by snowsquirrel on 2005-12-28
If anyone knows why I would be unable to make all of the above posts, as one large post, I would love to here it.  I tried the exact same text, as a single post, with Firefox, Konqueror, and Opera.

But tell me in a PM, as to keep this thread on topic.

Thanks,

~S

---

### Post by newuser111 on 2005-12-29
enabling full duplex also caused arts problems for me

but it works fine when its disabled

---

### Post by snowsquirrel on 2005-12-29
[QUOTE=newuser111]but it works fine when its disabled[/QUOTE]
Sound *input* works fine?

I am still wondering why there are so many instances of it, and gpg-agent.  I will likely need help from a Kubuntu developer, or kde developer for that though.

I have not had any luck recording sound with half duplex, but I will try again.

~S

---

