---
title: "[SOLVED] Thunderbird not displaying"
date: 2008-12-23
forum: General Help
---

### Post by pgdave on 2008-12-23
For the last 2 or 3 days, I have been unable to see my emails, via thunderbird. When starting up, the program shows the 'starting thunderbird' message in the task bar, then after about 8 seconds, this disappears, but no thunderbird window appears.

system/admin/system monitor shows two tasks: 'thunderbird' and 'thunderbird-bin', both sleeping.

Looking at home/.mozilla-thunderbird etc, I can see that emails are being received and stored on disk - it's just that I cannot see them at all.

I've tried moving the email folder to a backup location and running thunderbird afresh. That gets me the account setup screens, so I can set up the account again, but as soon as it goes to actually collect the email, it again fails to show a display.

Any ideas?

---

### Post by Titan8990 on 2008-12-23
Open the terminal and launch thunderbird from there:


$ thunderbird


report the errors it gives after thunderbird crashes.

---

### Post by pgdave on 2008-12-23
Starting thumderbird from the console results in a popup message at bottom right of screen = 'one message received in local folders' (or similar), then nothing. 

The bash prompt returns after I kill the 'thunderbird-bin' process in system monitor. The only message displayed is the 'killed' message.

---

### Post by Titan8990 on 2008-12-23
So the GUI is crashing but thunderbird keeps going?

---

### Post by pgdave on 2008-12-23
Nothing is crashing - it works perfectly, except that it won't display any screens. It's as if all video output is to /dev/null

---

### Post by pgdave on 2008-12-23
Now I've uninstalled and re-installed Thunderbird, and I still get the same result - no screen output after the initial setup screens. This is bizarre...

---

### Post by pgdave on 2008-12-28
Problem solved - as per [http://ubuntuforums.org/showthread.php?t=746017](http://ubuntuforums.org/showthread.php?t=746017)

Resetting screen resolution brought back the Thunderbird windows. I had previously had 2 monitors attached, and had removed one back to its Windows XP PC. 

Odd, though, that a complete wipe out and reinstall caused an invisible window - I'd like to know what file directs the program to display on an invisible window.

---

