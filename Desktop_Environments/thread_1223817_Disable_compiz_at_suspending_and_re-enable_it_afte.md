---
title: "Disable compiz at suspending and re-enable it afterwards - scrip help"
date: 2009-07-26
forum: Desktop Environments
---

### Post by meijer.o on 2009-07-26
Dear linux user.

When I enable compiz, X crashes when resuming from suspend. I want to make a script that kills compiz before suspending en re-enables after resuming. The script has to be placed in /etc/pm/sleep.d and the format has to be:
------------------------------------------------------------------------
#!/bin/sh

# Action script to enable/disable compiz in reaction to
# pm-action

case "${1}" in
        suspend|hibernate)       

# metacity --replace
# here script that kills compiz

               ;;
        resume|thaw)

# compiz --replace
# here script that restores compiz
            
               ;;
esac

-------------------------------------------------------------------------

Who can help me?

Kind regards,

Otto

---

### Post by meijer.o on 2009-07-27
Bump

Is there nobody out there to help me?

---

