---
title: "'Insufficient privileges' message box on boot"
date: 2005-05-15
forum: Desktop Environments
---

### Post by chopeen on 2005-05-15
I installed Firestarter about a month ago. I followed this <http://www.fs-security.com/docs/faq.php#trayicon> advice to start its GUI when I log on to the system. And everything was working fine until today.

Now when I log on, a message box 'You must have root user privileges to use Firestarter'. But Firestarter's GUI loads anyway (there's an icon in the tray), even if I don't click OK.

My guess is that 'sudo firestarter --start-hidden' line defined in System / Preferences / Sessions works fine, but there is something else that tries to load FS. To make sure, I removed this line - as a result, FS does not start, but there is still this annoying message box.

Any ideas how to get rid of it?

---

### Post by chopeen on 2005-06-05
I've just worked it out!

It was so simple and it took me so much time, that I simply cannot believe it.

I had used the 'Save current setup' option when shutting down my machine. The Firestarter had been running and its state had been saved too.

Then every time when the system was starting it tried to load it.

---

