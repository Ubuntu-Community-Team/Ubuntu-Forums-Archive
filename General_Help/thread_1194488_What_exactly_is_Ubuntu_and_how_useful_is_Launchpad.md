---
title: "What exactly is Ubuntu and how useful is Launchpad?"
date: 2009-06-22
forum: General Help
---

### Post by Andy06 on 2009-06-22
Ubuntu recently launched an initiative to fix 100 small, usability bugs that are easily fixable before the 9.10 release.

See here:

[https://launchpad.net/hundredpapercuts](https://launchpad.net/hundredpapercuts)

[http://arstechnica.com/open-source/news/2009/06/canonical-to-boost-ubuntu-usability-by-tackling-papercuts.ars](http://arstechnica.com/open-source/news/2009/06/canonical-to-boost-ubuntu-usability-by-tackling-papercuts.ars)

Now despite hearing a million horror stories about people being burnt on launchpad, I went ahead and filed a few bugs such as:

1.Back button being smaller (narrower) than other buttons in Nautilus toolbar despite being the most used and most important.

2.Eye of Gnome's inability to follow Nautilus's sorting mechanism. So basically you can only view pics in EOG sorted by Name and nothing else. You cannot view a folder full of pics sorted by modified date (or any criteria) in EOG in the correct order. Very basic and annoying oversight

3.No Image thumbnails/previews in GTK/Nautilus file selection and save as dialog boxes which makes it near impossible to select correct file from a folder full of >100 pics.


But all this got me thinking, what exactly is Ubuntu? From my limited knowledge, Ubuntu merely packages, polishes, integrates and then distributes the final product and then updates it by maintaining repositories. Canonical doesn't do any of the basic coding right? And Launchpad is merely for bugs in Ubuntu that Canonical can fix right?

So is there any point knocking at the doors in Launchpad and then  giving developers there a bad name for being high handed or arrogant when in fact they are actually helpless? Everything in Ubuntu is mainly to do with GNOME, and whatever isn't GNOME is usually a separate app. So 90% of the bugs, issues are non-ubuntu, is that right?

I need to get this right before I file 10-12 other small bugs there since I don't want to spam or flood the devs there but almost all of the bugs I see on launchpad are more to do with some part of GNOME and/or standalone apps. Are people merely wasting their time there by annoying the wrong people?

Thank you very much

---

### Post by Agent ME on 2009-06-22
A lot of the Ubuntu packages have further changes than merely being the upstream packages compiled. If you ever try compiling a package, you'd see there's a system in place to keep the Ubuntu (or Debian changes) separate from the upstream source.

Often the changes will also propagate upstream if it applies to more than just Ubuntu/Debian.

---

### Post by Polaris96 on 2009-06-22
try kde3

---

### Post by CatKiller on 2009-06-22
It's not accurate to say that the Ubuntu devs don't do anything, but it is a very small team compared to the resources that someone like Red Hat or Novell could muster. So it has to be focussed. They can't do everything. Upstart was an Ubuntu invention, as was the display configuration tool that could read Windows "monitor drivers" for relevant information. And obviously they make changes to some of the packages, and some of the changes propagate upstream.

Gnome doesn't use Launchpad and, it seems to me, they aren't that receptive to changes from downstream. It sometimes takes some work to get changes implemented in Gnome packages that doesn't have to be done for other packages, and sometimes they just refuse to concede that there's anything wrong (see, for example, gnome-screensaver).

But bugs that are reported on Launchpad do often get fixed upstream, and even if they are only fixed downstream by Ubuntu those changes can still be used by other downstream users.

BTW, the size of GTK buttons is theme-dependent. Both the forward and back buttons are the same size on every theme I've ever used.

---

### Post by Andy06 on 2009-06-23
> It's not accurate to say that the Ubuntu devs don't do anything, but it is a very small team compared to the resources that someone like Red Hat or Novell could muster.

> A lot of the Ubuntu packages have further changes than merely being the upstream packages compiled. If you ever try compiling a package, you'd see there's a system in place to keep the Ubuntu (or Debian changes) separate from the upstream source.

I think I came off wrong. I din't mean to belittle the work. I was in fact defending them sort of since if they aren't resposible for the basic coding, then they cannot be held responsible for the bugs. Purely from hearsay, Launchpad has a very bad reputation especially in the eyes of newbies and this could be unwarranted simply because the message isn't loud enough or clear enough that a majority of the faults posted on Launchpad are no fault of Ubuntus but rather of GNOME or standalone apps.

> try kde3

What? What has that got to do with anything? :D

> BTW, the size of GTK buttons is theme-dependent. Both the forward and back buttons are the same size on every theme I've ever used.

I don't know why even on Launchpad, the devs insisted on a screenshot. This is 100% reproducible so I don't know why there is still confusion. Even if it is theme dependent, the fact remains that with default configuration, the back button is smaller than the rest. Do not disable text below icons since that is not default and that is not the way first installs look. That is also not the way the majority of new users will have it.
With default configuration and ALL of the default themes that come with Ubuntu, the back button is mysteriously smaller than every other button on the toolbar (including redundant ones such as HOME). In fact even with custom GTK themes, I was unable to increase the size.
Please do explain to me if I am missing something. Here are some screenshots:

---

### Post by Legace on 2009-06-23
> **Andy06 said:**
> With default configuration and ALL of the default themes that come with Ubuntu, the back button is mysteriously smaller than every other button on the toolbar (including redundant ones such as HOME). In fact even with custom GTK themes, I was unable to increase the size.
Please do explain to me if I am missing something. Here are some screenshots:

That probably has something to do with the fact that "back" has 4 letters, while "forward" has 7.

Because the back button has an arrow [the black arrow, not the orange one] next to it (which is directly linked to the functionality of the Back button), it would be stupid to create a gap between them.

---

### Post by Andy06 on 2009-06-23
> That probably has something to do with the fact that "back" has 4 letters, while "forward" has 7.

Because the back button has an arrow [the black arrow, not the orange one] next to it (which is directly linked to the functionality of the Back button), it would be stupid to create a gap between them.

Or not. Since the "UP" has 2 letters in it and is yet bigger than the BACK button and the same size as every other button. Not to mention that having different button sizes for every button according to its label is bad design, you really aren't going to find that in any polished product. Design consistency is very very common in polished apps and UIs

If you noticed the black arrow beside the back button, you must have also noticed the same sort of black arrow also beside the forward button which also performs the exact same function, so that is not the issue either.

Neither is theming since the theme that comes by default as well as ALL other themes that come with the default installation have this issue, also dozens of other themes I tried from Gnome Look.

This is not just a matter of preference, the current toolbar in general and the back button in particular is in violation of Fitts law that deals with Human Interface and UI design.

---

### Post by Andy06 on 2009-06-23
Someone on launchpad pointed out why the design is the way it is.
It is indeed wrapped around the letters and the reason why UP isn't smaller than back for the same reason is that it is a different widget. (??)

This doesn't make things better though coz what I earlier thought to be a minor oversight is now quite simply and objectively, bad design by intention.

This is not a matter of personal preference but derived from basic principles of design. Right now design consistency is absent.

It is in violation of Fitts law. For users wanting a one line summary of the issue here and the line that best sums up the result of the GNOME HIG is:

Right now the most important toolbar button (the one used most often) in Nautilus is also the smallest.

I mean not only is it not the same size as the rest, it is actually smaller!

Are there any other GTK apps that have the same issue as Nautilus? I saw Epiphany and instantly realised why Mozilla decided to break the GNOME HIG, because they knew how to do design better. Mozilla hasn't just taken a slightly different approach with firefox, it is infact the complete opposite. Mozilla (and Opera) both prefer a larger back button (like in windows) or at least a similar sized one (for sake of consistency in other OSes), but Epiphany actually has it the other way round, the back button being the smallest. Hilarious :D

---

### Post by Tibuda on 2009-06-23
Offtopic: Mozilla didn't "decided" to break the GNOME HIG. They just don't care, as their main platform is Windows.

Ontopic: This is open source. You don't have to be the software developer to work with the source code and apply patches. That's what Canonical does. These patches can also be used upstream.

---

