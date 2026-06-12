---
title: "Firefox 1.0.7 Too Slow Please help Config."
date: 2005-12-26
forum: Desktop Environments
---

### Post by braveerudite on 2005-12-26
I'm using the latest Ubuntu.  My web browsing is totally slow.  I have cable modem going @ 512.  When I browse the internet with Firefox on windows it works fast (normal) but when I'm using Firefox on Ubuntu (Linux) goes really slow. (Like 56k slow) Are there any configuration or tips in how to get Firefox 1.0.7 working faster on my Linux System.  Thank you for your time.

---

### Post by rfruth on 2005-12-26
Something is wrong, Fx (1.0.7) is as fast now as it was on my Win XP machine, ya have lots (any) extensions & or themes, cleared the history file, tried a different profile, safe mode okay  :confused:

---

### Post by briancurtin on 2005-12-26
compile firefox from source. the ubuntu versions of firefox in the repositories tend to be slower for some reason.

if you want to stay on 1.0.7, then compile that, or if you are interested in upgrading to a newer version of firefox, you can check out the HOWTO right here:[http://www.ubuntuforums.org/showthread.php?t=79283](http://www.ubuntuforums.org/showthread.php?t=79283)

---

### Post by PapaWiskas on 2005-12-26
[QUOTE=briancurtin]compile firefox from source. the ubuntu versions of firefox in the repositories tend to be slower for some reason.

if you want to stay on 1.0.7, then compile that, or if you are interested in upgrading to a newer version of firefox, you can check out the HOWTO right here:[http://www.ubuntuforums.org/showthread.php?t=79283](http://www.ubuntuforums.org/showthread.php?t=79283)[/QUOTE]

I recommend doing this....worked great....and I am a newbie to Ubuntu....
Firefox works great.....

---

### Post by braveerudite on 2005-12-26
[QUOTE=briancurtin]compile firefox from source. the ubuntu versions of firefox in the repositories tend to be slower for some reason.

if you want to stay on 1.0.7, then compile that, or if you are interested in upgrading to a newer version of firefox, you can check out the HOWTO right here:[http://www.ubuntuforums.org/showthread.php?t=79283](http://www.ubuntuforums.org/showthread.php?t=79283)[/QUOTE]

What do you mean with "compile firefox from source" Sorry, I don't understand those  terms yet.

---

### Post by PapaWiskas on 2005-12-26
[http://ubuntuforums.org/showthread.php?t=99004&highlight=arnieboys+script](http://ubuntuforums.org/showthread.php?t=99004&highlight=arnieboys+script)

Is actually the link that I read and used...sorry for the confusion.  1.5 works for me really well.

---

### Post by mcduck on 2005-12-27
Before you compile anything, open firefox, type 'about:config' in the address bar and find a line with 'network.dns.disable.IPv6' and change the value to 'true'. restart FF and it might work a lot faster now.

If that's not enough, get the Fasterfox extension.

---

