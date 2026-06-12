---
title: "No Crontab"
date: 2009-03-29
forum: General Help
---

### Post by plinydogg on 2009-03-29
Hi folks,

I'm trying to add a cron job to my crontab. I've never done this before but have read a few tutorials and understand the basic syntax. The problem is that I don't appear to have a crontab file. 

The output of crontab -l is:  

```
no crontab for *username*
```

When I try to edit the crontab by running crontab -e it opens the Nano editor and appears to edit a file in the /tmp directory. The terminal output is:

```
no crontab for *username* - using an empty one
```

How do I create a crontab? And where does it go once I've created it?

Thanks in advance!

---

### Post by dcstar on 2009-03-30
> **plinydogg said:**
> Hi folks,

I'm trying to add a cron job to my crontab. I've never done this before but have read a few tutorials and understand the basic syntax. The problem is that I don't appear to have a crontab file. 

The output of crontab -l is:  

```
no crontab for *username*
```

When I try to edit the crontab by running crontab -e it opens the Nano editor and appears to edit a file in the /tmp directory. The terminal output is:

```
no crontab for *username* - using an empty one
```

How do I create a crontab? And where does it go once I've created it?

Thanks in advance!

It takes care of everything itself.

Install the gnome-schedule package if you want a GUI.

---

### Post by plinydogg on 2009-03-30
Thanks for the tip. I'll give it a go when I get home from work!

---

### Post by plinydogg on 2009-03-30
Worked great!

---

