---
title: "Firefox deleting cookies without consent"
date: 2009-05-12
forum: General Help
---

### Post by mike0020 on 2009-05-12
For some reason Firefox keeps deleting my cookies even though I have nothing set to delete them. I want to stay logged into a site but Firefox keeps clearing my cookies every time I close it.

---

### Post by rushmobius on 2009-05-12
Does the same behaviour occur with another browser or OS?

It may be the web site setting the cookie to expire when your session ends.

---

### Post by mike0020 on 2009-05-12
> **rushmobius said:**
> Does the same behaviour occur with another browser or OS?

It may be the web site setting the cookie to expire when your session ends.

I'm not sure but I know the sites don't delete the cookie right away, it happens to every site.

---

### Post by broken sword on 2009-05-14
any new information on this issue? this has started happening to me.

I've made sure that all my settings are correct, i.e. cookies retained untill they expire. I'm also having an issue with my open tabs. Firefox doesn't save my tabs. I also can't set a home page, it only loads a blank page.

I've tried some light troubleshooting. Will be trying more later, hoping that someone else found a way to fix this.

---

### Post by s.fox on 2009-05-14
Hi,

On a site I maintain I have a script that creates a cookie when the user logins in.  I then have another script delete the cookie when they logout.  Perhaps this is happening to you.

-Ash R

---

### Post by broken sword on 2009-05-14
> **Ash R said:**
> Hi,

On a site I maintain I have a script that creates a cookie when the user logins in.  I then have another script delete the cookie when they logout.  Perhaps this is happening to you.

-Ash R

I appreciate the answer, but that's not what's happening. All of my cookies expire, even the ones that were "permanent".

I may just try a re-install, and see if that help.s

---

### Post by _Purple_ on 2009-05-14
Try to rename ~/.mozilla and see if you still have the problem.

---

### Post by mike0020 on 2009-05-16
> **_Purple_ said:**
> Try to rename ~/.mozilla and see if you still have the problem.

Unfortunately that didn't work for me.

---

### Post by Legace on 2009-05-16
Open Firefox, Edit -> Preferences -> Privacy.

Make sure Cookies are kept "Until they expire" and that "Always clear my private data..." is NOT checked.

---

### Post by mike0020 on 2009-05-16
> **Legace said:**
> Open Firefox, Edit -> Preferences -> Privacy.

Make sure Cookies are kept "Until they expire" and that "Always clear my private data..." is NOT checked.

I have the cookies set to that however I have 'always clear my private data' checked, but on the options cookies is not one of the things to be deleted. I've tried disabling that in the past but they would still delete my cookies every time I close Firefox.

---

### Post by LordMarshall on 2009-05-19
I can confirm your problem. The same here, and I have no clue how to change it :(

I hope someone figures it out.

---

### Post by mike0020 on 2009-05-25
Has anyone found a fix for this?

---

### Post by mike0020 on 2009-06-20
I'm still having this problem, even on the latest version of Firefox. If anyone has found a way to fix this please post.

---

### Post by BFG on 2009-11-04
Now I'm getting it too.  Everything set correctly, and checked advice here:
[http://ubuntuforums.org/showthread.php?t=1291943&highlight=firefox+cookies](http://ubuntuforums.org/showthread.php?t=1291943&highlight=firefox+cookies)

Changing the profile did help for me. So, I changed it back and then renamed the following files:
cookies.sqlite
cookies.sqlite-journal

That seems to have worked so far.

---

