---
title: "Firefox Login Issues"
date: 2006-08-15
forum: Desktop Environments
---

### Post by Shampyon on 2006-08-15
About a week ago I noticed something very odd happen. Whenever I enter my username/pass and try to log in to MySpace or eBay, instead of going to my pages the login page simply refreshes. 

Also, I'd had cookies saved with the Cookie Culler Extension for certain forums, and found that they were no longer workingt - I have to now log in manually every time (user/pass autofill still works, though).

I've tried logging in to MySapce and eBay through Opera, and there's no problem.

PS: Love that "Check If Already Posted" option!

---

### Post by JerMe on 2006-08-15
Try to uninstall and reinstall firefox?

```
sudo apt-get remove --purge firefox && sudo apt-get install firefox
```

---

### Post by Shampyon on 2006-08-15
I just tried reinstalling simply using Synaptic, to keep my profile intact.
No dice.
I'm gonna try it your way now. Here's hoping it works!

*Update:* Aww, poop. No dice.
I'm wondering if it may be because of an extension, but I'm not sure which one it could be. None of the ones I've recently installed have anything to do with cookies, either.

Oops, I forgot. That's another site that won't work through FireFox any more: Gmail. It tells me my browser is rejecting coockies, even though it clearly isn't.
[I]
Update 2:[/I] Bull####. Bull-####ing-####. All that worry, all that searching and it was the simplest thing in the whole damn world.
Preferences>>Privacy>>Allow Sites To Set Cookies {Exceptions}.
Someone using my computer had set Firefox to reject cookies from half of my most-visited sites! When i find out, heads will roll, I assure you.

Thanks for the help. Hoppefully I won't have to ask for help to hide the bodies :P

---

### Post by Greycloak on 2006-08-16
I'm having the same problem but there aren't any sites listed in exceptions.  It seems to only happen on one forum that I visited.

---

### Post by mscman on 2006-08-16
That's why you don't let people use your computer. ;)

Glad you got it figured out!

---

