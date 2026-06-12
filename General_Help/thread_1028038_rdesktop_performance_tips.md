---
title: "rdesktop performance tips"
date: 2009-01-02
forum: General Help
---

### Post by DocForbin on 2009-01-02
This may be common knowledge, but I had never ran rdesktop from the command line and just discovered some key options aren't even available in the gui. If performance is an issue for you using rdesktop, I highly recommend using -x m to disable theming and -z to enable compression.

I also use -m to disable motion events, -r sound:off to diable sound, and -P to enable caching (all available in the gui). All of these combined give way better performance than the default options.

Here's the command I use now:

rdesktop -u username -f -m -z -x m -P -r sound:off -0 myip

---

### Post by NewbieLearnLinux on 2010-10-14
> **DocForbin said:**
> This may be common knowledge, but I had never ran rdesktop from the command line and just discovered some key options aren't even available in the gui. If performance is an issue for you using rdesktop, I highly recommend using -x m to disable theming and -z to enable compression.

I also use -m to disable motion events, -r sound:off to diable sound, and -P to enable caching (all available in the gui). All of these combined give way better performance than the default options.

Here's the command I use now:

rdesktop -u username -f -m -z -x m -P -r sound:off -0 myip
Thanks,
It improves the performance significantly. 

How about -b and -a8 ?

---

### Post by dcstar on 2010-10-14
> **DocForbin said:**
> This may be common knowledge, but I had never ran rdesktop from the command line and just discovered some key options aren't even available in the gui.
.........


Then use the **tsclient** GUI front end that has many other options easily available without mucking around with the command line.

---

