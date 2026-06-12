---
title: "The effects of a locale change"
date: 2008-03-01
forum: Desktop Environments
---

### Post by Magatsu Taito on 2008-03-01
So, I have been using TinyFugue for some time now, but I could never use åäö. Later on, I found out that my computers default locale was an english one, and even though I could use åäö in my terminal and such, TF never could.

So, I changed locale, to the swedish one, and voila, problem solve, but more problems were created. First of all, why the hell does it need to have everything in Swedish? It is disgusting, in my opinion. I want everything as it used to be, but with the swedish locale in use.

Second, I have a partition named köttbullen. This works great when used with Nautilius, but when trying to attend this partition with gnome terminal, or any other terminal for that matter, it looks like this:

2008-02-23 14:29 kÃ¶ttbullen

I who thought that using the swedish locale, would make it more usable with swedish letters? So instead of having a nice english layout, which works with every swedish letter, and a non working tf one. I have an awful swedish layout, which doesn't understand swedish letters, but a non working tf one. Thank you, thank you very much.

EDIT:
It seems as it is not the understanding of the swedish letters that are the problem, but something else. I tried creating a file called ååääöö with nano, which worked perfectly. It seems that when I created the partition called köttbullen, it was created with another locale standard? I do not know, because åäö seems to work fine, except for köttbullen. Still, natutilius sees it as Köttbullen, and not kÃ¶ttbullen, so I am not sure where the problem lies.

---

### Post by Bubbel on 2008-03-01
Hi,

I had the same problem with my Dutch locale. There are two things to keep in mind: The Locale and the keyboard layout.

The Locale can be customised by editing (as root) /etc/default/locale
I do not have the Swedish locale at hand, but here is my config:
```
LANG="en_US.UTF-8"
LANGUAGE="en_US:en"
LC_TIME=nl_NL.UTF8
LC_NUMERIC=nl_NL.UTF8
LC_MONETARY=nl_NL.UTF8
LC_PAPER=nl_NL.UTF8
LC_NAME=nl_NL.UTF8
LC_TELEPHONE=nl_NL.UTF8
LC_ADDRESS=nl_NL.UTF8
LC_CTYPE=nl_NL.UTF8
LC_COLLATE=nl_NL.UTF8
LC_MEASUREMENT=nl_NL.UTF8
```
You can see the locale stays en_US, while all others (especially dates & measurement) are Dutch.

The second issue is the creation of complex characters. That part you can find under the System ->Preferences->Keyboard.
There you can add your keyboard Settings. For me it was a US English. But that is half of it. You can set the variant if needed. The Alternative International variant gave me the desired result.
Play a bit with it, and remember the result for furture installations. (I forgot mine half a dozen times, before I got it right..)

Good luck. Bubbel

---

