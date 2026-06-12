---
title: "Another person with gaming problems."
date: 2007-08-18
forum: Gaming &amp; Leisure
---

### Post by Zimbaly on 2007-08-18
Ok I've used the search function. I've found some threads for my problems, but I'm having trouble executing some of them.

I must first say thank god for the installers and work some of you people do on here. I was having problems installing my nvidia stuff and found something great to do it on here for me. Mucho respect for that. 

But sometimes some of these things don't work. Take Unreal Tournament Anthology installation for example. There's a post on here with a script allowing for easy installation.

[http://ubuntuforums.org/showthread.php?t=394706](http://ubuntuforums.org/showthread.php?t=394706)

So I grab it, but I can't install/execute it. I've looked on the forums for the basic commands for stuff, but it always says 'Can't open ./utinst.sh' I know it's probably something I'm doing so I wanted to ask what am I doing wrong or did I forget to do something before hand.

I have it on my desktop. is there a suggested place for putting files I want to install or run?

Getting this to run under this instead of wine would be better. It would solve the mouse problems I have for it. I can't seem to figure that one out either.

Also my last issue is with Wolfenstein ET. When I try to run it I always get Can't open ./et-linux-2.60.x86.run

I don't know what I'm doing wrong.

And other then these few things I have been enjoying my experience of Ubuntu so far. Nice and easy to install ; )

---

### Post by GFree678 on 2007-08-18
This one's easy... provided you know what to do first, otherwise it drives you up the wall until you learn. :)

Run the following commands in the folder which has the file

chmod +x utinst.sh
./utinst.sh

The chmod tells linux the file is an executable, so it can run now. The same thing is used to fix your Wolf Et problem:

chmod +x et-linux-2.60.x86.run
./et-linux-2.60.x86.run

---

### Post by Zimbaly on 2007-08-18
Thank you so much = )

I'm gonna be doing that right now..... must.... game ; P

---

### Post by Zimbaly on 2007-08-20
Ok I got wolfenstein working and it was running so great..... then this morning I go to play it and it's lagging like mad. Getting that edge tearing effect with the graphics and bad fps now, and also diablo 2 loads up to a black screen in wine.... meh.

I've been looking on the forums... hope I find something = P

---

