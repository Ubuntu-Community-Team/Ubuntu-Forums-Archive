---
title: "Axiom session hangs in Texmacs?"
date: 2006-07-19
forum: Desktop Environments
---

### Post by xhantt on 2006-07-19
If I try to use Axiom within Texmacs, with init session then Axiom hang up.

But I can use Axiom on the command line, and Texmacs inserting Maxima within a session.

This doesn't happen in previous version. I wonder if this just happen to me?

---

### Post by Martin Aulbach on 2007-04-12
These problems probably arise because the standard shell has been changed from bash to dash in Edgy Eft.

The directory /usr/lib/texmacs/TeXmacs/bin contains the startup scripts that TeXmacs is using. They start with the line

#!/bin/sh

You have to change this line into #!/bin/bash to make the detection of Axiom work correctly. I think, in your case it will suffice to make this change to the file tm_axiom.

You can find more information about this and related problems at:
[http://savannah.gnu.org/bugs/?18519](http://savannah.gnu.org/bugs/?18519)
[http://ubuntuforums.org/showthread.php?t=278170&page=2&highlight=texmacs+maxima](http://ubuntuforums.org/showthread.php?t=278170&page=2&highlight=texmacs+maxima)

---

