---
title: "amarok's little problem"
date: 2006-06-14
forum: Desktop Environments
---

### Post by elbryan on 2006-06-14
I've a little problem ..
When I select a mp3 in amarok to play it skips to another one and after to another else ..

I can hear no sound but with XMMS I can play mp3s ...

What should I do?

---

### Post by Lord Illidan on 2006-06-14
In Options, Select the xine engine..

Make sure you installed xine from synaptic.

---

### Post by mjm115 on 2006-06-14
Also make sure that you have xine-extracodecs installed

---

### Post by elbryan on 2006-06-14
I've enabled all the respository into synaptic but I can't find xine-extracodecs ..

---

### Post by mjm115 on 2006-06-14
I'm sorry, look for libxine-extracodecs.  It's in the multiverse repository.

---

### Post by elbryan on 2006-06-14
Ok now it works ^^ thanks a lot!!

---

### Post by jhr79 on 2006-06-14
[QUOTE=elbryan]I've enabled all the respository into synaptic but I can't find xine-extracodecs ..[/QUOTE]

Try to search forum for this. There was one post that helped me. You just need to add working mirror - some of the mirrors seem to miss some files.

Jani

---

### Post by mjm115 on 2006-06-14
[QUOTE=elbryan]Ok now it works ^^ thanks a lot!![/QUOTE]


Sweet!  Glad to have helped.

---

### Post by cjb on 2006-06-14
[QUOTE=mjm115]Sweet!  Glad to have helped.[/QUOTE]

Hi there, I'm having the same problem. xmms plays files, amaroK doesn't. I commented these lines into /etc/apt/sources.list:

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

but I can't find a libxine-extracodecs package. The closest-looking uninstalled things are the -dev packages for xine. Has the functionality I need moved into another package, or have I misunderstood what I need to do?

thanks for any help
James

---

### Post by Jucato on 2006-06-14
The multiverse repository where libxine-extracodecs is in, is not dapper-backports, but just dapper.

You probably have an entry in your sources.list like this:
> deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe

Now add multiverse to that, to make it look like this:
> deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe multiverse

Save sources.list, then do an update (sudo apt-get update). That should solve it.

---

### Post by cjb on 2006-06-14
[QUOTE=Fenyx]The multiverse repository where libxine-extracodecs is in, is not dapper-backports, but just dapper.

You probably have an entry in your sources.list like this:


Now add multiverse to that, to make it look like this:


Save sources.list, then do an update (sudo apt-get update). That should solve it.[/QUOTE]

Works fine now, thanks :-)

---

