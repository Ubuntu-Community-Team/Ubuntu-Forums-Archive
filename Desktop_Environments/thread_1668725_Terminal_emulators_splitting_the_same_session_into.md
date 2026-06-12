---
title: "Terminal emulators splitting the same session into many views?"
date: 2011-01-16
forum: Desktop Environments
---

### Post by BiQ on 2011-01-16
Hi, 

I don't know if this is the right place to ask, and my question is not even very much Ubuntu-specific... but here goes.

I like to think of myself as some kind of Linux "power user", and I do know my way around the command-line and I've been using mostly Ubuntu when it comes to Linux for the last 3 years or so. The idea and practice of building softwares I use from sources is not completely alien to me even if I strongly prefer to just say apt-get install whatever. I'm currently using Terminator by tenshu.net as my terminal emulator due to its ease of use to tile terminals and encoding switching. My question is not specific to Terminator, and I'm willing to change it to another if that's needed to get what I want.

One thing that has bugged me about terminal emulators (and using a command-line interface altogether) lately is that they seem rather poor at utilizing the fact that widescreen is becoming more and more common as far as displays go. I'd really like to be able to view and edit 200 line long source code (.c source, for example) in vim (or any text editor using terminal) while seeing the whole file on screen at once. Since most of the code in question keeps within 80 characters per line, the width of display really goes mostly unutilized. 

Is there (relatively) easy-to-setup terminal emulator which could "tile" chunks of same terminal session/flow into, like, 3 different views so that any programs running in them/it would effectively "see" a terminal window made of >200 lines x 80 characters per line, all the while letting me view those chunks next to each other on my display? And how to actually make it happen in that terminal emulator? While I like to consider myself a "power user" of sorts, I'm also a bit lazy and would really appreciate if someone who has already waded through those man pages and hit into a solution for this question would share his/her knowledge in this matter. Even if it amounts to "nope, none of that is done in anywhere", since at least then I wouldn't have to search for something that's doesn't even exist. Also, if GNU screen can do this, those tips are appreciated too.

Oh, support for both UTF-8 and ISO-8859-1 is essential, too. Not that I believe there to be any currently developed terminal emulators failing that one, just to be sure...

Oh, and the views should "react" to each other, yes. in other words, stuff that flows out upwards from the "logically downmost" view should appear and flow into the "logically middle" view.

...I hope someone can actually understand what I'm aiming at here...

---

