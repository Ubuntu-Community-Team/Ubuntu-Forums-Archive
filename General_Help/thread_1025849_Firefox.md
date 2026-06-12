---
title: "Firefox"
date: 2008-12-30
forum: General Help
---

### Post by RedSingularity on 2008-12-30
Hey Guys,

I am using firefox on my Ubuntu desktop.  The problem is firefox seems to be loading the pages slowly.  As i scroll with the mouse wheel the page lags.  This seems more prevalent on sites with a lot of images or videos on the page I am viewing.  Any ideas on how I can speed it up? 

Thanks

---

### Post by kokkus on 2008-12-30
See if this can help you.

1.Type about:config into the address bar and hit return. Scroll down and look for the following entries:
network.http.pipelining
network.http.proxy.pipelining
network.http.pipelining.maxrequests
Normally the browser will make one request to a web page at a time. When you enable pipelining it will make several at once, which really speeds up page loading.

2.
Alter the entries as follows:
Set network.http.pipelining to true
Set network.http.proxy.pipelining to true
Set network.http.pipelining.maxrequests to some number like 30.
This means it will make 30 requests at once.

3.
Lastly right-click anywhere and select New-> Integer. Name it nglayout.initialpaint.delay and set its value to 0?. This value is the amount of time the browser waits before it acts on information it receives.

---

### Post by Izek on 2008-12-30
Are you using compiz as well?

---

### Post by RedSingularity on 2008-12-30
Ok I configured the settings under **about:config** and that did help with page loading.  Its much faster now thanks!!  But in responce to Izek, yes I am using compiz.  I am curious to know what effect would that have on it?

---

### Post by Izek on 2008-12-30
Compiz sometimes causes xorg to use up more resources than it should, in turn, causing a systemwide slowdown, firefox scrolling slower than usual is one indication of such.

---

### Post by RedSingularity on 2008-12-30
Could More RAM or a newer Graphics card help solve that?

---

### Post by rolandixor on 2009-01-18
what about nvidia drivers?

---

