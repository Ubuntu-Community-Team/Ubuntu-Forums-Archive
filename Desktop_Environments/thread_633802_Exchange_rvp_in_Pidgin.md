---
title: "Exchange rvp in Pidgin?"
date: 2007-12-06
forum: Desktop Environments
---

### Post by eldaria on 2007-12-06
I was looking to install the Exchange plugin for Evolution and came across the rvp plugin for Pidgin.
Is this plugin for real?
I tried to convert my settings from my Windows Exchange messenger, but I can't get connected.
Anyone got this working, if so how did you do it?

This would be the last step to convert my desktop to 100% linux, since right now I have to run the messenger through Citrix, (a real pain, since I don't get any flashing when new messages arrive)

Regards.
Brian

---

### Post by phoenix817 on 2008-05-01
I ran across the same problem as you described here last year when I converted my workstation to be linux-based.  Our internal messenger was based on Exchange 2000 / RVP.  With a little bit of work, I was able to compile my own version of Pidgin using the librvp library, and it works flawlessly with our RVP-based IM network.

The library is available here:

[http://www.waider.ie/hacks/workshop/c/rvp/]("http://www.waider.ie/hacks/workshop/c/rvp/")

Some words of advice from my experience:
1.  Remove any existing versions of GAIM / Pidgin from your system.

2.  You will need to compile a version of Pidgin yourself including the librvp library.

3.  Make sure you get the source for the version of Pidgin recommended by the developer.  I tried using the latest pidgin baseline with the librvp plugin, and as expected, it didn't work.

4.  I had to re-add my contacts (didn't find any way to import them), but it was a minor annoyance for the benefit.


Additional Information:
- Microsoft Exchange 2000 IM protocol == RVP
- Follow the instructions provided by the librvp developer, and things will go fine.

good luck.

---

