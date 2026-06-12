---
title: "Programs Crashing"
date: 2005-10-16
forum: Desktop Environments
---

### Post by The Headhunter on 2005-10-16
OK, so I currently have a couple of programs where if I open them, they crash immediately upon opening.  Those programs are gnome-cups-add and rhythmbox.  So I tried running them in the terminal to see if they output any text into the terminal window.

when I run gnome-cups-add, I get several of these:
** (gnome-cups-add:29580): WARNING **: Two ppds have driver == 'hpijs (recommended)'
        ->hplip/HP-PSC_2500-hpijs.ppd (HP PSC 2500 Foomatic/hpijs[1]) and
        ->foomatic-ppds/hplip/HP-PSC_2500-hpijs.ppd (HP PSC 2500 Foomatic/hpijs)[1]

when I run rhythmbox, I get this:
GLib-ERROR **: gmem.c:141: failed to allocate 1664036668 bytes
aborting...

From the look of the output in the terminal window, it looks like they're not related but what they have in common is that they crash immediately upon starting, every single time I try to open them.  If anyone knows what I could do, please tell me.  By the way, priority is on gnome-cups-add, as I would like to be productive while on linux.  Thanks.

---

### Post by farruinn on 2005-10-31
I'm experiencing this same exacpt problem. What architecture are you on? I'm on breezy for ppc. Anyone else having this problem?

I have filed a bug on this.

---

### Post by The Headhunter on 2005-10-31
I'm on breezy on an x86 and I filed a bug earlier too

---

### Post by farruinn on 2005-11-01
Sorry I wasn't clear earlier, I only have the rhythmbox problem. However, I've found that switching apps/rhythmbox/first_time_flag to true in Configureation Editor has resolved the issue for me. Unfortunately it means I cannot now submit a backtrace for the bug report.

Could you please attach a stack trace here: [https://launchpad.net/products/rhythmbox/+bug/3763]("https://launchpad.net/products/rhythmbox/+bug/3763")

There is a link from that page that tells you how to get a stack trace.

Regards,
Nathan

---

### Post by farruinn on 2005-11-02
I have some more information now.

It appears that my problem is iPod related.  I only have the problem when my iPod is plugged in.  Interestingly, I have the same exact problem with amarok when my iPod is plugged in (glibc memory error).  Headhunter, do you get this problem with an iPod?

---

