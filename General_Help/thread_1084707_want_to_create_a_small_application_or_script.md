---
title: "want to create a small application or script"
date: 2009-03-02
forum: General Help
---

### Post by gkraju on 2009-03-02
hi
my network often disconnects(line problem will be fixed soon)
but now i want to create an application like the one in Xp a small pop up in taskbar that tells when the network was connected and the duration of it 
can any one help me in this?
thanks in advance

---

### Post by porchrat on 2009-03-02
Do you mean your LAN or your internet connection?

You could set up some sort of script that pings the DNS or LAN gateway and only returns something for you when "host unreachable" occurs or when packets are dropped.

Perhaps a cronjob or something, I'm not sure how they work, but people often create a cronjob when they want something to run every so often.

Just a thought for what it is worth.

EDIT: I'm not aware of a way to make a script bring up a taskbar notification though, for that you'd need something more sophisticated.

---

### Post by gkraju on 2009-03-02
> **porchrat said:**
> Do you mean your LAN or your internet connection?

You could set up some sort of script that pings the DNS or LAN gateway and only returns something for you when "host unreachable" occurs or when packets are dropped.

Perhaps a cronjob or something, I'm not sure how they work, but people often create a cronjob when they want something to run every so often.

Just a thought for what it is worth.

it is not my lan it is my internet that often disconnects
so can you tell me briefly what i ahve to do

---

### Post by crokett on 2009-03-02
Google search for Linux Monitor network traffic:

[http://www.google.com/search?q=linux+monitor+network+traffic&sourceid=navclient-ff&ie=UTF-8&rlz=1B3GGGL_enUS266US280&aq=t](http://www.google.com/search?q=linux+monitor+network+traffic&sourceid=navclient-ff&ie=UTF-8&rlz=1B3GGGL_enUS266US280&aq=t)

One of those may do what you want

---

