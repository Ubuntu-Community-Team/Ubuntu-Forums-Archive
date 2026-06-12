---
title: "Installing Nautilus extensions / plugins"
date: 2009-12-02
forum: Desktop Environments
---

### Post by play_ on 2009-12-02
I would like to begin writing an extension for nautilus. (one that shows up on the right-click menu, to be specific)

The problem I am having is that whenever I add an already existing module (such as 'open-terminal'), i have to restart Nautilus to see the new menu item.

This is quite annoying since every change i'll make, i'll have to restart nautilus to see the change. 

And although /usr/share/doc/python-nautilus/examples says:

> 
To try any of the examples, copy them over to:

    @NAUTILUS_EXTENSION_DIR@/python/
or:
    ~/.nautilus/python-extensions/

Then restart nautilus.

Hint: if you're testing an extension that you're developing, it may
be useful to start a 'private' instance of nautilus, like this:
  $ mkdir /tmp/testing
  $ export TMPDIR=/tmp/testing
  $ nautilus --no-desktop

I followed the hint instructions and then placed open-terminal.py on both directories suggested above, and still did not see a change until i restarted nautilus.

any input would be appreciated and great help :)

thanks.

---

### Post by alienclone on 2009-12-03
the hint instructions do not say that you still wont have to restart nautilus

---

### Post by play_ on 2009-12-04
> **alienclone said:**
> the hint instructions do not say that you still wont have to restart nautilus

You're right.

I figured it out.

Searching google on how to restart Nautilus, many suggested $ killall nautilus.

Which i did, but wouldn't start when i did $ nautilus

So, what i do is:
$ nautilus -q

press ALT + f2 and type 'nautilus' to start it again. Typing $ nautilus in terminal would not start it again for me.

Hope this helps someone in th future :)

---

