---
title: "Epiphany + Firefox crashing on same websites -&gt; Gecko issue?"
date: 2009-05-05
forum: General Help
---

### Post by chainzz on 2009-05-05
Since this morning I am experiencing crashes with both Firefox and Epiphany when I visit Gmail. It also happens with both browsers when I visit Ustream.tv. When I look at the error message in the terminal it just says "Segmentation fault" (for both Firefox and Epiphany) and that's it. Both browsers seem to crash just after the whole page has loaded. Although Firefox already seems to be very crashy in the latest versions (More people seem to be complaining about it), a 100% sure crash when you visit certain websites is new for me. Could this be a Gecko related problem because Epiphany is crashing too with the same websites?

I am using only one add-on for Firefox by the way: Xmarks. I don't think this is the problem, because Epiphany isn't using add-ons at all but it also crashes.

Any ideas?

(By the way, I am using Ubuntu 9.04 64-bit with all the latest updates and with Firefox 3.0.10 and Epiphany 2.26.1 (straight from the repos))

---

### Post by Sef on 2009-05-05
> Could this be a Gecko related problem because Epiphany is crashing too with the same websites?

I have the same os as you and don't have a problem.   I would say it was with your gecko.  If I find what to do about seg faults, I will add an update.

---

### Post by sports fan Matt on 2009-05-05
Sef, Ive also noticed this with 9.04 but not 64 bit and the latest ff.  Crashes and "hanging pages" as well.  Hanging pages to where I need to kill the page several times a day with System Monitor..The only addons I have are novell moonlight, pdf download, xmarks (formerly foxmarks) and yahoo mail notifier...Im jjust adding my $0.02

---

### Post by chainzz on 2009-05-05
Well, I have uninstalled Flash 10 for 64-bit (the beta) and installed flashplugin-installer from the repos and now both Epiphany and Firefox don't crash anymore. Really weird, because Gmail doesn't even use Flash. Too bad I can't use the native 64-bit Flash 10 now though.....

---

