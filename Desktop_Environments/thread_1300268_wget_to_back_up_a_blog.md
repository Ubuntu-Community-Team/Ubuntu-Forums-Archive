---
title: "wget to back up a blog"
date: 2009-10-24
forum: Desktop Environments
---

### Post by raywood on 2009-10-24
I'm using this command to back up a private, passworded blog:

```
wget -mrc --convert-links --progress=dot --http-user=[user name] --http-password=[password] --level=3 --page-requisites --no-parent [URL]
```

That command gives me repeated instances of this:

```
Read error at byte 15928/15467 ((null)).  Retrying.
```

What's wrong with my command?

---

### Post by cilynx on 2009-10-25
Does the blog use standard HTTP Authentication for it's password?  Most blog engines have custom, cookie-based session management, which does not place nice with tools like wget.  That's not to say that it can't be done; but it definitely isn't trivial.

---

### Post by raywood on 2009-10-25
I dunno.  That may be it.  Thanks.  It's always a relief to know when it's finally time to give up and admit defeat.

I've been taking the approach of listing a maximum number of posts per webpage and just making a copy of the webpage.

---

### Post by cilynx on 2009-10-25
Is this your blog that you're backing up?  (e.g. do you have access to the shell of the machine the blog runs on?)

---

