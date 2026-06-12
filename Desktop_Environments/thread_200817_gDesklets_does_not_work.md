---
title: "gDesklets does not work"
date: 2006-06-20
forum: Desktop Environments
---

### Post by tdn on 2006-06-20
Hi.

A lot of the gDesklets does not work. And I get very unfriendly error messages. Some of them even showing me something that looks like source code. What am I to do with the source code as a user?

One of the desklets I have experienced this with is the one for creating stiky notes.

What is wrong? 
Do I need to install something to get them to work? If so, why doesn't the gdesklet package depend on this?

Why is the error messages so unfriendly?

---

### Post by meng on 2006-06-20
I have the same problem with sticky notes. So I removed it. One can ignore the error messages, and it still works, but I removed it anyway. I've found most other desklets work without error messages.

---

### Post by tdn on 2006-06-20
But this is not a solution to the problem...
I would really like to use this desklet.
If it is defect I think it should be removed from the package until it works.

Has this been reported as a bug?

---

### Post by taurus on 2006-06-20
Gdesklets is working fine for me here.  If you tell me what sticky note or where you download it, maybe I can check it out for you...  By the way, I assume you did run
```

sudo apt-get install gdesklet gdesklet-data

```

---

### Post by meng on 2006-06-20
[QUOTE=tdn]But this is not a solution to the problem...
I would really like to use this desklet.
If it is defect I think it should be removed from the package until it works.
Has this been reported as a bug?[/QUOTE]
What's stopping you from using it? If you set it to ignore error messages, the desklet still works, doesn't it? That is my experience. The real problem is not so much the error message, but that the desklet doesn't have great functionality!

---

### Post by tdn on 2006-06-21
Well... The error messages are stopping me. If I am supposed to just ignore the error messages, then why are they shown to me in the first place?
This is really bad usability.
Maybe I can live with this, but my mum certainly cannot.
I guess this is one of the reasons why Linux just isn't ready for desktop yet.
If the program gives errors then it should be fixed or removed from the package.

---

### Post by JGKC9AYC on 2006-06-23
Not only am I getting error messages (which I ignore), but also I have solid gray boxes where my gDesklets used to be & the gDesklet icon disappear from the menubar after my machine's been on for a while.
I tried going to the IRC channel as mentioned on their website, but nobody answers any questions even though there's 6 or 8 people in there.

---

### Post by patrick295767 on 2006-06-23
[QUOTE=tdn]Hi.

A lot of the gDesklets does not work. And I get very unfriendly error messages. Some of them even showing me something that looks like source code. What am I to do with the source code as a user?

One of the desklets I have experienced this with is the one for creating stiky notes.

What is wrong? 
Do I need to install something to get them to work? If so, why doesn't the gdesklet package depend on this?

Why is the error messages so unfriendly?[/QUOTE]

you dont have to unpack them.
just select the downloaded tar.gz, and zoou it should work... :KS

---

### Post by georgetoon on 2006-06-23
I'm having problems with Gdesklets, as well.  I successfully installed it and it ran great!  but when I tried to install a "quotes" widget the program froze up. Now, it will no start at all.  the main program window comes up, but no contents show.  It's a blank window.

I've uninstalled using Synaptic and that cleared the problem once.  I was able to start the program and previous widgets started up and ran automatically. Then, that that same "quotes" widget decided to launch and the entire program froze again.

I tried an uninstall and re-install twice and it did not help.   How can I clear this up?

---

### Post by scxtt on 2006-06-23
try removing ~/.gdesklets, that should get rid of all the user-specific settings (you'll have to reconfig it, but that's not to hard) ... make a backup if you want ...

---

### Post by georgetoon on 2006-06-23
[QUOTE=scxtt]try removing ~/.gdesklets, that should get rid of all the user-specific settings (you've have to reconfig it, but that's not to hard) ... make a backup if you want ...[/QUOTE]

Thank you.:) I didn't have to take this approach. 

Kind of weird...I was looking at the "recent documents" menu, picked the widget from gDesklets, the app launched!:)  I was lucky enough to get into the Shell window and uninstall the widget which was stuck.:)  Now all is well.:)

BTW, how do I get gDesklets to start each time I start Ubuntu?

---

### Post by scxtt on 2006-06-23
System --> Preferences --> Sessions : Startup Programs, Add

---

### Post by georgetoon on 2006-06-23
[QUOTE=scxtt]System --> Preferences --> Sessions : Startup Programs, Add[/QUOTE]

Yes, thank you.  What command do I use?  I tried "gDesklets" but that did not work.

---

### Post by scxtt on 2006-06-23
i haven't tried it myself, but see what these do for you:
[indent]$hostname [~]
:> ps -ef | grep desklets
$user     9087     1  0 06:23 ?        00:00:01 python **/usr/lib/gdesklets/gdesklets-shell**
$user     9091     1  1 06:23 ?        00:16:08 python **/usr/lib/gdesklets/gdesklets-daemon**[/indent]my bet would be the daemon, or possibly just gdesklets (*nix OSs are case sensitive) ...

---

### Post by georgetoon on 2006-06-23
[QUOTE=scxtt]i haven't tried it myself, but see what these do for you:
[indent]$hostname [~]
:> ps -ef | grep desklets
$user     9087     1  0 06:23 ?        00:00:01 python **/usr/lib/gdesklets/gdesklets-shell**
$user     9091     1  1 06:23 ?        00:16:08 python **/usr/lib/gdesklets/gdesklets-daemon**[/indent]my bet would be the daemon, or possibly just gdesklets (*nix OSs are case sensitive) ...[/QUOTE]

Yep! It was the case sensitivity thing. "gdesklets" worked!:)

Many thanks!

How do I get firestarter to start on start up when I don't have root permissions?

---

### Post by scxtt on 2006-06-23
if installed, it's always active ...

the nice editable config GUI on startup, hmm - maybe "gksudo firestarter" in Sessions? -- you'll most likely have to enter your password immediately ...

---

### Post by georgetoon on 2006-06-23
[QUOTE=scxtt]if installed, it's always active ...

the nice editable config GUI on startup, hmm - maybe "gksudo firestarter" in Sessions? -- you'll most likely have to enter your password immediately ...[/QUOTE]

Excellent!:)  Thank you!:)  then, I'll just option to start the interface on every now and again.:)

---

### Post by JGKC9AYC on 2006-06-24
So any idea why my gDesklets menu bar icon & starters disappear after a few hours & leave nothing but gray boxes on the desktop where they once were?

---

### Post by scxtt on 2006-06-24
after this happens, do you check to see if gdesklets is still running (is it crashing, or just 'closing' the desklets?)?

---

### Post by JGKC9AYC on 2006-06-24
[QUOTE=scxtt]after this happens, do you check to see if gdesklets is still running (is it crashing, or just 'closing' the desklets?)?[/QUOTE]

I've checked to see if it was running & it wasn't.  I was going to issue the "kill" command, but one can't kill something that isn't running.  I don't know what happened, but it does it consistently.  I've tried uninstalling & reinstalling to no avail.

---

