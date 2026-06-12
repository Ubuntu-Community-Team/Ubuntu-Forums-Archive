---
title: "bash completion with aliases?"
date: 2009-04-21
forum: General Help
---

### Post by KhaaL on 2009-04-21
I have a few aliases that i use to get my most used apt-centric commands shorted. For example, i have this alias:

alias aptin='sudo apt-get install'

which works great. but I don't get the ability to use autocompletion with *aptin* like i would have otherwise with *sudo apt-get install*. is this a sacrifice that has to be made when you're using aliases, or is there a workaround?

---

### Post by Slim Odds on 2009-04-21
you can define your own completions

take a look at /etc/bash_completion for some examples.

You might have a look at this: [http://www.debian-administration.org/articles/316](http://www.debian-administration.org/articles/316)

---

### Post by sdennie on 2009-04-21
It's possible to do but it's not straightforward.  This looks like a good guide but, I haven't tried it: [http://ubuntuforums.org/showthread.php?t=733397](http://ubuntuforums.org/showthread.php?t=733397)

---

### Post by KhaaL on 2009-04-23
Yeah, this was a bit too technical for me... I'll have to bookmark it and look at it at a later point. Thanks!

---

