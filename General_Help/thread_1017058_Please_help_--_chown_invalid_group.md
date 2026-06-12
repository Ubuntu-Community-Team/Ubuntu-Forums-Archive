---
title: "Please help -- chown: invalid group"
date: 2008-12-20
forum: General Help
---

### Post by togo59 on 2008-12-20
Ubuntu 8.10 (2.6.27-9-genertic). Screwed up groups after trying to configure sound card. Uing User and Group utility.

I know this [has been posted]("http://ubuntuforums.org/showthread.php?t=997346&highlight=invalid+group") but it doesn't quite relate to my problem. And [this has also touched on the problem. ]("http://ubuntuforums.org/showthread.php?t=977104&highlight=chown%3A+invalid+group")

However, in the second case, the /etc/group file had been completely overwritten. In my case it "looks" OK.

Symptom:
When I boot I get the Ubuntu logo and orange slider bar and then this:
```

chown: invalid group root:utmp
chown: invalid group root:root
chown: invalid group root:polkituser
* Loading ACPI modules                                   [OK]
* Loading ACPI services                                  [OK]
* Starting system log daemon                             [OK]
chown: invalid group 'syslog:admin'
 :
 : lots of these
 :
chown: invalid group 'syslog:admin'
* Doing Watcom setup                                     [OK]
* Starting kernal log daemon                             [OK]
chown: invalid group 'klog:klog'

```
and then it hangs.

I have had a look at the /etc/group file and the passwd file and can see nothing obviously wrong. I.e. both have many lines which follow the correct syntax, e.g. 
```
login-name:x:user-ID:group-ID:info:Directory:program
```

Could you please help me?

I can just reinstall from the live CD I suppose. Or copy the group file over but in that case, the passwd file won't match the group file. And presumably that will screw thing up just as much.

Many thanks!

---

### Post by taurus on 2008-12-20
Why don't you post /etc/group?

```
cat /etc/group
```

---

