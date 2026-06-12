---
title: "I broke my KDE 4.0 with Window Effects"
date: 2008-02-08
forum: Desktop Effects &amp; Customization
---

### Post by Bosonator on 2008-02-08
Can anyone tell me how to revert my KDE 4.0 Window Manager (KWIN, is it?) configuration to the default settings? I recently installed KDE 4.0, and when playing around with the (snazzy!) new window effects, I enabled one of them (I think it was "invert desktop colours") that causes the content of my windows to get shifted upwards. Because the window content is so distorted, I am unable to do anything on the desktop, and will have to make any fixes using the command line.

Thanks for the help!

---

### Post by PurposeOfReason on 2008-02-08
All I can think of will revert all of KDE back to default.

sudo rm ~/.kde

And because of that thread about commands, that will just delete your .kde folder (which holds your settings) and will be remade (default) next time you log into kde.

---

### Post by Bosonator on 2008-02-09
Thanks for the tip. I have KDE 3 Desktop still installed, and I'm worried the command you suggest will delete the configuration settings for that too. Is there anything I can do to specifically reset the defaults on *only* the window effects?

---

