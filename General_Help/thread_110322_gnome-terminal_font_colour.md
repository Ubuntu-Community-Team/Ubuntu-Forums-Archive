---
title: "gnome-terminal font colour"
date: 2005-12-30
forum: General Help
---

### Post by cbudden on 2005-12-30
Help!

The different colour of text for directories etc, has gone from my terminal.  How do I get it back?
[IMG]http://static.flickr.com/38/79464825_7de1c3197a_o.png[/IMG]

---

### Post by jlintz on 2005-12-30
add this to your .bashrc

# enable color support of ls and also add handy aliases
if [ "$TERM" != "dumb" ]; then
    eval "`dircolors -b`"
    alias ls='ls --color=auto'
fi

---

### Post by cbudden on 2005-12-30
Thanks.  It seems I didn't have a .bashrc file, so I copied one from another user which fixed the problem.  Thanks.

---

