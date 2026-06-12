---
title: "Clarity, please: .bashrc and other bash startup scripts"
date: 2010-12-15
forum: Desktop Environments
---

### Post by rpaskudniak on 2010-12-15
Greetings again.

This is not really a major problem, just a quibble over something I have observed and wish to share my $0.02 (US) with y'all.

I see that there is a .bashrc in my home directory and I have established it is being executed.  This is fine though I was  initially confused by the man page for bash:
> When bash is invoked as an interactive login shell, or as a non-interactive shell with the --login option, it first reads and executes commands from the file  /etc/profile,  if  that  file  exists.   After  reading  that  file,  it  looks  for ~/.bash_profile, ~/.bash_login,  and  ~/.profile, in that order, and reads and executes commands from the **_first one that exists_** and is readable.
Note: No mention of .bashrc.  The emphasis (underline) is my editorializing.

I would chalk this up to a bug in the documentation.  My assumption is that .bashrc should be listed first in the above list.  As I write this I am downloading a bunch of updates, including documentation on bash.  Until that download completes I will not know if this has been fixed.  I'll post an update if something changes.

Your opinions?

---

### Post by gmargo on 2010-12-15
Presumably you do not have a ~/.bash_profile or a ~/.bash_login file; most people don't.

However, you most likely have a ~/.profile file.  The default ~/.profile contains a clause that executes the ~/.bashrc file.  That's how it is running upon login.  It's not a doc bug.

---

### Post by nothingspecial on 2010-12-15
There are a few references to .bashrc in man bash.

To search man pages...

press /

then enter a search string (eg .bashrc)

Press n to go to the next one, or N (Shift + N) to go to the previous.

note: this is a feature of less that opens man pages by default.

---

