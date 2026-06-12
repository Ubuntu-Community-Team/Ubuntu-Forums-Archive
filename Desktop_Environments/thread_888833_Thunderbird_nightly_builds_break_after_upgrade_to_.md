---
title: "Thunderbird nightly builds break after upgrade to Hardy"
date: 2008-08-13
forum: Desktop Environments
---

### Post by lduperval on 2008-08-13
Hi,

(This was also posted on the Mozillazine forums).

I upgraded my Ubuntu system today to install 8.0.4.

I have been using the Thunderbird nightly builds for a while because I need the latest Lightning extension and there are some features that only work with nightly builds. IOW, I don't use the default Ubuntu version of TB, I use version 2.0.0.17pre (20080807).

Ever since I completed my system update, I am unable to send emails. Whenever I do, I get an error that says TB can't connect to the SMTP server.

I made a test and copied my profile to the Ubuntu profile directory (i.e. .mozilla-thunderbird instead of .thunderbird), and I was able to send emails correctly. I also noticed that I can no longer read RSS feeds. I have no problem reading mail because I use fetchmail to do the work.

This seems to me like some form of library issue (I am on AMD64). I tried looking at the TB Error console but nothing shows up.

Has anyone ever seen something like this? If so, how did you fix it?

Thanks,

L

---

### Post by lduperval on 2008-08-13
Nobody knows? Dows anyone know how to figure out what the problem is?

If the proble is the 64-bit/32-bit issue, how can I make sure that the needed 32-bit libraries are available on my system?

Barring that, is there a 2.0.0.17pre 64 bit build available somewhere?

Thanks,

L

---

### Post by lduperval on 2008-08-14
I fixed it by doing my own nightly build.

L

---

