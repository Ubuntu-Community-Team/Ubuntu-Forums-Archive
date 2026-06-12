---
title: "Problems with SCIM/Anthy"
date: 2009-05-07
forum: General Help
---

### Post by hugstrees on 2009-05-07
Edit: Solved.

Hey guys,

I posted this in the Tutorials section, but I wasn't sure if it was the appropriate place to ask, as it was 8.10-specific.

I'm having trouble using scim. I installed anthy from Administration->Language Support, but I can't seem to use it. The hotkeys don't seem to do anything. I can launch scim by typing scim-bridge in a terminal window. This gives me a tray icon, but it doesn't do anything. It's just taunting me. Any advice? Thanks!

Oh, I'm also using Jaunty, if that makes a difference. Is it a common problem?

---

### Post by fimblo on 2009-05-14
So how did you solve the problem? I've got exactly the same problem
(also running Jaunty).

Cheers
fimblo

---

### Post by fimblo on 2009-05-14
Aha, I found out how to fix it- you apparently write this in the terminal:

 im-switch -s scim

It worked for me!

---

### Post by chuugokujin on 2009-05-18
> **fimblo said:**
> Aha, I found out how to fix it- you apparently write this in the terminal:

 im-switch -s scim

It worked for me!

I have exact same problem, I can see the little keyboard icon for scim but it does nothing. 
I tried
im-switch -s scim

but it tells me
Error: no configuration file "scim" exists.
Error: No action taken.

how did you get this work?
Thanks

---

### Post by fimblo on 2009-05-24
Hmm, just by doing what I wrote. Have you tried clicking on the little icon in the corner? You can choose different layouts there.

---

