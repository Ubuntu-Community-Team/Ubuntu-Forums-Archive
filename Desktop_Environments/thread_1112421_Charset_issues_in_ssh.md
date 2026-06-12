---
title: "Charset issues in ssh"
date: 2009-03-31
forum: Desktop Environments
---

### Post by ep1p on 2009-03-31
Hi,
I'm running kubuntu 8.04. Ever since I've had it installed (prolly around 9months now) I've had issues in ssh when trying to type the pound character £ (that's a pound character as in UK currency (£) rather than a hash (#)) incase it doesnt show up right.

Every time I type it it seems to come up with a pound and a space like this: "£ ". On the console, it doesn't display the space, however if you backspace the pound symbols, it removes characters as if the space was there and thus you lose half your prompt or whatever else was on the line.

I've looked long and hard and cannot find anything on how to fix this. I've tried configuring my charset to both UTF8 and ISO-8859-1 and I get issues either way (dpkg-reconfigure console-setup). I'm guessing I should be using UTF8 ideally to ensure best compatibility..

meeb ~ # set | grep LANG
LANG=en_GB.UTF-8
LANGUAGE=en_GB:en

Things display fine if I type £ locally, however I suspect it's being interpreted differently here to on the remote machines. It also seems to happen with lots of remote distros (Gentoo, Debian, Ubuntu).

I'm using an apple keyboard on a Dell computer if that matters although I've tried with the dell one as well and it doesn't seem to make any difference.

It's getting to the point where I have to revert to using my Windows laptop sometimes to actually do stuff so I don't get weird character set issues!

Suggestions on what to set things to welcome.

Cheers,

john

---

