---
title: "How to skip google-analytics (in Firefox)"
date: 2009-02-12
forum: General Help
---

### Post by cl333r on 2009-02-12
Hi folks,
For me google-analytics is the major issue that makes web pages load slowly (it also seems my host/firefox/proxy has problems connecting to it), so I'd like to force Firefox to never follow google-analytics links which are put on a lot of sites to track the users.
So far I only found the Google customizer addon, but it doesn't seem to work as expected.
Any other ideas?

---

### Post by mikewhatever on 2009-02-12
You can block google-analytics by adding it to the adblock plus extension.

---

### Post by sune_cph on 2009-02-12
Append the following to your hosts file (sudo nano /etc/hosts):

```
0.0.0.0 www.google-analytics.com ssl.google-analytics.com

```

This, of course, has global impact and is not limited to Firefox.

/Sune

---

### Post by cl333r on 2009-02-12
Thanks a lot both of you!
I edited /etc/hosts and the sites now load snappier, no problems so far, haven't tried adblock because the first solution I tried works fine :)

---

