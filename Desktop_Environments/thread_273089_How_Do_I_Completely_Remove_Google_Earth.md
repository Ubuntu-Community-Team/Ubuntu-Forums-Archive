---
title: "How Do I Completely Remove Google Earth?"
date: 2006-10-07
forum: Desktop Environments
---

### Post by Mark76 on 2006-10-07
I downloaded it from Automatix to have a look, but I don't really want to keep it.

I've tried sudo apt-get remove google-earth, but it's not worked.

---

### Post by aldegaz on 2006-10-07
"its not worked" ??

Could you try to explain a little bit more?

What if you open the terminal and type: google-earth
Will it still load?

---

### Post by Mark76 on 2006-10-07
S'okay, I found the uninstall option in the folder.

---

### Post by hvtuananh on 2008-01-15
You must manually remove personal data in /home/{username}/.google-earth

---

### Post by peter3 on 2008-05-20
And what do you do when the response to the # ./uninstall looks like this?
root@heron:/opt/google-earth# ./uninstall 
Could not find a usable uninstall program. Aborting.

Thanks,
peter3

---

### Post by firefeather on 2008-05-21
> **Mark76 said:**
> I downloaded it from Automatix to have a look, but I don't really want to keep it.

I've tried sudo apt-get remove google-earth, but it's not worked.

See [this page]("https://help.ubuntu.com/community/GoogleEarth#head-c1c56a1bb75c740a3a33269b946d931272b451f6") on the Ubuntu Wiki! :) I use the Ubuntu Wiki as my first resort for finding answers to my questions, and it certainly comes through here.

Automatix, as far as I know, doesn't install things using the repositories, so using "sudo apt-get remove" on them won't work. One reason they recommend against Automatix, but some people swear by it, so whatever floats your boat, I guess....

**EDIT:** Oops...realized this thread was really old although the last few posts weren't. Sorry about that.

---

