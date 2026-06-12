---
title: "Last line entered in terminal keystrokes are?"
date: 2009-01-02
forum: General Help
---

### Post by jrounds on 2009-01-02
Hi total newb here,  I am desperate to learn what the keystrokes are to repeat the last line entered into the terminal without entering them.  In other systems this might be ctrl + uparrow.  But that just gets me a capital A.

Thank you!

---

### Post by afbase on 2009-01-02
try just hitting up arrow in command line.

---

### Post by jrounds on 2009-01-02
Ha! Thanks.  Can you believe I been wrestling with Ubuntu for 24 hours and cursing capital As the whole time -=)   And it was uparrow.

---

### Post by sdennie on 2009-01-02
Other useful things are !! (repeat last command) and !$ (last argument of last command).  Example:

```

more /var/log/syslog
!!
tail !$

```

That translates to:

```

more /var/log/syslog
more /var/log/syslog
tail /var/log/syslog

```

---

