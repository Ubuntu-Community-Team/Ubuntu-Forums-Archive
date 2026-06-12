---
title: "Counter-Strike Source Dedicated Server"
date: 2007-05-07
forum: Gaming &amp; Leisure
---

### Post by mistaWAC on 2007-05-07
I'd like to first start with two things, hello and thank you!  Hello to everyone in the Ubuntu community and thank you to anyone that has contributed to the advancement of Ubuntu as well as the people that are always helping everyone else.  There are too few of you left.

Now, onto business.  As my title depicts I'm trying to get a CS:S Dedicated Server up and running. but there is a problem.  I'm like, 95% new to Ubuntu.  I've had it for near two weeks now and am still having trouble adapting to it.  The fact that the OS is better operated through a command line drives me crazy because of all the commands I'll need to memorize.  What my main issue is right now is getting CS:S to run.  I Googled and found a really good tutorial, but halfway through it lead me to another site that is no longer in existence.  Since that happened I've been in a world of confusion as to what to do.

What I'm asking for is someone that can really help me get this accomplished.  Someone that can sorta coach me through step by step and get this done so I can learn a few things in accomplishing this.  If anyone would be able to help me or direct me to a good tutorial I'd be greatly appreciative.  I've been on Windows my entire life and am finally branching out to something new before I jump into college.  I'm generally a quick learner when I am taught things, I just can't teach myself something I don't know.

Thanks again for any help you guys can give!

---

### Post by dfreer on 2007-05-07
[http://wolphination.com/linux/2006/03/29/how-to-setup-a-cssource-dedicated-server/](http://wolphination.com/linux/2006/03/29/how-to-setup-a-cssource-dedicated-server/)
Never done this myself, BTW, although I play CS:S in ubuntu using wine.

Compared to other linux distros, ubuntu barely requires usage of the CLI. However, any guide/tutorial you follow online will almost surely make you use it. Why? because it is eaiser to tell someone to "copy and paste this into the terminal" then to tell them "click on System > Adminstration > Users and Groups, find this tab and click this button".
but at least you are willing to learn the CLI. you'll find the more you use it, it's just eaiser sometimes to use than the GUI.

---

### Post by Moustacha on 2007-05-07
[http://www.srcds.com/db/engine.php?subaction=showfull&id=1098643920&archive=](http://www.srcds.com/db/engine.php?subaction=showfull&id=1098643920&archive=)

If you're going to be running it on a server that is **not** connected to the internet, remove the gateway in your network settings otherwise it will be horrendously slow.

Also, if you want a high(er) tickrate server, add -tickrate *30>integer<=100* to the command to start the server, so it looks something like this
./srcds_run -console -game cstrike +map de_dust +maxplayers 16 -autoupdate -tickrate 100

It's also easier to save the start command to a text file and just run that when you want to start the server instead of remembering the command(s).

eg.
open a text editor (gedit, vim); paste this into it:
./srcds_run -console -game cstrike +map de_dust +maxplayers 16 -autoupdate

save it, make it executable
eg chmod +x server.sh
then run it either by double-clicking and running in terminal, or
cd *patch-to-folder*
./server.sh


I think that should be all...

---

### Post by mistaWAC on 2007-05-08
Dfreer, thanks for that link, there's a problem though.  I followed it all the way to the server.cfg file and it then directs me to the mani-admin-plugin.com forums and the thread it uses doesn't exist anymore.  So I'm stuck guessing my way through it, which I don't think I did right.

Moustacha, thanks for that website.  I'll check it out when I get home tonight. It looks pretty solid...

And great thanks to both of you for the quick replies and some pretty good help!

---

