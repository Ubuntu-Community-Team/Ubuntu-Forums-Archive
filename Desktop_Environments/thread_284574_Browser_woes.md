---
title: "Browser woes"
date: 2006-10-25
forum: Desktop Environments
---

### Post by dalani on 2006-10-25
Can I rip out firefox, uninstall it and delete all trace of it on my computer??? and install another browser? 
I am very disappointed with firefox. The whole raison d'etre for linux for me was to browse safely.  To this day, I find with Firefox some pages dont load well if at all even after I clear the cache and switched off Ip6. As a precaution if things did not work out, I kept my dual boot Win98.  The same webpages that dont load in Firefox load instantly when I dual boot to  'you know what' and use, of all things, IE5!! ( its difficult to expalin to my two year old son why his favorite flash cartoon website  loads so slow under linux)

Now I have the Dapper CD and Im wondering if Opera will do the same thing or if swiftfox anybetter. Anyone run into this problem??? or recommend these browsers?? I am afraid I might rip out linux while trying to find a suitable browser.


I run hoary on a PII dual boot.

---

### Post by FyreBrand on 2006-10-25
If it's Flash website you're having trouble with then it isn't your browser that is the problem, but the Flash version.  Every browser you try will produce similar if not worse results.  Firefox handles these sites as good as any other browser you will install. Currently Adobe only provides Flash 7 for Linux while Flash 9 is provided for Microsoft and Apple.

There are some answers though.
1. You can patiently wait for Adobe to release Flash 9 for Linux.  It's right around the corner, but still a couple months away. -- not the best answer if you want to surf these right away.

2. You could install "wine" and use the Win32 version of Firefox.  Wine is a Microsoft Windows emulator that allows you to install some Windows 32 bit applications.  Firefox and Flash 9 are two applications that work pretty good with wine.

I would suggest option 2.  Here is a link on Ubuntu Documentation on [**Wine**]("https://help.ubuntu.com/community/Wine").

Usually wine works good with minimal, but it's not the simplest task to configure it and occasionally there are problems.  I would highly recommend reading that link at Ubuntu Documentation and also doing a search for "installing wine", "firefox on wine" and similar forum searches to read what other people have to say about it.  With this task research is a good idea.

---

### Post by dalani on 2006-10-26
I checked and it's not just flash sites. For instance from Linux/firefox logging onto heavily trafficked sites like google.com or even this one here ubuntuforums.org takes a looonnnnngg time. That's even after clearing the cache clean! I check the same sites with IE5 and the speed is instant from the same dial-up connection. 

Now the newer firefox in Dapper might resolve this or be worse if Dapper is more taxing on my present CPU...(that means a clean install and hope for the best not to mention countless hours configuring if something does not work)

or if I take your wine suggestion to heart, I might just upgrade the other side of my dual boot...(isn't that like using wine only it works exactly?)

---

### Post by FyreBrand on 2006-10-26
It's hard to tell exactly what or why you are having a problem because there aer so many factors involved.  I use Firefox 2.0, Konqueror, and Opera in Linux and Firefox 2.0 and IE7 on Windows at work.

Firefox is functioning exactly the same for me in both environments except for the flash sites.  I have a few problems with Opera on Moodle in both Windows and Linux, but that is the only site I have to use Firefox for that I can think of.

As far as load speed goes there's nothing I can say about that because there are so many unknown factors.  I dual booted with Windows XP and Dapper up until a couple months ago. I can't say that I noticed any difference in load times.

I'm sorry I can't be of any help here.

---

### Post by andiii on 2006-10-26
A two year old kid on the computer? :(

---

### Post by dalani on 2006-10-27
> **andiii said:**
> A two year old kid on the computer? :(

Yes. have a look at his favorite website: [http://www.thomasandfriends.com/ca/homepage.html](http://www.thomasandfriends.com/ca/homepage.html)

---

### Post by dalani on 2006-10-27
> **FyreBrand said:**
> It's hard to tell exactly what or why you are having a problem because there aer so many factors involved.  I use Firefox 2.0, Konqueror, and Opera in Linux and Firefox 2.0 and IE7 on Windows at work.

Firefox is functioning exactly the same for me in both environments except for the flash sites.  I have a few problems with Opera on Moodle in both Windows and Linux, but that is the only site I have to use Firefox for that I can think of.

As far as load speed goes there's nothing I can say about that because there are so many unknown factors.  I dual booted with Windows XP and Dapper up until a couple months ago. I can't say that I noticed any difference in load times.

I'm sorry I can't be of any help here.


That's the kind of data I need to make the correct choice.
Have you tried to multitask heavily on both? One thing I noticed is that the linux load meter maxes out on page loads and if I open eg. evolution, gimp and firefox (like I do when im sending pictures while checking webemail) the computer locks up churning away. Could you do that test scientifically and report the results? send me an email if you don't want to go public...

---

### Post by FyreBrand on 2006-10-27
I did that test using similar apps because I'm testing out KDE at the moment and they do suck up all my memory but almost no cpu usage.  This seems about normal though.  I will over-generalize and say that Linux likes physical memory and isn't shy about using it.  I don't think that's a bad thing just a little different.  If a system is a little lighter on memory then things can slog a bit (lets say somewhere around < 256MB and more like < 200MB).

I did visit the Thomas the Train site.  My daughter, who's 3, has decided that will now be one of our sites we visit.  Thanks ](*,) 

The site does work on my machine.  I wish I had a clever geek answer for you, but I don't.

---

