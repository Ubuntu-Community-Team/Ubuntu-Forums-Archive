---
title: "Links in Evolution dont Open browser"
date: 2005-10-20
forum: Desktop Environments
---

### Post by Darrin on 2005-10-20
Hyperlinks in Evolution wont open firefox unless the browser is already launched. Shouldnt clicking on the link open firefox?

---

### Post by Dr. Nick on 2005-10-20
Havent used evoulition but just a guess, Check System-Prefrences-Preferred Applications Web Browser tab. Is > mozilla-firefox %s the command?

If thats right it might be a setting in evoulution

EDIT
Just tried it using Thunderbird and links open even if FF is closed, so it should be posible just not sure where to set it, If changing preferred apps does nothing Im not sure what will.

---

### Post by Darrin on 2005-10-21
Looks like firefox wasnt checked as the default web app. Checking it worked. Thank you.

---

### Post by jmooney on 2005-12-14
[QUOTE=Darrin]Looks like firefox wasnt checked as the default web app. Checking it worked. Thank you.[/QUOTE]

I'm having the same problem.  It used to work, now it doesn't.  Could you explain what you did?  Did you make this the default web app in Evolution or through a GNOME config dialog?

What did you do?

Thanks,

Joe

---

### Post by sethmahoney on 2005-12-14
Did you by chance install firefox 1.5?  I've had the same problem ever since I upgraded from the default version.

---

### Post by jmooney on 2005-12-14
[QUOTE=sethmahoney]Did you by chance install firefox 1.5?  I've had the same problem ever since I upgraded from the default version.[/QUOTE]

No, not yet.

Joe

---

### Post by Dr. Nick on 2005-12-14
[quote=jmooney]I'm having the same problem.  It used to work, now it doesn't.  Could you explain what you did?  Did you make this the default web app in Evolution or through a GNOME config dialog?

What did you do?

Thanks,

Joe[/quote]

If he folowed my instructions it was in the gnome config. System Menu- Prefrences- Prefered Applications. Set webrowser to custom then command is firefox %s

---

### Post by cstudent on 2005-12-14
I upgraded to FF1.5 and had to change preferred applications to firefox instead of mozilla-firefox.

---

### Post by jmooney on 2005-12-14
[QUOTE=Dr. Nick]If he folowed my instructions it was in the gnome config. System Menu- Prefrences- Prefered Applications. Set webrowser to custom then command is firefox %s[/QUOTE]

OK, I did that, but it won't "take".  That is to say, I change the custom radio-button option from "mozilla-firefox %s" to "firefox %s" and click "OK".  When I re-open this dialog however, the custom radio button is no longer selected.  Instead, the radio button above it is selected with the option "Firefox" in the pick window.

I've also tried putting "/usr/bin/firefox %s" in the custom radio-button box and that will "take".  However, I still can't get firefox to open when I click on a link in  Evolution.

The thing is, this worked before, I'm not sure how it changed.  Perhaps if there was some good documentation on GNOME?

---

### Post by jmooney on 2005-12-15
The Plot Thickens...

Turns out that this problem is only occuring in one specific e-mail message.  All the other messages with included links work just fine.

...puzzling...

---

### Post by dcstar on 2005-12-16
[QUOTE=jmooney]The Plot Thickens...

Turns out that this problem is only occuring in one specific e-mail message.  All the other messages with included links work just fine.

...puzzling...[/QUOTE]
Possibly a Virus e-mail with a munged link, not opening it could be Linux's way of protecting you from Windows crap.

---

### Post by JoaoMachado on 2007-05-05
Just an update on this thread, I was having the same issue where, links in the email message would not open firefox browser, the browser would have to be already open. For me on Fiesty, the cause was, that in gnome control panel for default apps, I had the browser opening in a new tab, but I also had it set to do the same within Firefox, the fix was to have gnome only open the browser, and leave the setting in Firefox to open in new tabs.

It may work the other way around as well, but I did not try. just thought I would pass this on in case anyone else was having the same issue.

Joao

---

