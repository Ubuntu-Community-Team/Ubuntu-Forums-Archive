---
title: "Which setting causes KDE to fail?"
date: 2015-01-15
forum: Desktop Environments
---

### Post by musiKk on 2015-01-15
From one day to the next, KDE suddenly stopped working. At first I'd get a black screen after resume. I rebooted, logged in and only got a black screen. After a bit of troubleshooting and not really finding anything I renamed my ~/.kde/ directory in order to have it reset and low and behold, KDE works again.

Now, I'm glad that it isn't anything serious but I'm not really thrilled either. I have changed a lot of settings over time to customize KDE to my needs and now I have to do it again. I'd much rather find out what caused the issue but unfortunately I couldn't find anything in the logs. Is there a way to find out what exactly is the problem so that I can apply a small fix and have everything as it used to be?

I don't recall changing anything in the settings and there have been no software updates in the past days that would warrant such a behavior. From my perspective this happened completely randomly.

Thanks
mK

---

### Post by vinnywright on 2015-01-16
what were some of the things you were doing before this happened ,,,,,like maby running a GUI app (like dolphin) with sudo (bad idea) kdesudo would be the proper way.

do you still have the old ~/.kde ? 
if so check the ownership of the files in it ,,,,thay should all be owned by you:you (user:group) if the files are owned by root:root you have your prob. and can change them back with chown (see man chown) then move/rename ~/.kde[whatever you named it to]back to .kde after renaming/deleting the new one and you will have your setup back .

if the ownership is not the problem you can still start copying/over righting  the .kde folders from your renamed .kde to the new one one at a time and log out and back in untill you find one that starts the prob. again  to narow things down.

VINNY

---

### Post by musiKk on 2015-01-24
Hi vinnywright,

sorry for coming back to you so late. It's just that I don't like to restart my browser unless I have to. But today my session got the hiccups again and I decided to reboot and use this opportunity to copy over my old KDE settings in order to see what causes the troubles (no ownership problems). But the old settings work now. So that's that. Really weird, I wasted at least two or three hours on this problem when it happened to no avail... It's frustrating sometimes...

Thanks for your help, though.

---

### Post by musiKk on 2015-05-22
I just had it happen again and I found out what the problem was. I usually have an external monitor on my laptop but for some reason unplugging it is more of a hit and miss: Sometimes I just get a black screen. This is what happened here and probably in the other case. Deleting .kde/share/apps/kscreen solves the problem. Since I don't really play around with the settings in kscreen but have everything setup automatically this is just a little annoying but not a huge deal. But yeah, still annoying.

---

