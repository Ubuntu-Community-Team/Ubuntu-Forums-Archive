---
title: "How robust is NTFS support?"
date: 2009-06-01
forum: General Help
---

### Post by TheForumTroll on 2009-06-01
Hello =)

I'll make this short:
I have a drive I use with torrents. It's using NTFS. I need to use it in both Ubuntu and Vista. So my question is: Is NTFS write support mature enough that I can download directly to my NTFS drive or should I continue to do as I do now (download to /home and copy to the NTFS drive)?

---

### Post by michy99 on 2009-06-01
I have never had problems downloading to a NTFS drive on either Hardy or Jaunty. Your mileage may vary.

---

### Post by t0p on 2009-06-01
When I still dual-booted with XP, back in the days of Gutsy (or was it Feisty..?) I wrote direct to NTFS all the time and it never fell over on me.

Of course YMMV - other people have reported problems with NTFS support.  But I haven't noticed anyone saying that for quite some time.  Hence I think that NTFS support is mature enough to be counted on.

---

### Post by TheForumTroll on 2009-06-01
Okay, I'm going to go ahead and see how it works out. Thanks =)

---

### Post by aeiah on 2009-06-01
you should be fine. as a general rule anything that's been included for a while in a default ubuntu installation should be stable enough to be trusted, especially if it was included in a long term release. you're right to not just jump in though of course.

---

### Post by mb_webguy on 2009-06-01
I've been dual-booting Windows and Ubuntu for a couple of years now, and using a shared data partition formatted as NTFS.  Except for the obvious lack of support Linux-style file permissions on the NTFS partition, and one particular instance where Ubuntu wouldn't mount the NTFS partition because Windows had crashed and not closed out the NTFS journal properly, I've never had any problems.

---

### Post by Wiebelhaus on 2009-06-01
> **TheForumTroll said:**
> Hello =)

I'll make this short:
I have a drive I use with torrents. It's using NTFS. I need to use it in both Ubuntu and Vista. So my question is: Is NTFS write support mature enough that I can download directly to my NTFS drive or should I continue to do as I do now (download to /home and copy to the NTFS drive)?

Yes , Once it's mounted you can use it like any other mounted file system.

```
sudo apt-get install ntfs-3g ntfs-progs
```

---

### Post by HavocXphere on 2009-06-01
> **TheForumTroll said:**
> Is NTFS write support mature enough
Yes I think so. I'm constantly moving around big amounts of data across drives from ubuntu...and 90% of my hdd space is ntfs formatted.

The one thing I'd be careful with though is the sleep/standby/suspend stuff. It seems to sometimes unmount an external ntfs drive & not remount it cleanly.

---

### Post by TheForumTroll on 2009-06-01
> **Wiebelhaus said:**
> Yes , Once it's mounted you can use it like any other mounted file system.

I know I can mount NTFS drives but torrenting does a LOT of writing and I would be quite sad if all 500GB was lost. I just recently started using Ubuntu again (and this time I think I'll stay) but last I was using it most said that NTFS _writing_ wasn't mature enough. That was the reason I kept using Windows. But that was back in 2005/2006...


> **HavocXphere said:**
> Yes I think so. I'm constantly moving around big amounts of data across drives from ubuntu...and 90% of my hdd space is ntfs formatted.

Okay, that does sound promising since it's the write part I'm worried about. If something bad happens I'll let you all know ;)

---

### Post by Wiebelhaus on 2009-06-01
> **TheForumTroll said:**
> I know I can mount NTFS drives but torrenting does a LOT of writing and I would be quite sad if all 500GB was lost. I just recently started using Ubuntu again (and this time I think I'll stay) but last I was using it most said that NTFS _writing_ wasn't mature enough. That was the reason I kept using Windows. But that was back in 2005/2006...




Okay, that does sound promising since it's the write part I'm worried about. If something bad happens I'll let you all know ;)

Yea , I move 25gig plus on a regular basis , but 500Gig is crazy.

---

