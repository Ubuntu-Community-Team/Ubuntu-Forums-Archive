---
title: "NVIDIA Card not recognized in Wine"
date: 2007-05-15
forum: Gaming &amp; Leisure
---

### Post by celiothrkn on 2007-05-15
I have the latest drivers for my NVIDIA 6150 in my Ubuntu.

I tried to wine Prince of Persia: Two Thrones. At initial startup (in wine), POP3 launches a system requirement check. It recognizes all my hardware and they all pass except my video card (in fact, it claims I do not have one).

Is there any way I can get wine to recognize my NVIDIA card so that the POP3 passes the system check?

Sorry if this is a silly question. I did try a brief Google search before posting.

---

### Post by misfitpierce on 2007-05-15
Are you sure they are confured properly? and also are you sure prince of persia is fully suopported on Wine... I use cedega so just asking.

---

### Post by hikaricore on 2007-05-15
Normally I would suggest the wine application database, but in this case:

[http://appdb.winehq.org/appview.php?iVersionId=5612](http://appdb.winehq.org/appview.php?iVersionId=5612)

There's nearly nothing there.

You may want to be more specific about what's happening for those like myself unfamiliar with the game.

Are you trying to run it or install it?  Sometimes installation issues can be overcome by copying an install off of an existing windows partition where it might already exist.  This is not always the case but i thought it was worth mentioning.

You may also want to contribute to the application database by posting your experiences and findings on the page for your game which I linked above.  Good luck,


--Aaron

---

### Post by Cappy on 2007-05-15
According to that wine database it says it won't work because you can't bypass the CD Protection. Rated as "garbage" and they said it's not fixed in the newest wine. They didn't outright say if it would run with a cd-crack or not, but I assume that it won't.

---

### Post by celiothrkn on 2007-05-15
Interesting. Well, even though the WINE database says it doesn't run, mine runs.

In any case, this is a screenshot of what I get when I run POP3 in WINE and Crossover Pro.

[IMG]http://img379.imageshack.us/img379/2585/pop3crossoverprory1.png[/IMG]

So, even though my Feisty plays sound and recognizes my NVIDIA's 3D acceleration, my WINE (or Crossover Pro, for that matter) does not see it, and claims I have neither, which is why I can't launch the game. Any ideas how I can get my WINE to recognize them?

---

### Post by DoktorSeven on 2007-05-15
My guess is that the config utility is looking for something that Wine doesn't implement.  Chalk it up to Wine not being perfect when it comes to running stuff like that.

---

### Post by hikaricore on 2007-05-15
Have you looked around for a nocd hack or alternate installation instructions?

These usually bipass the configuration chite.

---

### Post by celiothrkn on 2007-05-16
Yea, I'm assuming that No-CD cracks would fix most games. Except POP3 demands that you run the system hardware first.

In other words, after installation, there's a PrinceofPersia.exe and a POP3.exe. The crack replaces POP3.exe, which I believe to be the main game. Yet when I try to WINE that, it says that "You must start the game with PrinceofPersia.exe." Oh well.

I do have tiny good news. I updated my WINE from 0.9.33 (from Synaptic Package Manager) to 0.9.37 (from the WINE website). It seems the sound card is detected now. Still no luck detecting the video card though.

---

