---
title: "Firefly DAAP Server"
date: 2009-03-30
forum: General Help
---

### Post by arrrghhh on 2009-03-30
There needs to be a good write-up for this project.  I couldn't find one.  Perhaps there's an issue I need to iron out with my setup, but I can never get the webUI to work.  The cxn is always refused, and mt-daap never spits out any errors, even when I run it from the terminal.  I've opened port 3689, tried forwarding that port to a localmachine, nothing works!  I will go over my logs to see if I'm missing something when I get home tonight, but if someone has installed this and wants to do a how-to it would be much appreciated!  This project looks very promising, and I need _something_ to replace myth as a music player!  Thanks!

BTW - I installed mt-daap from the repo's.  Probably an old version.  I may try to compile the latest and see if that makes a difference.



Well I guess I should make a how-to on this, although what I did to fix it hardly seems like a fix.  Instead of pointing to a valid music folder on initial run, I pointed mt-daapd.conf to a folder with no (or hardly any) music in it.  I think it came up with one mp3 and a bunch of nothing essentially. At any rate, after letting it troll that bad folder I was able to get to the webUI and configure it correctly.  I hit the "Start Full Scan" button and 20 minutes later it had a 33,000+ song database built.  Impressive!  It's a little slow to access via Rhythmbox, I'll try a different client perhaps... at any rate, I don't know why it wouldn't load my music when I configured it by hand (syslog had an error that said it couldn't load xxx.m4a and the daemon simply halted!  I don't see any reason...) but when I configured it via the webUI it trolled thru my music collection with ease.  I don't think this is how-to worthy, especially since I'm not even compiling the most recent version, as that did not work out well haha!

---

