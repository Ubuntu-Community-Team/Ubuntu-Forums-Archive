---
title: "Crontab assistance needed"
date: 2009-05-03
forum: General Help
---

### Post by ml41782 on 2009-05-03
This is my first shot at using crontab with a new machine. 

Yes I have read the FAQs but I still have a problem. 

crontab -e

it starts up just fine

otg1017@Webserver:~$ crontab -e
no crontab for otg1017 - using an empty one
29
05 * * * * /home/otg1017/inverters.sh
?


I can't use a ctrl-C to get out. what is the question mark and what is the 29 ? 

Thank you for any help or guidence you can give. 

Michael

---

### Post by spiderbatdad on 2009-05-03
the -e option launches the current crontab using vi as editor. Check out a tutorial on using vi modes like :wq to save and exit, or you can select a more simple default editor:
```
sudo select-editor
```choosing 3 for nano is easiest.

---

### Post by codeseer on 2009-05-03
Give this a go:

```

crontab -r
crontab -e

```

---

### Post by mali2297 on 2009-05-03
To use nano as the editor, try
```

EDITOR="nano" crontab -e

```

---

### Post by ml41782 on 2009-05-03
Thanks for the help, 

I found one that I hope will work for me. 

crontab <cron file> 

I listed out all the entries I needed and then reset cron from root

/etc/init.d/cron restart

everything appears to be working for me. Just frustration more than anything doing it the way I normally do it on a sun box. 

Thanks again

---

