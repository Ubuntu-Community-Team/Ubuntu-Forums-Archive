---
title: "Clickless interface"
date: 2009-11-20
forum: Desktop Environments
---

### Post by mylh on 2009-11-20
Hi All.

I'm using kubuntu on a laptop. I wonder if there is a way to enable clickless interface for KDE, something like in Lancelot launcher widget. I found it very convinient to activate elements without removing my finger from touchpad ;) I also set up raising windows on hovering and it is also works very good for me. Any ideas? Is there a way to emulate click on a touchpad on changing pressure level?

---

### Post by Zorael on 2009-11-20
> **mylh said:**
> Is there a way to emulate click on a touchpad on changing pressure level?
You mean, to make the touchpad register it as a tap if you just briefly press it harder? I don't believe the Synaptics driver currently supports this.

The Synaptics bug tracker is [here](https://bugs.freedesktop.org/buglist.cgi?query_format=advanced&short_desc_type=allwordssubstr&short_desc=&product=xorg&component=Input%2Fsynaptics&long_desc_type=allwordssubstr&long_desc=&bug_file_loc_type=allwordssubstr&bug_file_loc=&status_whiteboard_type=allwordssubstr&status_whiteboard=&keywords_type=allwords&keywords=&bug_status=NEW&bug_status=ASSIGNED&bug_status=REOPENED&emailassigned_to1=1&emailtype1=substring&email1=&emailassigned_to2=1&emailreporter2=1&emailqa_contact2=1&emailcc2=1&emailtype2=substring&email2=&bugidtype=include&bug_id=&chfieldfrom=&chfieldto=Now&chfieldvalue=&cmdtype=doit&order=Importance&field0-0-0=noop&type0-0-0=noop&value0-0-0=). You could post it as a wishlist/enhancement item. Product: **xorg**, Component: **Input/synaptics**. ([guidelines](https://bugs.freedesktop.org/page.cgi?id=bug-writing.html))

---

### Post by kerry_s on 2009-11-20
did you look in the kde mouse settings? in gnome there's a accessibility feature.

---

### Post by Zorael on 2009-11-20
Oh, right, kmousetool.

It should be under Utilities in your menu.

---

