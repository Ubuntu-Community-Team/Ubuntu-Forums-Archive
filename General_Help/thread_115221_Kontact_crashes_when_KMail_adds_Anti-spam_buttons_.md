---
title: "Kontact crashes when KMail adds Anti-spam buttons to the toolbar"
date: 2006-01-10
forum: General Help
---

### Post by vitorsouza on 2006-01-10
Hi,

I configured KMail (running inside Kontact) to work with antispam (tried bogofilter, spamassassin or spambayes, same result) and when I manually add the action "Filter Classify as SPAM" (and also "NOT Spam") to the toolbar, Kontact crashes.

The message just before the crash is:

```
*** KMail got signal 11 (Crashing)
KCrash: Application 'kontact' crashing...
```

After that, when I start Kontact again, I get:

```
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
*** KMail got signal 11 (Crashing)
ERROR: Communication problem with kontact, it probably crashed.
vitor@seattle:~/.kde/share/apps/kmail$ KCrash: Application 'kontact' crashing...
```

To fix it, I have to edit ~/.kde/share/apps/kmail/kmail_part.rc and remove the lines that refer to the anti-spam buttons. Then, I have to classify as SPAM by right clicking on the message, which really bugs me.

[http://bugs.kde.org/show_bug.cgi?id=91294](http://bugs.kde.org/show_bug.cgi?id=91294) states that the problem is fixed in KDE 3.3, but I'm using KDE 3.5 and I'm experiencing the problem. Anyone else have been through this?

One more thing: does bogofilter work? I used it for weeks and it classified every single message as being 52% spam... Has anyone been through this also?

Thanks for any pointers,

Vítor Souza

---

### Post by Hangetsu on 2006-03-30
I'm having the same issues, and would love a solution!

---

### Post by Dianoga on 2006-07-26
I am having the same problems

---

### Post by Apostata on 2006-07-30
I've just run into this problem myself. I flagged some "ham" as NOT SPAM and it eventually crashed. Now whenever I load Kmail/Kontact it freezes.

I soooo don't want to use Evolution. Anyone else figure this out?

---

### Post by vitorsouza on 2006-08-01
After installing dapper (6.06 final) the problem was solved for me.

Vitor

---

### Post by Apostata on 2006-08-07
The fix for me was going into:

/home/blah/.kde/share/config/

and deleting **kmailrc**.

Although you'll need to re-configure your pop and smtp information afterwards (as well as filters), it did the trick.

---

### Post by bibliophile86 on 2007-06-20
Sorry for the bump.

I found a less destructive way to fix the problem.

1. Open the directory: /home/username/.kde/share/apps/kmail
2. Right-click the file kmail_part.rc
3. >Actions>Edit as Root
4. Scroll to section at the end of the document labeled <Toolbar>
5. Delete the two lines in that section that refer to marking a message as "spam" or "not spam".
6. Make sure the very last two lines of text are snug against the bottom of the toolbar section.
7. Save and close the file.
8. Launch Kontact and it should work now.

Again, sorry for the bump. I was having this same problem fifteen minutes ago and wanted to post my discovery.

---

