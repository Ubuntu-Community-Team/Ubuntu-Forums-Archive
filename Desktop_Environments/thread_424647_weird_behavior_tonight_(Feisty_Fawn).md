---
title: "weird behavior tonight (Feisty Fawn)"
date: 2007-04-26
forum: Desktop Environments
---

### Post by jammodotnet on 2007-04-26
here is a screen shot of an error i can reproduce 
[http://img135.imageshack.us/img135/804/070426202002qp0.png](http://img135.imageshack.us/img135/804/070426202002qp0.png)

i clicked the little SHOW DESKTOP icon? bottom left side?
its very odd.

also, if you see next to my trashcan, where it suPPOSED to show my Workspace1/Workspace2 icones, there is nothing. it's like it's not even loading?

the error states "your window manager dos not support the show desktop button, or you are not running a window manager."

even weirder, if all my launched windows are NOT visible on the lower task bar. and the top task bar disappears when windows are maximized.

i have NOT installed any software since my successful update a few nights ago.
i'm afraid of coming home and NOT being able to boot.
i did a search on the above mentioned error, not alot came up.

here is another screen:
[http://img254.imageshack.us/img254/4898/070426203315xb9.png](http://img254.imageshack.us/img254/4898/070426203315xb9.png)

---

### Post by shae on 2007-04-26
Just restart x, metacity probably crashed.  It should be no big deal.

---

### Post by llamakc on 2007-04-26
Why not just restart metacity?

---

### Post by netsurfau on 2007-04-26
This is identical the the issue I'm having.

It seems to be related to your user profile.  I logged out then back in as root & the prob
had gone.  Now just trying to find out if profile can be repaired or not.

---

### Post by jammodotnet on 2007-04-27
Thank you.
This solved my problem.
[http://ubuntuforums.org/showthread.php?p=2544698#post2544698](http://ubuntuforums.org/showthread.php?p=2544698#post2544698)

:)

---

### Post by firfin on 2007-04-27
> **llamakc said:**
> Why not just restart metacity?

Nice idea. How?

I'm experiencing the same problem. For some ppl deleting the session worked (see [this thread ]("http://ubuntuforums.org/showthread.php?p=2544883#post2544883") )
[COLOR="LightBlue"]
I will try that soon and let you know.[/COLOR] Well removing ~/.gnome/session did the trick for me. I can manage my windows again. :-)
Still wondering what caused this though

---

### Post by Neobuntu on 2007-04-27
In Kubuntu, rebooting doesn't fix it, changing theme doesn't fix it.

It's a good thing to know [ALT]+[F2] huh?

---

### Post by jammodotnet on 2007-04-27
> **Neobuntu said:**
> In Kubuntu, rebooting doesn't fix it, changing theme doesn't fix it.

It's a good thing to know [ALT]+[F2] huh?

for the uninformed (ME!) what does ALT + F2, do?

---

