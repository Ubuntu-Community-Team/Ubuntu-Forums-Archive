---
title: "Screen lock: Access denied despite password"
date: 2005-10-22
forum: Desktop Environments
---

### Post by ReadAloud on 2005-10-22
Hi all,

when I lock my screen in GNOME (System -->Lock Screen) and then try to get back to work, the screen lock gives me an "Access denied", although I have correctly entered my password.

I am running Breezy on an IBM ThinkPad T42, which usually works well with GNU/Linux. And yes, I have entered my password correctly. More than once.

This problem started when I dist-upgraded from Hoary a few days ago. Google seems to have no answers to this. Any help would be much appreciated.

---

### Post by piggyaugu on 2005-10-22
[QUOTE=ReadAloud]Hi all,

when I lock my screen in GNOME (System -->Lock Screen) and then try to get back to work, the screen lock gives me an "Access denied", although I have correctly entered my password.

I am running Breezy on an IBM ThinkPad T42, which usually works well with GNU/Linux. And yes, I have entered my password correctly. More than once.

This problem started when I dist-upgraded from Hoary a few days ago. Google seems to have no answers to this. Any help would be much appreciated.[/QUOTE]


I've met this once. It was due to my confusing frence/US keyboard layouts. Try to check that.

---

### Post by ReadAloud on 2005-10-22
> I've met this once. It was due to my confusing frence/US keyboard layouts. Try to check that.

Nope, unfortunately that does not solve it. I have deleted all but one keyboard layouts I was using, but the problem persists. Thanks, though.

btw: CapsLock is not part of the problem either.

Update: 
I just re-installed the gnome package, but to no avail. That eliminates another hypothesis...

---

### Post by ReadAloud on 2005-10-22
Ok, just found this post by **aulin** which solved the problem:
> 
I am not sure what the password is but a way around the issue is to do ctrl-alt-f1 then at the prompt type:

sudo passwd ubuntu

and make the password what ever you want. Then go back to the X screen with ctrl-alt-f7 and log back in


([http://ubuntuforums.org/archive/index.php/t-26447.html](http://ubuntuforums.org/archive/index.php/t-26447.html))

Although this only means re-stating the user passwd, which I believe I had done before, it worked. Thanks, **aulin**!

---

