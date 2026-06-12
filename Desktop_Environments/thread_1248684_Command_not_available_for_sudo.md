---
title: "Command not available for sudo"
date: 2009-08-24
forum: Desktop Environments
---

### Post by abelta on 2009-08-24
I'm using some of Ruby Gems that I need to run straight from the command line like this (example with starling):

[FONT="Courier New"]$ starling[/FONT]

Even though I had that particular gem installed, bash didn't recognize it and I got a message like this:

[FONT="Courier New"]bash: starling: command not found[/FONT]

I found out that I needed to append some data to the environment variable PATH (or something like that, excuse my noobism), so I gedited ~/.basrc and added this lines:

[FONT="Courier New"]# For Ruby Gems
export PATH=$PATH:/var/lib/gems/1.8/bin[/FONT]

including the path where the gems are stored.

Now bash does recognize the names of my gems as commands, but it seems like I need to run some of then with sudo and when I do, I get the same error again:

[FONT="Courier New"]sudo: starling: command not found[/FONT]

the command is recognized by my user, but then I switch to a different user and, consequently to a different environment (my guess) the PATH isn't recognized anymore.

Any ideas how I can add that path for the root user?

Thanks.

---

### Post by andrewc6l on 2009-08-25
There appear to be three places where you might make the change. Two are global: /etc/login.defs or /etc/profile. The first will require that you log out and back in to get the new environment variable; /etc/profile will set up your environment only for ash/bash/dash-like shells (not csh).

Alternately, you might be able to put it in /root/.profile - which would enable it for root using ash/bash/dash but not for everyone. 

Be aware that by adding things to your path, you're opening up possible areas for attack on your system. By default, root has very little on the path so it doesn't accidentally run a program that can open more security holes. In particular, you'll want to make sure that /var/lib/gems/1.8/bin is writable only by root.

---

### Post by abelta on 2009-08-25
Thanks for the reply. I had already tried some of those config files without success.
It seems I'm not the only one having this same problem, so I googled (yet) some more and found a workaround creating an alias for sudo like this:

[FONT="Courier New"]alias sudo='sudo env PATH=$PATH'[/FONT]

BTW, /var/lib/gems is only writable for root anyway, but thanks for the security tip.

---

