---
title: "Web interface to LTSP"
date: 2007-11-28
forum: Desktop Environments
---

### Post by wjhildreth on 2007-11-28
Hello all,

I hope I have this posted to the correct forum.

I am interested in using Linux Terminal Server for distributing some applications. I would like the applications to be available to some windows machines as well. Now in Citrix, they have a client for each OS, but it looks like LTSP only runs in a thin client mode. Is there fat client software? Is there web based version on the client or some means of allowing a Windows machine to connect to the server and run apps?

Many thanks for your time.

Regards,

Joe Hildreth

---

### Post by timcredible on 2007-11-28
are you asking for a windows program that will connect to a linux/unix machine with xdm?  xming is an open source product that works very well for this.  if i'm not understanding the question, just disregard.

---

### Post by wjhildreth on 2007-11-28
Well,

Our corporation uses Citrix to distribute applications to remote users through the web. The hospital that I work for is moving off the corporate network and the Citrix services will not be available to them. They cannot afford Citrix and the associated licensing fee, but a few users will need access from home for one reason or another.

I would like to used Linux Terminal Server in place of Citrix to allow remote access to the Health Information System. In citrix you can install a platform dependent client (windows, linux, whatever) and connect to the citrix server to run applications. Also Citrix provides a web interface to the applications.

Is it possible to do the same type of function with LTSP? While reading up on it, it seems that only thin client technology will run with LTSP? Is there another way to do what I am asking?

Regards,

Joe

---

