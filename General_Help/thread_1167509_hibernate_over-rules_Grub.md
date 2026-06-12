---
title: "hibernate over-rules Grub?"
date: 2009-05-22
forum: General Help
---

### Post by scradock on 2009-05-22
I have realised that if I hibernate one Ubuntu session, the next time I start the machine I get the Grub menu as usual, but whatever Ubuntu install I choose from the menu, the machine actually resumes the hibernated session.

This seems counter-intuitive to me: if the hibernated session is going to start up again anyway why do I get the Grub menu at all? I don't remember if I ever was able to choose to startup a DIFFERENT Ubuntu session from Grub, but now I notice that I can't it bugs me. It seems to me that after I specify one particular install Grub ought to be checking to see that the correct kernel is loaded, for instance, and not just blindly say "Oh, there's a hibernated session - we'll run that one instead of the one the guy asked for."

Any thoughts - has it always been this way and I've just noticed, or has something changed??? Or am I doing something wrong......

---

### Post by Locutus_of_Borg on 2009-05-23
why are you booting different kernels?

append noresume to any kernel lines you dont wish to resume from

---

### Post by egalvan on 2009-05-23
I have never used hibernation, so I have no experience,
merely an observation...

Hibernation uses the swap file...

Perhaps this is causing the problem?

---

### Post by Locutus_of_Borg on 2009-05-23
the problem is he is booting the same installation of his root file system, but with a different kernel

if you boot an actual different installation it doesnt do this

or at least never has for me

---

### Post by scradock on 2009-05-23
That's what I thought - but now, with Jaunty and Karmic installed, the hibernated one starts up even if I choose the other one from Grub. I mentioned the kernel because it seemd that Grub would be checking that it was using consistent files based on kernel numbering.

I haven't actually tried choosing the older kernel in the same install and seeing which one I get - my guess is that I would get whichever one was hibernated even if I chose the other one.

---

