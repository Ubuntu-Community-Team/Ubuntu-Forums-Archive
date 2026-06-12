---
title: "Power button shutdown as current logged in user"
date: 2006-06-24
forum: Desktop Environments
---

### Post by rune on 2006-06-24
I usually use my power button to shutdown my computer, but that messes up the session, because then root is the one initiating the shutdown.

I'm looking for a command that acts like pressing the shutdown button in the power option, then I'd pass that one to the power button script like this:

USER=`find user currently using screen`
su $USER -c "gnomeshutdowncommand"

Is this possible?

---

