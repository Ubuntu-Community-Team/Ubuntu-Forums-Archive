---
title: "Touchpad and Mozilla/Firefox"
date: 2005-03-09
forum: Desktop Environments
---

### Post by Tehanu on 2005-03-09
I think this is where I need to ask this question.

I've installed Ubuntu on my laptop, and I love it. However, with the currently installed firefox/mozilla, whenever I move my finger from right to left, on the bottom of my touch pad, it goes back a page. And, if I move up or down on the right side, the scroll goes crazy.

I'm sure this is nice for some people, but I hate it. And I can't figure out how to turn it off. Is there a way?

I tried installing FireFox 1.0.1, but it does the same thing, so I figure it's a Gnome thing that I can't figure out..

Thanks for the help, guys!

---

### Post by ember on 2005-03-09
I guess it's not an issue with firefox, but with the touchpad. I have the same problem - I'll look into it, maybe I'm able to give a solution

---

### Post by Tehanu on 2005-03-09
I guess I should have done this before making a new thread. :P But, maybe my title will help others in the future to find the answers to which they seek.

DoubleDangerClub has already covered why this might be happening, and gives a fix in this thread:

[http://ubuntuforums.org/showthread.php?t=3994](http://ubuntuforums.org/showthread.php?t=3994)

So, yes. :)

---

### Post by wernst on 2005-03-10
[QUOTE=ember]I guess it's not an issue with firefox, but with the touchpad. I have the same problem - I'll look into it, maybe I'm able to give a solution[/QUOTE]

This annoyed me too. For about 10 minutes before it occured to me to Google "firefox horizontal scroll back," where I found:

In Firefox, type about:config into the address bar and hit return. This gives you a list of all possible configuration options. The ones we want are those that start with mousewheel.horizscroll.withnokey. Make the following changes by double-clicking the appropriate option in the list:

    * mousewheel.horizscroll.withnokey.action => 0
    * mousewheel.horizscroll.withnokey.sysnumlines => true

Bingo! Problem solved.

-Warr

---

### Post by MetaMorfoziS on 2006-11-10
Oh! thanx! it's cool! :D

---

