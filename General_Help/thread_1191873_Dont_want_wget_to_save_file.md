---
title: "Dont want wget to save file"
date: 2009-06-19
forum: General Help
---

### Post by Johnsie on 2009-06-19
Hi, is there any way I can use wget to download a page but not save the file on my hard disk?

I'm running a cron job every hour and dont want my folder filled up with files. Any other helpful suggestions are welcome.

---

### Post by dcstar on 2009-06-20
> **Johnsie said:**
> Hi, is there any way I can use wget to download a page but not save the file on my hard disk?

I'm running a cron job every hour and dont want my folder filled up with files. Any other helpful suggestions are welcome.

Then get the cron job to delete the files.

---

### Post by rampageoberon on 2009-06-20
> **Johnsie said:**
> Hi, is there any way I can use wget to download a page but not save the file on my hard disk?

I'm running a cron job every hour and dont want my folder filled up with files. Any other helpful suggestions are welcome.

Johnsie, maybe consider the "-O" option. So for example the below code will not save the file, rather it will display on standard output

```
wget -O - http://checkip.dyndns.org
```

Hope that helps

---

### Post by andrew.46 on 2009-06-20
Hi Johnsie,

> **Johnsie said:**
> Hi, is there any way I can use wget to download a page but not save the file on my hard disk?

Sounds like you are after *curl* rather than *wget*.

Andrew

---

