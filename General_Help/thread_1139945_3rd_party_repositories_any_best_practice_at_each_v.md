---
title: "3rd party repositories: any best practice at each version upgrade?"
date: 2009-04-27
forum: General Help
---

### Post by UranUtan on 2009-04-27
Hi,

I started with Ubuntu with 8.10 x64. I had added a few entries in Software Sources. Something like **deb .... intrepid main**

After I upgraded to 9.04, all of the 3rd parties repository are disabled. I had to search for the new PPA information and create a new 3rd party repositories one by one.

I guess I am going to repeat the same ritual again in 6 months. This will probably take me may be 30 minutes to complete, so this is not that big of a deal. However, I wonder if there is a better way to update the 3rd party repositories at every Ubuntu release.

If you have a good practice, I would appreciate any advice.

Thanks in advance.

---

### Post by dLeon on 2009-04-27
Backup/copy/write your sources.list somewhere else (floppy?/a piece of paper?). At upgrage, just copy/rewrite the 3rd party lines to your new sources.list. These will safe you 29.59 minutes.

---

### Post by snowpine on 2009-04-27
Also don't forget to check the main Ubuntu repository; sometimes, 3rd party apps get moved in to future releases of Ubuntu. (wicd is a good example)

---

### Post by UranUtan on 2009-04-27
> **dLeon said:**
> Backup/copy/write your sources.list somewhere else (floppy?/a piece of paper?). At upgrage, just copy/rewrite the 3rd party lines to your new sources.list. These will safe you 29.59 minutes.

Wow, this is the trick I was looking for, thanks.

If I restore the sources.list from the previous Ubuntu version. I assume that I must replace all 'intrepid' by 'jaunty'. Can you please confirm.

Also, I remember in the 3rd party repositories. There was something saying backport. Unfortunately it was disabled and I have deleted it. Can you give me the deb ... line to put back this backport thing? Not sure if I will need it but I have seen in other blogs as this is a good practice to enable the backport repository.

---

