---
title: "M1330 laptop screen darkens after 1 or 2 minutes"
date: 2009-02-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by TimDaniels on 2009-02-26
After one or two minutes of inactivity - like when I'm reading a news article - the screen on my XPS M1330 laptop darkens if it's on battery power.  It doesn't do this under converter power or under Vista.  It seems to be an Ubuntu battery management thing.  Is there a parameter that will extend the timeout period for full screen brightness, and if so, how does one access it?

*TimDaniels*

---

### Post by NoReflex on 2009-02-26
Hello!

Which version of Ubuntu are you using?
You could go to System -> Preferences -> Power Management and check the options there.

Best wishes,
NoReflex

---

### Post by TimDaniels on 2009-02-26
That did it!  Thank you.  I unchecked Reduce Backlight Brightness and it didn't dim when I switched to battery, and I unchecked Dim Display When Idle and it was still bright after 7 minutes of inactivity.  There's another problem with only 0%, 50%, and 100% as the options for brightness, but that's another thread.

*TimDaniels*

---

### Post by biocorp on 2009-02-26
> **TimDaniels said:**
> That did it!  Thank you.  I unchecked Reduce Backlight Brightness and it didn't dim when I switched to battery, and I unchecked Dim Display When Idle and it was still bright after 7 minutes of inactivity.  There's another problem with only 0%, 50%, and 100% as the options for brightness, but that's another thread.

*TimDaniels*

If you are using ubuntu 8.04 try this:
put "blacklist video" in /etc/modprobe.d/blacklist

---

