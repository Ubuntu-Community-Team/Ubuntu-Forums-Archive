---
title: "Thunderbird Inbox file reduced to zero size!"
date: 2009-05-19
forum: General Help
---

### Post by uusimtel on 2009-05-19
Hello,

I use Ubuntu in an ext3 filesystem and I have just had a very unfortunate moment with Thunderbird. My Inbox was flooded and auto-compressed to zero size!! I lost >3000 e-mails.

Is there any way to salvage the previous Inbox file (as it was before the compression)?

I am currently reading the documentation of foremost. It seems able to recover most common files like jpg, pdf, avi etc, but I have found no way to tell it to search for mbox (i.e. plaintext) files.
Any ideas/suggestions would be most appreciated. In other words: H E L P !!!!!

---

### Post by Bindsa on 2009-05-19
I'm afraid you lost your data permanently, you can however try to run file recovery software on your disk. To prevent this from happening in the future change the settings displayed in this menu: File >> Offline >> Offline settings

---

### Post by uusimtel on 2009-05-21
Thanks for your reply.

Fortunately, the Foremost software worked OK and I was able to recover about 4GB of my mbox e-mail files (in chunks no larger than 7-8 MB each). I believe some of them are redundant, but I estimate that I rescued more than 50% of the damaged Inbox file. By the way Foremost was awsome; It was even able to recover some chunks from the swap partition as well!! And I learned a lot in the procces.

By the way, just in case you ever happen to be in a similar situation (I hope you never be) the correct line in the foremost.conf file that does the job should read like this:
```
     .     y    100000000     X-Mozilla-Status    X-Mozilla-Status     ASCII
```Please note that despite what the documentation says, you should not use the keyword NONE if you wish to carve files with no extension. It seems to work fine when you run it with the -w option but in the real scenario it does not build the proper path to save the files and stops with an error message (yes, probably a bug, or an undocumented "feature"). After some experimentation, I found that the dot (.) worked OK instead of NONE.

And yes, I WILL backup my files from now on. I guess I have been over-confident on Thunderbird and I never expected to crash like that due to a few hundred spam mails that overflooded my Inbox :)

---

### Post by megamania on 2009-05-21
> **uusimtel said:**
> 
And yes, I WILL backup my files from now on. I guess I have been over-confident on Thunderbird and I never expected to crash like that due to a few hundred spam mails that overflooded my Inbox :)
You may trust Thunderbird but your disk may break, you could inadvertedly delete your emails and empty the trash, a bad sudo command could destroy your file system...

I'm not preaching, just thinking out loud. I started backing up my data regularly 6/7 years ago. Now, when I don't backup for a week I freak out.  :-)

---

### Post by uusimtel on 2009-05-28
> **megamania said:**
> You may trust Thunderbird but your disk may break, you could inadvertedly delete your emails and empty the trash, a bad sudo command could destroy your file system...

I'm not preaching, just thinking out loud. I started backing up my data regularly 6/7 years ago. Now, when I don't backup for a week I freak out.  :-)

Yes, but I would expect that Thunderbird should at least check how much free disk space is available before it tires to download new e-mails from the POP server. :(
In fact, it seemed it checked, didn't liked what it saw, and compressed my Inbox to gain some space. I have no objection to that, but a verification from the user should be mandatory before taking such liberties, IMHO.

---

