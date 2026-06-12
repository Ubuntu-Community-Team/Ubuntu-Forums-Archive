---
title: "[SOLVED] is there a way to stop blacklisted module ipv6 syslog messages?"
date: 2008-12-20
forum: General Help
---

### Post by cb34 on 2008-12-20
i have purposely disabled ipv6 on my system.

now i have the msg:

Not loading blacklisted module ipv6

repeating over and over in the syslog whenever i'm online.

it's not a big deal, but i'm a real freak, and want to control every aspect of the OS..

just wondering.. is there a way to stop the syslog msg's? besides re-enabling ipv6 support..:p

it's just annoying that's all, because i have syslog tailed in conky on my screen, and i dont want to see anything about ipv6 anymore.

Thanks for any info!

---

### Post by dcstar on 2008-12-20
> **cb34 said:**
> i have purposely disabled ipv6 on my system.

now i have the msg:

Not loading blacklisted module ipv6

repeating over and over in the syslog whenever i'm online.

it's not a big deal, but i'm a real freak, and want to control every aspect of the OS..

just wondering.. is there a way to stop the syslog msg's? besides re-enabling ipv6 support..:p

it's just annoying that's all, because i have syslog tailed in conky on my screen, and i dont want to see anything about ipv6 anymore.

Thanks for any info!

It is a known bug (that also affects me):

[https://bugs.launchpad.net/ubuntu/+source/module-init-tools/+bug/66423](https://bugs.launchpad.net/ubuntu/+source/module-init-tools/+bug/66423)

Try this method of disabling ipV6:

[http://ubuntuforums.org/showthread.php?t=87798](http://ubuntuforums.org/showthread.php?t=87798)

---

### Post by cb34 on 2008-12-21
thanks dcstar, that 2nd link is actually where i got the info to disab;e ipv6, and i tried all different combinations of the bad_list file, blacklist file entry, changed aliases entries for ipv6, like it says in that thread all over.. i had it working before i reinstalled intrepid few dayz ago, but now the only way ipv6 is truly disab;ed for me, is when i add the line in the blacklist file. the aliases entries dont seem to do anything, and i reboot in between each edit.

thanks man. i'll look through the 14(LoL:D) pages again i guess soon, and try again and again ocd stylez, what im good at.. :p

Thanks!

(HEY! i wonder if this has something to do with why my web browsers, all browsers, crashing randomly.. (with or without flash installed), with or without disabling ipv6 in firefox..hmmm? because the crashing seems to happen when the browser is making multiple connections on a heavy page, like with lots of banners n things.. maybe it's somethin to do with ipv6 connection attempts.)

---

### Post by dcstar on 2008-12-22
> **cb34 said:**
> thanks dcstar, that 2nd link is actually where i got the info to disab;e ipv6, and i tried all different combinations of the bad_list file, blacklist file entry, changed aliases entries for ipv6, like it says in that thread all over.. i had it working before i reinstalled intrepid few dayz ago, but now the only way ipv6 is truly disab;ed for me, is when i add the line in the blacklist file. the aliases entries dont seem to do anything, and i reboot in between each edit.
......

The second link works for me on my 8.04 system, good luck trying to fix your 8.10 system.

---

### Post by cb34 on 2008-12-22
i got my system running super stable at the moment, fixed the firefox issue i mentioned, ipv6 IS diisabled.. it's just the constant syslog msg's that are real annoying.

can't they be sent to /dev/null or turn off monitoring of the ipv6 module all together from within the system somewhere.. that's what i love about linux.. anything i wanna do, i can do, and if it doesn't exist, write some code. :D so i do beleive there's a way to stop the msg's.. i just dont think anyone who is super experienced and knows the inside workings of the system/kernel care to waste there time with such low priority annoyances.. eez cool.. i'll survive. :D:D

but thanks dcstar, my 8.1 system is pretty fast and stable now. got no 'real' complaints here. :D

be well.

---

### Post by cb34 on 2008-12-24
ok.. i figured it out and have ipv6 disabled with NO syslog msg's being sent like crazy.

you don't use the /etc/modprobe.d/blacklist file at all.
i removed the ipv6 entry i added to the blacklist file.
using this blacklist file to blacklist the ipv6 module sends msg's to the syslog every time an internet connection attempt is made, hundreds and hundreds of msg's to syslog just saying, "Not loading blacklisted module ipv6" and then lines like, "this msg repeats 132 times" etc.

and bad_list file doesn't work for me either.

the only thing that did it was to modify the /etc/modprobe.d/aliases file so the ipv6 section(net-pf-10) looks like this: (just one line to change.)
```

#alias net-pf-10 ipv6
alias net-pf-10 off

```

all the other variations of modifying the etc/modprobe.d/aliases file didn't work, i tried each way systematically with a reboot in between each mod, and only the above worked for me.

ipv6 disabled, and no syslog messages. success. :guitar:

hope this helps someone out there.

overNout[COLOR="Red"]'[/COLOR].

---

### Post by cb34 on 2008-12-24
:lolflag: [http://ubuntuforums.org/showpost.php?p=2631546&postcount=116](http://ubuntuforums.org/showpost.php?p=2631546&postcount=116) :lolflag:

the answer was there along. :popcorn:
sudo killall -9 -r cb34

---

