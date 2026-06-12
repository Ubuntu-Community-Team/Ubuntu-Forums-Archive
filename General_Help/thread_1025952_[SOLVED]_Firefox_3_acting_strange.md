---
title: "[SOLVED] Firefox 3 acting strange"
date: 2008-12-30
forum: General Help
---

### Post by Polomint01 on 2008-12-30
Ubuntu 8.04 in wubi.

Firefox 3 todays has started to act strangely.

Sometimes it will start ok, othertimes it will not start at all, and strangest of all it starts but nearly all my extensions have gone.

The add on window opens telling me that a new add on has been added.

I noticed at first it had added 3 new add ons now it is saying 4 new add ons, I cannot see anything new added.

It opens on the language tab to tell me this, and states I have Firefox(en-GB) ver 3.0.1 and Xulrunner(en-GB) ver 1.9.0.1 are present.

Also on the about firefox window I have some Thai political statement,is this normal?

Can I restore Firefox back to a fully working state, any help welcome.

---

### Post by namdung on 2008-12-30
Things to try out in order:

1. Try removing the Firefox add-ons.

2. Reconfigure Firefox in terminal
```
sudo dpkg-reconfigure firefox
```

3. Reinstalling Firefox from *Synaptic Package Manager*.

4. Install stable Hardy Heron 8.04.2 LTS, which is releasing on 1/1/2009.

---

### Post by Polomint01 on 2008-12-31
Reinstalling firefox did the trick, it seems.

Thanks for all your help.

---

