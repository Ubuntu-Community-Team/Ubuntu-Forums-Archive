---
title: "Ncurses (aptitude/owl/etc) won't display correctly in screen"
date: 2005-11-07
forum: Desktop Environments
---

### Post by jasonc on 2005-11-07
I'm having problems with screen and aptitude, owl, and other ncurses apps, they look corrupted.  Anybody ever see this before?

[[IMG]http://img138.imageshack.us/img138/4641/broken8ia.th.jpg[/IMG]](http://img138.imageshack.us/my.php?image=broken8ia.jpg)

---

### Post by Remmelas on 2005-11-08
a screenshot would help to identify your issue, but, I wonder if you've changed to a custom console font by chance?

---

### Post by jasonc on 2005-11-08
[QUOTE=Remmelas]a screenshot would help to identify your issue, but, I wonder if you've changed to a custom console font by chance?[/QUOTE]

Changing the font on the gnome-terminal does not fix the issue.

---

### Post by Remmelas on 2005-11-09
my apologies, i had assumed you was talking about the native console, not a graphical one...

---

### Post by grotesmurf on 2007-02-15
Maybe a little late to post a solution, but I just installed dapper and had this same problem.

Tried to find a solution on the internet, but maybe almost no one uses ubuntu with the screen program... Because I did not find a solution.... Although it is wierd because all ncurses based applications also behave strange in every terminal (so also when screen is not used)... did not find anyone complaining about it.

After trying several different things I finally fixed this issue. There seems to be a problem with the UTF8 locales installed by default.

Here is the way to check and change your locale settings:

To check which locale you currently have as your default just run: locale

Changing the default locale is a little different on Ubuntu compared to most Linux distros, these are the steps we needed to go through to get it changed:

Add the locale to the list of 'supported locales' Edit /var/lib/locales/supported.d/local and add the following line: en_GB ISO-8859-1

Regenerate the supported locales Run sudo dpkg-reconfigure locales

Change the default locale Edit /etc/environment and ensure the LANG and LANGUAGE lines read as follows: LANG="en_GB" LANGUAGE="en_GB:en"

Just logout your system and back in again and your problems are solved.

Edit: well not all of them of course... just the problem with the strange behaviour of ncurses based apps.

---

