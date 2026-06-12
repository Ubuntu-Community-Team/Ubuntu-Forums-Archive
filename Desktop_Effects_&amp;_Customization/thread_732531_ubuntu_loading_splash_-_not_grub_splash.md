---
title: "ubuntu loading splash - not grub splash"
date: 2008-03-23
forum: Desktop Effects &amp; Customization
---

### Post by musikgoat on 2008-03-23
Hey folks, 

I'm looking to fix a small issue.   I've been using Ubuntu for a while and back with either dapper or edgy there was a very attractive loading screen that would show the ubuntu name and the loading lines of the various services.

Later, I believe on feisty,  they took away that part, in a grub parameter called quiet splash, which stopped showing the services loading, but still had the image.

Ever since gutsy and now hardy beta,  I am able drop the quiet parameter from defoptions so i have the following
# defoptions=splash

but this only shows the "pretty" splash for part of the loading and goes to the normal system services loading after about 30 seconds...

I'm wondering if anyone may know why.
I will try to upload a youtube video showing what I mean, because I may not be describing it well enough.

---

### Post by musikgoat on 2008-04-10
bump...  Anyone familiar with the ubuntu splash loading screen?   It shows the last option as "... resume devices"...   and then goes to the normal command line where it shows, Finding boot files needed, or something to that effect.

In the past, all that now shows in the command line also used to display in the nice graphical loading screen.

If it helps I'm running 64bit Hardy Beta currently.

---

### Post by StooJ on 2008-04-10
So are you looking to suppress the text altogether?

I may be wrong, but I think the text only shows when there are unexpected or abnormal outputs (something not loading properly)

I only get text output when the network is playing up (it's incorrectly wired, I think)

---

