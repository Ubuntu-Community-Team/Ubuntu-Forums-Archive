---
title: "unity with no launcher"
date: 2011-10-23
forum: Desktop Environments
---

### Post by tmcmurph on 2011-10-23
I upgraded and it forced me to use unity. There is no launchbar on the left or anywhere. How do I get the launchbar to appear? Moving mouse to left side does nothing.

That or just give an option to revert to the gnome desktop that actually WORKED.

---

### Post by Frogs Hair on 2011-10-23
What version of Ubuntu ? If you are using 11.10 there is no Classic Ubuntu Gnome 2 session because it uses Gnome 3   . you could try  and  Alt + F2 or Crtl + Alt + T and run the following command .```
unity --reset
```

[http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html](http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html)

---

### Post by tmcmurph on 2011-10-30
Still no launcher. Thanks for the suggestion but this is the last straw. I love Ubuntu but after 5 years this Unity is making me look for another distro. If I had wanted someone else's decisions forced down my throat I'd have stayed with Windoze.

The previous interface worked fine and I was very happy. This upgrade with no way back and forcing Unity on me is ignorant at best. Having it not work AT ALL is just stupid.

---

### Post by Mark Phelps on 2011-10-31
At the risk of getting FLAMED, I will agree that this Ubuntu version is the worst ever!  I've been using Ubuntu since 7.04, so I know my way around it a bit, and even though I've only used 11.10 for a few days, I've had it crash and seize up on me repeatedly, yesterday UNITY vanished, and in the process, it trashed a document I had been working on for two days (and yes, I saved the changes every 15 minutes)!

If you're interested in recovery UNITY, read the info in the link below:

[http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html]("http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html")

---

### Post by grahammechanical on 2011-10-31
Now, who is doing the flaming?

I have not had any problems with 11.04 or 11.10. I can get to do what I want in 11.10 just as I did in 10.10. Perhaps I do not want to do as much as others. There you are.

Regards.

---

### Post by raja.genupula on 2011-10-31
Hi make sure that in compiz settings unity box enabled ...

if you wanna get it type **ccsm** in your terminal and then make sure that its enabled. 

all the best.

---

### Post by Mark Phelps on 2011-10-31
> **raja.genupula said:**
> Hi make sure that in compiz settings unity box enabled ...

if you wanna get it type **ccsm** in your terminal and then make sure that its enabled. 

all the best.

The Unity box WAS checked -- and it still trashed UNITY as soon as I opened ccsm!

---

### Post by rinrada on 2011-11-01
I am getting exactly the same problems.

After using it for several months without any problems, yesterday I booted up my desktop (Ubuntu 11.04) and the left side launcher and the top menu bar were both missing. I also found all the standard shortcut keys were disabled. I still had access to Terminal as I had created a personal shortcut which for some reason was not disabled.

I did all the usual things from various threads (check Unity with ccsm, etc) to no avail, so I tried upgrading. It upgraded fine but I still have the problem. In this thread I saw the
>unity --restore
option, which I ran. It did a lot of things but near then end I got a message that went something like "This should not be happening, you should probably submit a bug report".
Needless to say, the unity restore did nothing for the problem but did successful disable my shortcut for the Terminal. So now I cannot use the computer at all.

I am writing this on a laptop which can (or at least could beforehand) connect to my desktop via ssh. Any help would be much appreciated.

---

### Post by Mark Phelps on 2011-11-01
> **rinrada said:**
> Any help would be much appreciated.

Then go to the link in my post and do the commands indicated there.  You will have to remove unity and compiz, clean up the remainder, and reinstall both.

---

### Post by tmcmurph on 2011-11-02
[http://linux-software-news-tutorials.blogspot.com/2011/10/ubuntu-1110-oneiric-remove-unity-and.html](http://linux-software-news-tutorials.blogspot.com/2011/10/ubuntu-1110-oneiric-remove-unity-and.html)

This is a great link to how to get rid of Unity and go back to something that actually works. 

Seriously I don't know of ANYONE who has tried 11.10 (about 12 people) who kept it. All have gone back to the classic. All are sysadmins who can make most things work but just couldn't be bothered to use Unity. 

UNbuntu is the nickname for it (UNusable, UNbelievable).

Thanks for the fix Unity link above Mark, I may give it a try when I have nothing better to do ;)

---

