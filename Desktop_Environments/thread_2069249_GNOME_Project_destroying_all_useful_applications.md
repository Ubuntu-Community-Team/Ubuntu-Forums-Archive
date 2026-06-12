---
title: "GNOME Project destroying all useful applications"
date: 2012-10-10
forum: Desktop Environments
---

### Post by decomp on 2012-10-10
Umm I can't configure my printers anymore. there's no settings. also disk utility is now useless and only lets you delete or create partitions.

These both used to be useful applications.

What happened?

---

### Post by jbicha on 2012-10-11
Try running system-config-printer.

Things are in transition; "Disks" as the tool is called now is quite a bit more useful in 12.10.

---

### Post by linuxvstheworld on 2012-10-11
> **jbicha said:**
> "bit more useful in 12.10."

Since you mentioned Ubuntu 12.10, when is going to be released?

---

### Post by on2mars on 2012-10-11
The release date is the 18th.

---

### Post by decomp on 2012-10-12
> **jbicha said:**
> Try running system-config-printer.

Thanks! 

Although I don't see how having to use the run dialog is an improvement.

> **jbicha said:**
> 
Things are in transition; "Disks" as the tool is called now is quite a bit more useful in 12.10.

cool I guess but why replace a usefull app with a placeholder? 

what about those of us who don't plan on using 12.10? 12.04 is supposed to be LTS.

Things are always in transition. Shoudn't a usable OS be a priority?

---

### Post by jbicha on 2012-10-12
> **decomp said:**
> what about those of us who don't plan on using 12.10? 12.04 is supposed to be LTS.

Things are always in transition. Shoudn't a usable OS be a priority?

GNOME doesn't have a LTS cycle which makes things difficult for Ubuntu. There are also opposing pressures: some people like me want the latest GNOME release (i.e. 3.4 all the way for 12.04 LTS); others wanted to hold back and use GNOME 3.2.

Sticking with 12.04 is the right answer for those who value stability over features. Disks in particular can't be officially backported to 12.04 as it needs udisks2 which is only in 12.10 and higher.

---

### Post by decomp on 2012-10-12
> **jbicha said:**
> Disks in particular can't be officially backported to 12.04 as it needs udisks2 which is only in 12.10 and higher.

That means that we will never get the new application and will be stuck with a broken utility. 

Why not just leave the existing application in place for 12.04?

Thanks for your informative replies.

Any suggestions how I can safely remove my external HD? 

Disk Utility was the only way.

---

### Post by cmcanulty on 2012-10-13
To get the printers config to show just add indicator applet complete to menus. Then you click printers and get the old options. Why they are gone from system settings -printers is I think the idiotic new style of making everything bare bones and removing functionality in order to have more useless empty space

---

