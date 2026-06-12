---
title: "No messaging services in Kopete?!?"
date: 2006-08-29
forum: Desktop Environments
---

### Post by clintonthegeek on 2006-08-29
Hey Everyone!

I've just installed a fresh install of Ubuntu on a computer, and decided I wanted to install Kopete.

So, rather than use the outdated version from the repositories, I "dpkg -i"'d Kopete 0.12.1 (and the dependency libortp_0.7.1-0) from [KDE-Apps]("http://www.kde-apps.org/content/show.php?content=41143").

Well, I started it up, and guess what I see?

[IMG]http://img95.imageshack.us/img95/7276/kopetenoservicesmw7.png[/IMG]

There are no messaging services to pick from! And the Next button goes inactive once you try to click it, of course. 

So, I promptly "dpkg -r kopete" to get rid of it, and "apt-get install kopete" to install the older repo, but I STILL get no services.

And here's what the "Configure Kopete..." page looks like.

[img]http://img135.imageshack.us/img135/2739/kopetenoservices3xo0.png[/img]

For background, I've installed kde-base, and am now installing apps as I need them vs. just installing kubuntu-desktop, which is why Kopete wasn't installed to begin with.

Any help would be great!

-Clinton

EDIT: Okay... silly problem. I just upgraded to KDE 3.5.4 and now everything works peachy. :)

---

