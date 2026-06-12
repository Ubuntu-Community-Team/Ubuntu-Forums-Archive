---
title: "How to check last round of updates?"
date: 2011-01-20
forum: Desktop Environments
---

### Post by treacl on 2011-01-20
The last round of updates to 10.04 changed the initrd image, which I wasn't expecting.

How do I check the updates to make sure that this is in fact the expected behavior? I.e., how do I go back and check which updates were supposed to have been installed, check what was actually installed, and see which one modified the initrd and why?

Thanks,
treacl

---

### Post by Frogs Hair on 2011-01-20
System > Administration > Synaptic Package Manager > File > History

---

### Post by treacl on 2011-01-20
That is excellent. Answered a question I have been wondering about idly for a long time.

Once I had the list, I guessed that updating "mount" would have caused the OS to generate a new initrd image. I copied the initrd image to another directory, expanded the archive, and checked for "mount" in the image's /bin directory. Bingo: "Mount" is there. End of story?

---

### Post by treacl on 2011-01-20
[Duplicate post removed--sorry about that.]

---

### Post by treacl on 2011-01-20
[Duplicate post #2 removed--sorry about that.]

---

