---
title: "xfce4-screenshooter save file name"
date: 2011-11-24
forum: Desktop Environments
---

### Post by math4tots on 2011-11-24
In Xubuntu, you can take and save a screenshot to a given directory with the following command:

```
xfce4-screenshooter -f -h -s $SAVE_DIRECTORY
```I have two issues:


[LIST=1]
[*]How do I choose the filename? The default file name is weird and has spaces in it. The man pages didn't seem to list any options, though choosing a filename just seems like something you should be able to expect from a screenshooter.
[*]The command simply saves to the default directory if $SAVE_DIRECTORY doesn't exist yet. How could I get it to create the directory if it doesn't exist? (this second question actually isn't as critical because I could just add an if command to create the directory when needed, however, I figure it would be nice if there was a more canonical way to do this i.e. through options/arguments).
[/LIST]

 
Thanks.

---

### Post by wernerml on 2013-03-20
yeah... I'm trying to change the filename too, couse it has ":" character in it... (and it will become an unusable file in Windows...)

---

### Post by oldos2er on 2013-03-20
[COLOR=#000000]If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

Closed.[/COLOR]

---

