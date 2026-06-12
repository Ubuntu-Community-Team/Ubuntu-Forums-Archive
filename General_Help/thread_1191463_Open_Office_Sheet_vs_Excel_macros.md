---
title: "Open Office Sheet vs Excel macros"
date: 2009-06-19
forum: General Help
---

### Post by wurx on 2009-06-19
Hi there,

I'm working on some complexed excel sheets at work. But when I try to open them with open office, all the links are missing. I've activated the macro's in open office that doesn't help at all. I would like to get it going in order for me to do my work at home.

Any ideas?

---

### Post by akakingess on 2009-06-19
> **wurx said:**
> Hi there,

I'm working on some complexed excel sheets at work. But when I try to open them with open office, all the links are missing. I've activated the macro's in open office that doesn't help at all. I would like to get it going in order for me to do my work at home.

Any ideas?
Let me get into work where some of my more 'complex' spreadsheets are and experiment and will check back in with you, just didn't want you to think everyone was ignoring you, they just may not know, or may not be where the complex spreadsheets are (like me, but give me an hour or two)....

akakingess

---

### Post by akakingess on 2009-06-19
OK, I was able to open one of my on-call spreadsheets with macros disabled and enabled. I am using Open Office 3.0.1 (specifically - OOO300m15 (Build 9379)). I know this doesn't really help you much, but let me know what else I can try to help you solve your issue.

akakingess

BTW, I had macros set to notify/ask me before enabling them when I opened the spreadsheet, and I opened the document from within OpenOffice rather than double-clicking, have no idea if this is relevant, just trying to be helpful ;)

---

### Post by niteshifter on 2009-06-19
Hi,

Bad news: That's the one area where OpenOffice Calc and Excel are not compatible - macros.

Excel: Macros are Visual Basic for Applications (VBA)
Calc: OpenOffice Basic. (There are other languages that can be used, but this most 'Excel-like').

Good news: BASIC is BASIC. The two are keyword compatible. Bad news: How these two programs setup to access data / functions within the document differ. Takes a rewrite to fix, which makes moving back and forth difficult.

---

