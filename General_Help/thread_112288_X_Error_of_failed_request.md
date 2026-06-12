---
title: "X Error of failed request"
date: 2006-01-04
forum: General Help
---

### Post by Baf on 2006-01-04
I've had a problem opening up Unreal Tournament(UT99) for about a week now. Everything had been working fine until last week. I had been running UT since 5.10 came out. I get this error in the terminal when I try to run UT:

> X Error of failed request:  XF86DGANoDirectVideoMode
  Major opcode of failed request:  137 (XFree86-DGA)
  Minor opcode of failed request:  2 (XF86DGADirectVideo)
  Serial number of failed request:  114
  Current serial number in output stream:  115
Signal: SIGSEGV [segmentation fault]
Aborting.
XIO:  fatal IO error 0 (Success) on X server ":0.0"
      after 125 requests (123 known processed) with 5 events remaining.

I hadn't done any changes, this error just randomly happend. I've been looking around for a solution and haven't had any luck so far but I will continue to look. I would appreciate any help I can get.

---

### Post by mo_x on 2006-01-04
Did you upgrade your nvidia driver? Latest nvidia driver does not support dga.

---

### Post by Baf on 2006-01-04
Sorry, I should have mentioned that. I have an ATI card and like I said everything was working right. I didn't upgrade anything, including the driver. I've been using the same one since the beginning.

---

### Post by Baf on 2006-01-26
bump

---

### Post by Baf on 2006-01-26
Nevermind, I just simply reinstalled the video drivers and it's working again.

---

