---
title: "No Window menu entry in konqueror"
date: 2005-10-26
forum: Desktop Environments
---

### Post by jabster on 2005-10-26
Hi.

Could someone please tell me why there's no "Window" menu item in konqueror? Running a fresh install of Breezy.

It is much more difficult to open the Navigation Panel without it.

On a somewhat related note, why can't I load View Profiles from inside konqueror? I have to have View Profiles as a K menu item.

-john

---

### Post by ltmon on 2005-10-26
Hi,

Konqueror in Breezy was shipped with an ultra-simple view profile by default (missing the "Go" menu as well).

Maybe you could try loading it with:

konqueror --profile profilename

... where profilename is the name of a more vanilla view profile (not erally sure what the profiles are though, maybe "webbrowsing"?) and then adjusting the available profiles using the gui from there.  I'm not at home so I can't check myself.

L.

---

### Post by jabster on 2005-10-27
[QUOTE=ltmon]Hi,

Konqueror in Breezy was shipped with an ultra-simple view profile by default (missing the "Go" menu as well).

Maybe you could try loading it with:

konqueror --profile profilename

... where profilename is the name of a more vanilla view profile (not erally sure what the profiles are though, maybe "webbrowsing"?) and then adjusting the available profiles using the gui from there.  I'm not at home so I can't check myself.

L.[/QUOTE]

No good. In fact, I'm reusing my old view profiles from my previous gentoo install.

I have no Window menu, and can't edit/access view profiles from within konq.

-john

---

### Post by jabster on 2005-10-28
Found this FAQ entry:
[http://www.kubuntu.org/faq.php#konqueror](http://www.kubuntu.org/faq.php#konqueror)

Yea.

Really don't understand that design decision tho.

-john

---

