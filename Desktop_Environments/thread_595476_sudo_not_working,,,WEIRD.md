---
title: "sudo not working,,,WEIRD"
date: 2007-10-28
forum: Desktop Environments
---

### Post by neighborlee on 2007-10-28
hi peeps..


    I am doing this:

neighborlee@Heartseed:~$ sudo -l
Sorry, user neighborlee may not run sudo on Heartseed.

wth ? ;)

thx anyone for a fix and a possible explanation of what I may have done wrong..a brand new install btw of buntu gutsy.

cheers
g.leej

---

### Post by legonum on 2007-10-28
I tried to use your link to heartseed.org and got the Vdeck error page instead, telling me to try again tomorrow, and then send an email to support if the page was still off-line. It appears your not the only one who can't access it. Tried to reach the website from a computer using a windows operating system.

---

### Post by neighborlee on 2007-10-28
> **legonum said:**
> I tried to use your link to heartseed.org and got the Vdeck error page instead, telling me to try again tomorrow, and then send an email to support if the page was still off-line. It appears your not the only one who can't access it. Tried to reach the website from a computer using a windows operating system.

Sudo is related to my local machine, not heartseed ;)

My local machine ;)

sudo for some odd reason , out of a fresh install is borked.

cheers
g.leej

---

### Post by PurposeOfReason on 2007-10-28
Please post your /etc/sudoers file.

My default one looks like:

```

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Defaults

Defaults	!lecture,tty_tickets,!fqdn

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
```

---

### Post by neighborlee on 2007-10-28
> **PurposeOfReason said:**
> Please post your /etc/sudoers file.

My default one looks like:

```

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Defaults

Defaults	!lecture,tty_tickets,!fqdn

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
```

OK I got it..I have NO idea how it happened as I"ve installed ubuntu before :)..but somehow there were two usres instead of just me..there was neighborlee and neighbor

I have no idea why..I never go by just neighbor per se so I have no idea what happened..

anyway I gave neighborlee admin privileges and then deleted neighbor and all is well

cheers
g.leej

---

### Post by legonum on 2007-10-30
I understood the problem you were having was with Sudo on your local machine, I simply said I couldn't access the heartseed.org website from your link, even with a machine that uses windows as it's OS.

uhh, if I dare venture another potentially irrelevant comment, that neighbor/neighborlee  disparity reminds me of the kinds of problems that can result from a sticky "enter" key, sometimes it enters before you finish typing since it's still partly depressed from last time, or a little un-intended finger bounce can cause that when the enter key is very senstitive. How could that make a whole new ( and unwanted) user account? I dunno....all this Ubuntu stuff is new to me. 

Is Sudo working correctly now? 
Ahhh! yes, I see from your most recent post that it is!  yeah!! congratulations, I'm glad to see your problem is solved.

---

