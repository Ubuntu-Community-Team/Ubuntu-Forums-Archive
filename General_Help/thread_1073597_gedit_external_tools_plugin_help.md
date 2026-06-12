---
title: "gedit external tools plugin help"
date: 2009-02-18
forum: General Help
---

### Post by ManoloM on 2009-02-18
Hi there,

I can't seem to get the "open terminal here" external tool plugin to work
properly. Whenever I try to use it, the shell output window displays:

Running tool: Open terminal here

Done.
Invalid argument: "functions"

But then nothing happens! What does "Invalid argument: "functions"..." mean?

The actual script file currently is:

#!/bin/sh

#TODO: use "gconftool-2 -g /desktop/gnome/applications/terminal/exec"
gnome-terminal --working-directory=$GEDIT_CURRENT_DOCUMENT_DIR&

I have the suspicion that the variable $GEDIT_CURRENT_DOCUMENT_DIR isn't working properly, how can I fix this?

I am using gedit 2.20.3 on ubuntu 7.10 (gutsy)

Any help would be appreciated. Thanks

Manuel

---

### Post by fragos on 2009-02-18
Type <Ctrl>F9 and select the terminal tab and you'll have what you want.

---

