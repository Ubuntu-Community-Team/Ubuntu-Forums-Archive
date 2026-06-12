---
title: "Need to prevent or automatically restart firefox"
date: 2009-01-14
forum: General Help
---

### Post by ChrisGoforth on 2009-01-14
I have been tasked with making 2 internet ready kiosks here at work. We have decided to use ubuntu with firefox. I have got everything working with no problems so far. I just need to get over the last 2 hurdles. 

Hurdle 1 (the biggest) - I need to be able to either prevent users from closing firefox or to have it automatically restart if it has been closed. I have the firefox kiosk mode add-in installed and it works great except that in order to have a navigation bar it also gives you the ability to close firefox. Firefox does automatically start when you boot the computer so that is not an issue either.

Hurdle 2 (minor) - I need to add content management to firefox. I am planning on using a firefox plug in for this unless someone has any other suggestions.

Thanks in advance for your help. I do appreciate it.

Chris Goforth

---

### Post by easybake on 2009-01-15
> **ChrisGoforth said:**
> I have been tasked with making 2 internet ready kiosks here at work. We have decided to use ubuntu with firefox. I have got everything working with no problems so far. I just need to get over the last 2 hurdles. 

Hurdle 1 (the biggest) - I need to be able to either prevent users from closing firefox or to have it automatically restart if it has been closed. I have the firefox kiosk mode add-in installed and it works great except that in order to have a navigation bar it also gives you the ability to close firefox. Firefox does automatically start when you boot the computer so that is not an issue either.

There are a couple ways that I can think of off the top of my head, but I really don't have the time to go into too much detail because I'm leaving soon.

You can create a script to see if firefox is running and if it isn't then have it launch firefox. You would then use cron to execute that script at any set interval.

or

You could use the [menu-editor ]("https://addons.mozilla.org/en-US/firefox/addon/710")extension in firefox to remove close from the menus. Undecorrating firefox would remove the close buttons. But these solutions would only discourage quitting rather than entirely disable it.

I'm sure there are a few better ways to do it.

---

