---
title: "weird random problems"
date: 2009-03-14
forum: General Help
---

### Post by MikeBasilico on 2009-03-14
My computer has been acting up with 3 problems in particular

-When i start firefox, it starts with no window decorations, the i do a F11 for fullscreen and when i return it comes back

-Most fullscreen games and such dont work, when i launch i get "no supported signal"

-My folder's top row toolbar randomly went missing

-On a variety of apps i get blank menu items with just a "_" in place ot the respective text

I'm hoping this is just because my geforce440 is a little dated and not ubuntu's fault, because i would like to continue with ubuntu on my next machine

---

### Post by davec64 on 2009-03-14
compizconfig settings manager > workarounds plugin > untick legacy fullscreen support

That should sort Firefox when you start it again, not sure how it will help with your other problems! :)

---

### Post by davec64 on 2009-03-14
Just had a nother thought, for:

-My folder's top row toolbar randomly went missing

You could try reloading the Window Manager, this has worked for me in the past:

```
replace --emerald
```

Assuming Compiz is running.

---

### Post by MikeBasilico on 2009-03-14
Firefox problem solved! thanks, i dont know how that randomly happened

and turns out emerald got uninstalled somehow, im re intalling now

i hate computers haha

---

### Post by davec64 on 2009-03-14
> **MikeBasilico said:**
> 

i hate computers haha


Tell me about it! :):D

---

### Post by MikeBasilico on 2009-03-14
emerald did not fix the problem

<img src="http://img9.imageshack.us/img9/1655/97064344.jpg">

this is the problem, there is no "back" forward" "search" anything on the toolbar

---

### Post by davec64 on 2009-03-14
Under the View menu, you have got Main Toolbar, Side Pane etc ticked?

---

### Post by davec64 on 2009-03-14
Just another thought, if you disable desktop effects do things reappear?

Right click desktop >> Change Desktop Background >> Visual Effects Tab >> None

---

### Post by aextance on 2009-03-15
I've got very much the same problems. Will try the emerald thing for the display but have fixed the back/refresh arrow problem in firefox.

According to Mozilla it's a problem with the places.sqlite file.

I removed the profile.ini file in /home/(user)/.mozilla and that got it working but that did lose my bookmarks.

The thread below might work better for you:

[http://ubuntuforums.org/showthread.php?t=1083687&highlight=firefox+history]("http://ubuntuforums.org/showthread.php?t=1083687&highlight=firefox+history")

Loads of people are having this problem - if you search the Ubuntu forum with the term "firefox history" you'll find I've just posted this same thing on two other threads. My guess is that it's from a poorly executed upgrade.

---

