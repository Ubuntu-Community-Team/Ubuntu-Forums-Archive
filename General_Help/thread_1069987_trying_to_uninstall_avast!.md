---
title: "trying to uninstall avast!"
date: 2009-02-14
forum: General Help
---

### Post by Trim0 on 2009-02-14
is it necessary?
does anybody use AV software for ubuntu? if so what is the most effective?
i'm new to ubuntu, i went to add/remove option in the application menu but i couldn't locate avast...

also, is clam any good/necessary?

---

### Post by |{urse on 2009-02-14
I've only used avast/clamav on systems where you would slave a windows hard drive to the host linux system and scan it from there.

I'm pretty sure it's just 

*sudo apt*-*get* autoremove *avast* <---- replace avast with the actual name of the package

so far as its actual package name, im googling that at the minute so gimme a few and i should have it for you, in the meantime try the command as it is.

to install clamav (which is good but contestably unnecessary)

 *sudo apt*-*get* install clamav clamtk

---

### Post by Bablefish on 2009-02-14
It is also in the Snyaptic Package Manager, you may have to seach for it.

---

### Post by |{urse on 2009-02-14
did you install this as a deb from avasts site?

if so tell me what the output of 

**sudo dpkg --get-selections | grep avast**

gives you.

---

### Post by |{urse on 2009-02-14
looks like the command to remove it is

 sudo dpkg -P avast4server --force-remove

but dont do this just yet. Give me a minute.

---

### Post by |{urse on 2009-02-14
Got called into work...

Any progress on this?

---

