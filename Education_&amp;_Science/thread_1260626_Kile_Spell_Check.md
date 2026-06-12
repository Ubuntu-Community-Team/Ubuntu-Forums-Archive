---
title: "Kile Spell Check"
date: 2009-09-07
forum: Education &amp; Science
---

### Post by pvfloripa on 2009-09-07
Hi all,

In Ubuntu 8.10, I am trying to use the spell check in Kile, but it doesn't work. When I go to Tools->Spelling, I get the pop-up message:

"The spelling program could not be started. Please make sure you have set the correct spelling program and that it is properly configured and in your PATH"

In other threads people say that one should install Aspell and Kcontrol. I already have Aspell, but Kcontrol is not available in the repository anymore. Are there any workarounds to get this working?

Thanks!!

---

### Post by nateperson on 2009-09-08
Try typing:

echo $PATH

in the command line.  That will give you your paths.  If the path to the folder that contains aspell isn't in there type:

export PATH=/location/of/aspell:$PATH

and test it again.  If it works add the export command to your .bashrc

Sorry if that doesn't work, I can't replicate the problem...

---

