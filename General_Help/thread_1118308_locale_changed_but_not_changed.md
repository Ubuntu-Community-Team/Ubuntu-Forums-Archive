---
title: "locale changed but not changed?"
date: 2009-04-06
forum: General Help
---

### Post by Mephator on 2009-04-06
I recently did an install of 8.10-server and, without thinking, chose the Canadian location/locale (I live in Canada, it was a knee-jerk reaction). A little while later I noticed I was getting strange characters when I tried to compile programs. Some research informed me that it's probably a locale-related program, so I installed localeconf and got rid of all the locales except for en-US.UTF8. I restarted the server and again attempted to compile the program and again got the extra characters. I've gone so far as to remove and then reinstall the gcc packages and a few others, but nothing helps.

What can I do to get rid of these extra characters? The only thing I can think of that would be a problem would be PuTTY not playing well, but it's never given me a problem before.

---

