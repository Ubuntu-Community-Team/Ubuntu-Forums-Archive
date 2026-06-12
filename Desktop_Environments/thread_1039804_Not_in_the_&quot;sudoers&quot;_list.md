---
title: "Not in the &quot;sudoers&quot; list?"
date: 2009-01-14
forum: Desktop Environments
---

### Post by Fireblazer on 2009-01-14
Hey,

I just noticed that when I watched a YouTube (or any other flash app) video, the sound comes out of my little keyboard receiver / speakerphone. I wanted it to come out of my huge speakers but that's beside the point.
My problem is that when I went to install a package using "sudo apt-get install..." it said something along the lines of "(username) is not in the sudoers list.   This incident will be reported.". I recently istalled a Dovecot/Postfix mail server and created the user "admin", could this have hi-jacked the admin group ans caused this? If so, can I still keep the user admin (in another group of course)? Right now I fixed my problem by running "visudo" and adding "(username) = ALL(ALL) ALL". I just want to know if this is safe and what else I might need to do.

The Point: I removed my self form something (group, file, etc.) and added "(username) = ALL(ALL) ALL" to my "sudoers" file, is this safe?

~ Fireblazer

PS: Who came up with "sudoers", I love that word!

---

### Post by utnubuuser on 2009-01-15
Check your permissions in Administration>>Users and Groups>>user>>user priviledges.??

---

### Post by adamlau on 2009-01-15
I prefer adding users to the admin group if they require escalated privileges, including myself. Assuming you are logged into your account, what is the output of:

```
groups
```

...and..

```
groups admin
```

---

