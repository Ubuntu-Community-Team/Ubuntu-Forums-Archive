---
title: "ubuntu update manager problem (and solution!)"
date: 2005-02-23
forum: Desktop Environments
---

### Post by SurreaL on 2005-02-23
Hello everyone!

I just spent a little bit of time wrestling with a weird problem.. and since I found the answer I thought I might post it in case others have the same issue I did :) (I searched and didn't find any reference to it previously..) I'm new to Ubuntu and although I've gone through some minor growing pains since installing it on my laptop and work desktop.. (ie sound on my laptop don't work :/ but that's another thread..) I like it so far :D

Anyhow my problem was with the Ubuntu Update Manager. That little applet that sits in the system tray and waits to tell you about new updates to download.. for some reason it wouldn't open. I wasn't sure why, and the issue seemed to spread to synaptic! (Although I could open it from a console where I had su'd.. just not as my current user!) 

Turns out the problem was with .gksu.lock, a file located in my home directory. As soon as I deleted it, I was able to launch the update program again and everything was working perfectly :) I guess it had been created after I had attempted to launch the update program, and it froze asking for my password.. after re-starting X everything else was fine except for that one glitch!

Anyhow off to post about my sound probs, hopefully this helps someone down the line :)

---

### Post by flibble on 2005-02-23
Thanks for posting this. I just had the same thing happen and you saved me from having to muck about just before some uni work was due. groovy!  :-P

---

### Post by kweinert on 2008-04-29
Here's another possibility - for security reasons I have my /tmp filesystem mounted noexec - the updates happened just fine, but the upgrade (to 8.04 LTS) would mysteriously (and silently) fail right after downloading the "file 2 of 2".

It wasn't until I ran it from the command line and I could see what it was doing that I realized what was happening.

Should this be filed as a bug?

---

