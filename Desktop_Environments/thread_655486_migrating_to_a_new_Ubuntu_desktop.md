---
title: "migrating to a new Ubuntu desktop"
date: 2008-01-01
forum: Desktop Environments
---

### Post by joeybutterface on 2008-01-01
Hello,

I'm about to migrate an existing Ubuntu 7.10 desktop install to a new Dell system (that will also run Ubunty 7.10). I want to know which is the easiest way to migrate all the existing settings, emails, address book, Mozilla bookmarks etc. to the new machine? There is quite a bit of data there.

I have another network server available to temporarily store files that need to be migrated. That server is also running Ubuntu 7.10. I also have external USB hard drives that could be used.

What is the recommended way to handle this? How would you approach it? Any guides?

Thanks in advance for your suggestions!

---

### Post by elliotjreed on 2008-01-01
When I re-installed, all I did was copy all of the files, and hidden files in my Home folder - to a usb, or external HDD, or a CD.

---

### Post by jamaisvu on 2008-01-01
> **elliotjreed said:**
> When I re-installed, all I did was copy all of the files, and hidden files in my Home folder - to a usb, or external HDD, or a CD.

[FONT=Franklin Gothic Medium]Just watch things like /home/yourusername/.mozilla/firefox/cache/ -- this can be massive, and may well be a waste of time to copy. The file size view in Konqueror is really useful for identifying massive rubbish.[/FONT]

---

### Post by joeybutterface on 2008-01-01
> **elliotjreed said:**
> When I re-installed, all I did was copy all of the files, and hidden files in my Home folder - to a usb, or external HDD, or a CD.

That's what I figured. I was going to use rsync to my home server but it just feels like overkill. And probably slower given the desktop will be connecting on a wireless access point to retrieve the old files.

I'll try the USB drive route.

Thanks!

---

