---
title: "moving logs"
date: 2009-06-01
forum: General Help
---

### Post by slimx3m on 2009-06-01
have a question......... i am moving my server from windows base to linux based.  is there a way that i could convert my windows logs to linux? (e.g. online converter, program, or something)

thanks in advance

---

### Post by upbeat.linux on 2009-06-02
Your windows server logs will include separate entries for Application, Security, System, etc that may or may not relate to the specific linux logs.  

You might want to look into running splunk on your linux box and shipping the logs via NC_Net or another app so they are searchable.  

As far as logs in the past are concerned It really depends on what you intend to do with them.

---

### Post by slimx3m on 2009-06-02
upbeat.linux,

thnx for your help but i was really tired when i wrote that and your answer make sense but i didn't explain exactly what i was looking for.

what i am looking for i found it this mourning :P and is to be able to convert an IIS log to Apache log ([iis2apache]("http://www.jammed.com/~jwa/hacks/")).

sorry for not explaining well enough.

---

### Post by upbeat.linux on 2009-06-09
sweet! Good find!

---

