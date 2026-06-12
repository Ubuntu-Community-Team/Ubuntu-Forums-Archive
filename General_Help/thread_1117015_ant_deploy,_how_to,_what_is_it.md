---
title: "ant deploy, how to, what is it?"
date: 2009-04-05
forum: General Help
---

### Post by primaxx on 2009-04-05
Hi,

This post should never have been posted here, but since it seems the Open-Xchange forum is more or less dead, I hope I'll get some help here.

I have translated (almost) all of the GUI of Open-Xchange to Norwegian, following these threads on the OX-forum:
[http://www.open-xchange.com/wiki/index.php?title=GUI_Translation](http://www.open-xchange.com/wiki/index.php?title=GUI_Translation)
and
[http://www.open-xchange.com/wiki/index.php?title=Open_Xchange_Installation#IV.4._Open-Xchange_GUI](http://www.open-xchange.com/wiki/index.php?title=Open_Xchange_Installation#IV.4._Open-Xchange_GUI)

My problem is when I get to the point where it says```
After that, the new translation must be transformed to JavaScript
and copied to its final destination on the web server.
This is done by starting Ant again, as described in section [IV.4]("http://www.open-xchange.com/wiki/index.php?title=Open_Xchange_Installation#IV.4._Open-Xchange_GUI")
of the installation tutorial:

ant deploy

```I understand *nothing*.

So, I asked in their forum
[http://www.open-xchange.com/forum/showthread.php?t=3395](http://www.open-xchange.com/forum/showthread.php?t=3395)
but I still haven't, after several days, got any response.

Are there anyone here that understands English better than me, and can explain to me what OX wants me to do?

Thank you for any help!

---

### Post by jespdj on 2009-04-05
[Ant](http://ant.apache.org/) is a build tool written in Java (kind of like 'make').

Did you see that the text you quoted contains a link to an instruction manual which explains in detail what you should do?

You'll probably need to install Java and Ant:
```
sudo apt-get install sun-java6-jdk ant
```
And then simply run the given command:
```
ant deploy
```

If you don't know anything about software development, it might be hard to understand what it all means and you'd better find a developer of the software you're talking about to help you with this. It's a bit hard to give you a course in software development in a forum topic...

---

### Post by primaxx on 2009-04-05
Thanks for responding!

Yes, I saw the link, I inserted it myself.
I also don't expect anyone here to teach me Java! :grin:

It's just that I'm so spoiled with this forum where whatever someone asks the response is always very concise, with just a few commands in the terminal fixing all sorts of problems.

Thanks, anyway!
(I'll have to reinstall Zimbra...)

Edit: I had allready installed ant, but I had no idea wether this was a simple task easily explained or not.

---

