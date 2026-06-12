---
title: "What are hwclockfirst.sh and hwclock.sh init scripts for ?"
date: 2006-01-15
forum: Desktop Environments
---

### Post by lanjelot on 2006-01-15
Hi all,

i was just wondering why there are those two init scripts hwclockfirst.sh and hwclock.sh that are very similar... They only differ from one line: one set the variable FIRST to "yes" and the latter to "no".

Does anyone know the particular purpose of each file ?

---

### Post by lanjelot on 2006-01-17
no one ? :)

---

### Post by qferret on 2006-01-17
NO idea why..... but from what I read, it appears that hwclockfirst.sh is ran at boot and calls hwclock.sh at the end....

You say they are the same except the one line?
(Sorry, I'm at work & using XP ATM....(yucky))

---

### Post by lanjelot on 2006-01-19
yeah hwclockfirst.sh is a copy of hwclock.sh exept that at line 19:
 - hwclockfirst.sh: FIRST="yes"
 - hwclock.sh: FIRST="no"

here's the important part:

if [ "$HWCLOCKACCESS" != no ]; then
  log_begin_msg "Setting the system clock..."

  /sbin/hwclock --hctosys $GMT $HWCLOCPARS $BADYEAR

  if [ "$FIRST" = yes ]; then

    if [ -z "$TZ" ]; then
      /sbin/hwclock --noadjfile --hctosys $GMT $HWCLOCKPARS $BADYEAR
    else
      TZ="$TZ" /sbin/hwclock --noadjfile --hctosys $GMT $HWCLOCKPARS $BADYEAR
  fi
fi

Since --noadjfile is documented as "hwclock will not read nor write to the file /etc/adjtime", i assume that /sbin/hwclock --hctosys will make use of /etc/adjtime although i don't see what for.

So when booting, hwclockfirst.sh sets the system time from the hardware clock twice by reading /etc/adjtime the first time and without using it the second time, and then hwclock.sh sets the system time again by reading /etc/adjtime.

What's the point of running it twice, i don't get it.

Damn i am completely lost on that one.

How do you understand it ?

---

