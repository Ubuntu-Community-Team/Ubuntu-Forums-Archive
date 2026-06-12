---
title: "FireFox stops saving my settings at random"
date: 2009-02-15
forum: General Help
---

### Post by ShinigamiKiba on 2009-02-15
This has been happening since the first time I started using Ubuntu and it's pretty much my biggest problem with the OS. After installing a bunch of extensions FF just up and resets its GUI settings and switching profiles and stuff doesn't help.
The only thing that resolves this problem is for me to delete my profile, get rid of all the mozilla/ff settings and start over with a fresh FF and if I'm lucky enough it won't mess up again, if not it'll mess up and I have to start all over again...it's very annoying.

Fortunately I stopped using FireFox and started using SwiftFox, dunno what that fixes but it seems I don't have this problem with it, however FF seems to perform better on this computer than SwiftFox now that it had a new update but the deleting of settings is still there.

So I dunno what to do, do I just stick to SwiftFox and hope for an update at some point and stop using Mozilla altogether and try and get used to Opera, which honestly I can't because I downright hate the browser.

The computer this happens on:
Duron 1.3GHz
512MB RAM

I know it's a no good system, but Ubuntu works great on it, I just wish I could use a good, smooth web browser with it too because both FF and SF aren't that good when it comes to performance, they load pages fast no problem but the browsers themselves are pretty laggy and slow.

---

### Post by ShinigamiKiba on 2009-02-15
bump, sorry not sure if bumping is ok here

---

### Post by ShinigamiKiba on 2009-02-15
man, this is one fast and active forum

---

### Post by MarblePanther on 2009-02-15
Did you use firefox from the repos or from mozilla?

You can always give Opera, Konqueror, Midori, Epiphany, etc... a shot too.  They are all much faster than firefox.

---

### Post by Bios Element on 2009-02-15
> **MarblePanther said:**
> Did you use firefox from the repos or from mozilla?

You can always give Opera, Konqueror, Midori, Epiphany, etc... a shot too.  They are all much faster than firefox.

Erm, Telling him to ignore the problem by using another browser isn't really helping. >.>

Make sure you have nothing you want to save from firefox and run the following commands.

```

sudo apt-get purge firefox
sudo apt-get install firefox

```

And see if that helps.

---

### Post by MarblePanther on 2009-02-15
> **Bios Element said:**
> Erm, Telling him to ignore the problem by using another browser isn't really helping. >.>

Make sure you have nothing you want to save from firefox and run the following commands.

```

sudo apt-get purge firefox
sudo apt-get install firefox

```

And see if that helps.

*Erm,*he mentioned that firefox is too slow a browser for him.

>  I just wish I could use a good, smooth web browser with it too because both FF and SF aren't that good when it comes to performance, they load pages fast no problem but the browsers themselves are pretty laggy and slow.

And I agree, firefox is the slowest browser I've used on linux.

---

### Post by cl333r on 2009-02-15
Reading the extensions log file could help figuring out what's the matter: go to the settings Firefox folder (mine is /home/fox/.mozilla/firefox/p3m8xx9y.default) and read the log file: extensions.log

If that helps you could report about the bug to the author of the corresponding extension so that in the future it eventually ships fixed.

---

### Post by cl333r on 2009-02-15
> **MarblePanther said:**
> *Erm,*he mentioned that firefox is too slow a browser for him.

He mentioned the opposite.

---

### Post by MarblePanther on 2009-02-15
> **ShinigamiKiba said:**
> I just wish I could use a good, smooth web browser with it too because both FF and SF aren't that good when it comes to performance, they load pages fast no problem but the browsers themselves are pretty laggy and slow.

no he didn't

What is everyone's problem today?

---

### Post by cl333r on 2009-02-15
I paid attention to this one
> Fortunately I stopped using FireFox and started using SwiftFox, dunno what that fixes but it seems I don't have this problem with it, however FF seems to perform better on this computer than SwiftFox now that it had a new update but the deleting of settings is still there.

---

### Post by MarblePanther on 2009-02-15
I simply mention the names of some smoother/faster browsers for him to peruse/ponder.  Must everyone get upset?  It is just a suggestion to his wish for a smoother browser.  that is all

*I come in peace*  :cool:

---

### Post by cl333r on 2009-02-15
Of course Peace :)
Remember the Ubuntu moto about humanity?
> We are what we are thanks to Mark Shuttleworth's money.
[http://uncyclopedia.wikia.com/wiki/Ubuntu](http://uncyclopedia.wikia.com/wiki/Ubuntu)

that was my last off topic.

---

