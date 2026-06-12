---
title: "PDF files not accepted by cups for printing"
date: 2011-08-19
forum: Desktop Environments
---

### Post by mbojan on 2011-08-19
My Ubuntu Lucid 64-bit stopped printing PDF files from all applications. I'm using a network printer. It was before OK, and stopped working suddenly. I'm not sure whether its because some package update on my machine or perhaps on the printer server, or some other reason. 

In /var/log/cups/error_log I have:

```
E [19/Aug/2011:14:15:29 +0200] [Job 302] Print file was not accepted (Unsupported format 'application/pdf'!)!
```

followed by other messages. The symptoms are identical to this bug report:

[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/576192](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/576192)


However, I'm not sure what to make out of the reply by Till Kamppeter at the bottom (item 1) there. How exactly do I "set up a raw queue on the client" etc.

Help? Anybody?

---

