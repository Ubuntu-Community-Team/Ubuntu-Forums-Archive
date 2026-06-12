---
title: "Thunderbird - symbolic link problem"
date: 2009-04-30
forum: General Help
---

### Post by Bruce M. on 2009-04-30
Hi folks,

I have a problem, I'm running two linux distros and using Thunderbird in both. I want to make a symbolic link so Thunderbird in Dreamlinux can use Xubuntu's Thunderbird settings for the mail. I have years of emails in Xubuntu ~/.mozilla-thunderbird but Dreamlinux uses ~/.thunderbird for it's setting (as well as other distros).

A symbolic link just creates the "link" as a subfolder of ~/.thunderbird

I tried using:
```
thunderbird -profilemanager
```
to create a new profile, but it immediately sets up and uses: ~/.mozilla-thunderbird

How can I get Xubuntu's Thunderbird to use ~/.thunderbird instead of ~/.mozilla-thunderbird?

At least then I could create a proper symbolic link.

Have a nice day.
Bruce

---

### Post by kanikilu on 2009-04-30
You can move your profile anywhere you want, you just have to tell thunderbird where it is. Check out this article:

[http://kb.mozillazine.org/Moving_your_profile_folder](http://kb.mozillazine.org/Moving_your_profile_folder)

Although, I'm confused as to why the symbolic link didn't work, since that would be the easier way to do it...

How did you try to create the link? For directories, I think the syntax is:
```
ln -s /path/to/original /path/to/link
```

---

