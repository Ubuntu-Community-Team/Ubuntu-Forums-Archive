---
title: "Spyware  in linux"
date: 2009-01-11
forum: General Help
---

### Post by GammaPoint on 2009-01-11
It seems that spyware doesn't really affect linux users. Is this because it's specifically designed to target windows or does linux actually prevent it from working?  

Also, doesn't spyware usually infect when the users visit websites? Can the creators of spyware not detect what OS you are running and then run the appropriate spyware code based on that reading?  

I've just been curious about this stuff. If I have a discussion with someone about it I don't want to sound as n00bish as I do now.

---

### Post by binbash on 2009-01-11
both

some websites can leave cookies to detect your language or country but that is not important.They can detect the os but cant run anything if you do your permissions correct.

---

### Post by hikaricore on 2009-01-11
There really isn't any way for software to be installed outside of the user's home directory even if it were possible for a web browser to install spyware under Linux.

The biggest issue in the Windows environment is with people who we'll just call "tards"
for short, clicking on and running every piece of software that ever comes their way.

Another common issue is the use of Internet Explorer and it's failtastic ActiveX
controls which can give direct access to users systems.

In a Linux environment these problems are virtually non-existant.

The worst a piece of Linux spyware could do is install itself in your home directory and set itself to run at session start.
(assuming it accessed the gnome or kde config files properly and these would differ from version to version of gnome/kde)
At which point you could simply kill and delete it.  As it would have no system access outside the user level it could make
itself a service nor could it install other copies of itself to run outside of this home folder environment.

Worst case you could delete the user and recreate them having completely wiped the spyware out.

---

### Post by hikaricore on 2009-01-11
Not to mention I don't think anyone is making spyware for Linux.

Hell aside from rootkits there are what like 20 Linux virii in existence?  And most of them are just proof of concept.

---

### Post by mcduck on 2009-01-11
The stricter way Linux/Unix systems handle permissions compared to Windows simply makes creating viruses and spyware/adware a lot harder..

Unlike Windows, any file can't be executed, the file must be set as executable before you can run it. New files created (or saved into your browsers cache directory) won't be executable by default. So you'd pretty much need to fool the user to manually change the file's permissions and run it..

Even then, the file program would only have the same permissions as the user who started it, so it wouldn't be able to do anything outside that user's home directory. As all your programs and system configurations etc. are outside your home and owned by root, not you, that program would have a bit harder time trying to stay hidden or getting itself to start automatically.

And, in the end, if it would succeed in all that the root user could still remove annoying program from normal user's account without any troubles. Root has all the power while the program would have very little.

I'm not saying it would be impossible to create such a program for Linux, what I'm saying it's very, very hard while doing the same on Windows is quite easy. Knowing the user bases of both OSes, and that Linux users tend to have a bit more knowledge about computer stuff, it's no surprise that spyware writers choose the easier and more profitable way of annoying Windows users. :D

---

### Post by scouser73 on 2009-01-11
> The biggest issue in the Windows environment is with people who we'll just call "tards"
for short, clicking on and running every piece of software that ever comes their way.

PMSL that's so true.

---

### Post by bgerlich on 2009-01-11
There is no Linux spyware (and probably there never will be) because there is no point in writing one. To install it you would need root privleges and if you have (gain) root privleges you can spy on users using standard system tools - no point in creating special software.

---

