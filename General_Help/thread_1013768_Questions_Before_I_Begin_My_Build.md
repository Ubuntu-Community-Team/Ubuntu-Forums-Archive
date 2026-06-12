---
title: "Questions Before I Begin My Build"
date: 2008-12-17
forum: General Help
---

### Post by falconed7 on 2008-12-17
Hey everyone,

I have just ordered my hardware for a home file server and the gear should be coming within a day to two.

I am going to run Ubuntu Server 8.04.1 and it's going to be headless. I have only used Ubuntu desktop 8.10 on a laptop for a few months and I am still keen to learn, hence why I am choosing the server edition.

I have a few questions about my installation:

I am going to be using 2 HDDs (80GB for OS, 750GB for data) and am wondering if I should only install the 80GB first, install the OS, and then place the second in later after using gparted to format the drive? Or would it be better to just put them both in from the get-go and let the OS installation worry about it (if that's possible)?

So with my understanding (probably wrong) the drives will look like this with both drives having 1 partition each:
80GB = /boot
750GB = /home

I will be following this guide: [Click Here]("http://www.howtoforge.com/ubuntu-home-fileserver").

It says I should format the data drive as NTFS... I assume this isn't necessary as I wouldn't be taking it out and placing it into my windows PC? So ext3 will be fine?

I'll be installing OpenSSH from the OS install and be using Putty straight away to access the server.

Finally, I am going to be installing the following:
[LIST]
[*]Samba
[*]rsync
[*]mediatomb
[*]Some sort of torrent client
[/LIST]
I am going to be installing webmin/eBox (which is better?) and am wondering if I should install and configure this first or last?

Any help will be great!

Cheers.

---

### Post by squaregoldfish on 2008-12-17
I can answer some of your questions.

You can put both drives in straight away - the partition editor on installation will make it perfectly obvious which drive is which.

Your partitions should be:

80GB = /
750GB = /home

ext3 is what you want for the formatting.

As for webmin/Ebox, I don't know which is best, but whichever you go for should be installed last, after everything else is up and running. This will ensure that it finds everything it needs to when it's first installed and run.

Steve.

---

### Post by falconed7 on 2008-12-17
> **squaregoldfish said:**
> I can answer some of your questions.

You can put both drives in straight away - the partition editor on installation will make it perfectly obvious which drive is which.

Your partitions should be:

80GB = /
750GB = /home

ext3 is what you want for the formatting.

As for webmin/Ebox, I don't know which is best, but whichever you go for should be installed last, after everything else is up and running. This will ensure that it finds everything it needs to when it's first installed and run.

Steve.

Thank you Steve.

You pretty much covered everything I needed to know.

---

