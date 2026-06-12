---
title: "wesnoth won't open"
date: 2012-03-10
forum: Gaming &amp; Leisure
---

### Post by dunbrokin on 2012-03-10
Wesnoth will not open for me anymore. I have tried uninstalling and reinstalling all to no avail!


Battle for Wesnoth v1.8.6
Started on Sun Mar 11 11:38:21 2012

Unexpected characters at line start, value '$' at <unknown>:1

---

### Post by CivilizationII on 2012-03-11
> **dunbrokin said:**
> Wesnoth will not open for me anymore. I have tried uninstalling and reinstalling all to no avail!


Battle for Wesnoth v1.8.6
Started on Sun Mar 11 11:38:21 2012

Unexpected characters at line start, value '$' at <unknown>:1


This is really some great luck: you have automatically gained the best that wesnoth can do ;)

That said, this is maybe the occasion to switch to 1.10 release, the same boring game with some minor boring enhancement, don't worry you will not be lost.

On a little more serious tone, your problem is likely the initialization files, to reset them (so you will need to reconfigure wesnoth after applying this command):

> rm -Rdf ~/.wesnoth*

You will not need to do that if installing 1.10, because initialization files are not located in the same place.

Happy tedium ;)

---

### Post by dunbrokin on 2012-03-11
:}

thanks for that.....each to their own...

---

### Post by houseworkshy on 2012-03-11
It could be that some setttings are getting in the way so try "sudo apt-get purge" when you uninstall, this will remove those too.  Then try reinstalling again.

---

### Post by CivilizationII on 2012-04-19
> **dunbrokin said:**
> :}

thanks for that.....each to their own...


Never mind for so few ;-)

---

### Post by gadha1998 on 2012-07-19
I also have wesnoth 1.10 on ubuntu 12.04 . I have the same problom and I try'd re installing 2 times. Still it wot open when i click it. I have try'd to open it via /usr/game folder  It stll wont open. :confused:

---

