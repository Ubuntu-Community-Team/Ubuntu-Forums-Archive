---
title: "Panel Crashes repeatetly after icon theme change"
date: 2013-03-29
forum: Desktop Environments
---

### Post by hister on 2013-03-29
Hi guys and gals,

I am a complete Linux noob so please go easy on me.

I have had a fresh Lubuntu 12.10 install today and downloading it I tried downloading and using the faenza icon theme.  While scrolling through the available themes and applying to see how they looked the panel restarted itself in order to present the new theme until it got in a state of constant restarting from which I could not get it out.  Even if I changed to the the default theme and applied the panel would still keep restarting itself driving my CPU crazy.  I tried restarting but nothing.

Thank you for your help in advance,

PS I had Lubuntu with similar settings to what I tried to achieve today for a couple of days now working with no issues at all, but had to reinstall due to a hard drive update.

---

### Post by Rex Bouwense on 2013-03-30
I was a little confused about your post.  You already had this set up and running well for a couple of days but you had to re-install and that is where your problem began.  Is that correct?
It is not rare for the LxPanel to freeze up.  To correct this all you need to do is restart it.
```
lxpanelctl restart
```

---

