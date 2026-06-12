---
title: "Updates Error/Bug @ New updates how to solve?"
date: 2008-12-04
forum: General Help
---

### Post by EsixNL on 2008-12-04
So there are new Updates,
30 minutes ago.

I updated it but at the point the updates were ready the computer Hung, and had to restart my computer. 

Now I get the following Error, 

```

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

```

So I start Terminalwindow

```

Sudo -i 
dpkg --configure -a

```
I get the following error: 

```

dpkg: Error at analysing  from File ' /var/lib/dpkg/updates/0117 at line 1: field name

```

I Couldn't find the right translation for Fieldname in dutch it is; Veldnaam. 
I'm from the netherlands so.. 

Now is my question

how to install the new updates without the error?

Thanks,

Seb

---

### Post by Wayne_V on 2008-12-04
I would just try starting over:

# rm /var/lib/dpkg/updates/*
# apt-get update ; apt-get dist-upgrade

---

### Post by EsixNL on 2008-12-04
Now I've more problems. ;o

```

dpkg: Error at analysing  from File ' /var/lib/dpkg/updates/0117 at line 1: field name

EOF in value of fiels 025 (missing closed new line)

```


Now I asked myself?
Isn't it just possible, to Delete everything in the map Updates, and than I automaticly get al the updates again

Or doesn't it work that way?

---

### Post by EsixNL on 2008-12-04
bump

---

### Post by Wayne_V on 2008-12-04
Yes, you should be able to.   You may want to back things up before you start rm'ng tho:

# cd /var/lib/dpkg
# mkdir ~/dpkg-save
# find . | cpio -padm ~/dpkg-save

---

### Post by EsixNL on 2008-12-04
nope didn't work :\
only got the message he couldn't find the directory, 
so I turned to the Recovery mode and than dpkg resolve etc.

Didn't workout either,
So.

Now back to the start I Get the error message;

```

dpkg: error at analysing the file `/var/lib/dpkg/updates/0211'at line 1: EOF in the value of field `1025' (missing closing new line

```

so I 'm back at the start :\

Please help it's a anoying problem 

@ wayne thanks for the help sofar ^^

---

### Post by Wayne_V on 2008-12-04
So what exactly have you tried so far?  Can you send the commands you've run?

---

