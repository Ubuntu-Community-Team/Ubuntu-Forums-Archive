---
title: "If I change the video card will my installation(X, Gnome, etc.) break?"
date: 2006-01-03
forum: Desktop Environments
---

### Post by rozojc on 2006-01-03
I had a question: My parent's computer has Ubuntu and I'm thinking about changing the video card. If I do that will Ubuntu recognize the change and auto-configure it appropriately, or will I maybe (hope not) change it, boot the computer, and find out that X won't start or something?

Is it safe? I mean, can I just take it off, put a new one and everything will work?

---

### Post by Zimmer on 2006-01-03
[QUOTE=rozojc]I had a question: My parent's computer has Ubuntu and I'm thinking about changing the video card. If I do that will Ubuntu recognize the change and auto-configure it appropriately, or will I maybe (hope not) change it, boot the computer, and find out that X won't start or something?

Is it safe? I mean, can I just take it off, put a new one and everything will work?[/QUOTE]

Quick reply to get you searching....No...
Not if it is a different model card to the one you are replacing...
You will need to (at least ) reconfigure xorg.conf...and (at worst) install drivers for the new card and change the config.
Have a look in the wiki for installing cards, and on the forum...
I believe I have read that one reasonable method is to install and configure the necessary drivers and config BEFORE you  change the card in the machine. Then on bootup you have a fighting chance of it working straight away. But don't take my word for it. When I last did this it was during a clean install of Ubuntu and I re installed the whole shebang just so it would recognise the card...I don't think you have that option...I will have a trawl around and see what other info I can find...
have a look at 
[https://wiki.ubuntu.com/CommonProblemsGraphics?highlight=%28install%29%7C%28graphics%29](https://wiki.ubuntu.com/CommonProblemsGraphics?highlight=%28install%29%7C%28graphics%29)

---

