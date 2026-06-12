---
title: "SSH terminal option : &quot;Follow terminal folder&quot;"
date: 2015-10-26
forum: Desktop Environments
---

### Post by wink2 on 2015-10-26
I manage servers via SSH, but I am missing a function I had in a software called MobaXterm :

[IMG]http://mobaxterm.mobatek.net/img/moba/features/feature-sftp-browser.png[/IMG]

The "Follow terminal folder" keep an eye on the current SSH directory, then allow me to edit them with a desktop application (like Sublime).
That's very handy, so I don't need to use ls -lha all the time and can use my favorite text editor instead of vim. 

Any idea how I can have the same behavior on the Ubuntu desktop ?

Thanks

---

### Post by TheFu on 2015-10-26
Sorry - you lost me completely with that description.

You can use vim to remotely edit files over ssh.
[http://blogs.perl.org/users/smylers/2011/08/ssh-productivity-tips.html](http://blogs.perl.org/users/smylers/2011/08/ssh-productivity-tips.html)

Have you checked "alternativeto.net"? Anything there?

I'm pretty good at ssh, but prefer plain xterms for terminals. 
If I want to watch files in a directory, I use the 'watch' command.  Unix has a solution to most needs, if you think in the Unix way. "kitchen-sink" applications are NOT the Unix way.

OTOH, I probably don't understand what you really want.

Looked up that tool - any of the top 5 file browsers include an sftp client. I think that is what you want with "follow folder" - thunar, nautilus, pcmanfm, .... are some of the choices. Just put ssh://  or sftp:// into the URL field.

Don't forget about sshfs.

---

### Post by wink2 on 2015-10-27
Thanks TheFu, sorry my explanation wasn't clear. I expected the screenshot to be straight forward.

I know there are tons of ways to use sftp, all of them involve either running extra commands or using an extra program.

What the "Follow terminal folder" checkbox is doing on mobaXterm, is opening a panel on the left side to automatically "ls" all the folders you "cd" into. (can't make it clearer)
This is just to be more productive, once you are used to it, typing "ls" 500 time a day sound irrelevant.

---

### Post by TheFu on 2015-10-27
Ah. I think I get it.
I just use different buffers in vim for that stuff. Highly efficient. No mouse needed. I program from a "project perspective", not a "directory perspective."
Don't really type 'ls' much when programming.  Generally have 4+ terminals open, with focus set to follow the mouse, so a quick bump puts me into the other xterm, last cmd, <enter>, bump back, code some more ... no clicking needed.  Guess we just work differently.

---

### Post by tgalati4 on 2015-10-27
Midnight Commander (mc) is what was used back in the day.  Try installing it on your server and fire it up.

---

