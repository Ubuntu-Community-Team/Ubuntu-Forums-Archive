---
title: "problems using ubuntu"
date: 2014-02-14
forum: Debian
---

### Post by beansdad on 2014-02-14
Been using Ubuntu since 2005 and found it to be very good with great improvements in user friendliness up to 2010. Since then it seems to be getting more & more difficult to use with a lot of problems being encountered.

Examples are the inability of 2011 onwards versions to easiy recognise my HP all in one scanner; updates repeatedly over-riding my settings; updates repeatedly causing crashes; Firefox insisting on starting with the last page accessed despite setting its preferences to always open on my home page; sound not automatically switching off the speakers when earphones are plugged in (reboot is necessary).

I've tried various versions of Ubuntu itself and Linx Mint and keep getting these annoying problems and am wondering if there may be some malicious activity involved to drive users away from Ubuntu!

Can anyone explain what is going on or recommend a user friendly alternative?

---

### Post by MG&amp;TL on 2014-02-14
Every release has its ups and downs - from the sounds of things, you are in the unfortunate position of getting more ups than downs.

I assure you that there is no 'malicious activity' involved in providing the distribution, there is in fact a considerable [effort]("http://qa.ubuntu.com/") to assure the quality of Ubuntu. The process is, however, not yet perfected.

If you want a distribution that has no Ubuntu influence, you could try Crunchbang (a Debian derivative designed to ease some of the perceived problems with Debian), OpenSUSE, or Debian itself, to name but a few. 'User-friendly' is rather subjective.

---

### Post by tgalati4 on 2014-02-14
Any time you have a working distro, that is precious and not something to be taken lightly.  When upgrading, I prefer to dual-boot--old distro and new distro.  It could take 6 months to a year to get everything ironed out.  So some patience is required to get everything working in the new distro, yet you have the backup distro when you need to get work done or you need a specific piece of hardware to work.  It's not a conspiracy, just a fact of the complexity of the many frameworks (layers) that modern linux is built on.  All of the frameworks are being updated and improved, but sometimes there are regressions--as you have discovered.

The lesson here is not to take a working distro and trash it, but have a strategy that always allows you to go back to the working distro and yet try out new things at the same time.

I use Linux Mint Mate because I like the Gnome2 interface.  Yes it is dated, but it works the way I expect it to.

Also, User-Friendly and customizable/fixable tend to be incompatible strategies.  So you have a choice to either learn the intricate procedures required to fix things--and there are a lot of resources out there--or accept User-Friendly and accept that things are more locked down and either work or don't.  There is no perfect distro, only one that you are more familiar with and are able to fix things so all of your hardware and software works the way you want.

Try going from WindowsXP to Windows8.whatever on your P4 and tell us your experiences.

In the meantime, ask a specific, single question about what you want to fix, because it is not clear from your original post.

---

### Post by buzzingrobot on 2014-02-14
Have to say I've seen none of those problems.

My HP printer requires an HP driver that is not installed by default.  Many HP printers do, as, well, on any Linux distribution. WIthout that driver, the printer config routine will likely seem to finish successfully, but the printer won't work.

I have found that a direct relation exists between changes made by third-party tools to the base system and update problems. Ditto PPA's. Replacing base components with foreign code from PPA's or elsewhere is sure to cause update issues unless you blacklist those packages from updating.

Does Firefox remember the other preference adjustments you make? If, by chance, your "home page" is a local HTML file of your making, I suspect Firefox wants its location prefaced with 'file:///').

Dunno about the headphone since I don't use them.

---

