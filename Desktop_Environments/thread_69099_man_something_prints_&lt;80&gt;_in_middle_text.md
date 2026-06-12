---
title: "man something prints &lt;80&gt; in middle text"
date: 2005-09-25
forum: Desktop Environments
---

### Post by jedrik on 2005-09-25
I'm getting extra characters when running the man command. For example
doing: 

  $ man ssh

I get in the middle of the text:
   Second, if .rhosts or .shosts exists in the user<80><99>s home dir ...

When I should get:
   Second, if .rhosts or .shosts exists in the user's home dir ...

It looks to me that the problem is with single quotes and dashes that are
generated when hyphenating a word.

It happens when using an xterm or a gnome-terminal.

I have done:

   $ man ssh > ssh.out

and looked at ssh.out.  There are no extra characters in "user's home dir"

My only guess is that I'm missing a font but I'm not sure what it might be.

Any ideas?

---

