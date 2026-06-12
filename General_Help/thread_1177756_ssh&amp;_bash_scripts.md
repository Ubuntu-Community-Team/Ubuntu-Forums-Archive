---
title: "ssh&amp; bash scripts"
date: 2009-06-03
forum: General Help
---

### Post by gforster on 2009-06-03
I have ssh all setup with public/private keys to help me out. That works splendidly. I have about 30 computers in our school lab that I want to run some scripts on. Things like apt-get update & apt-get upgrade or aptitude install, etc. I have found [sshsudo]("http://code.google.com/p/sshsudo/") to be extremely helpful for certain things as I don't have to repeatedly type in my password. 

When I install a program, it usually asks for confirmation and I have to press "y" and enter. Is there a way to bypass this connfirmation? The other thing I would like, but is not necessary, is to update/install/whatever simultaneously instead of one after the other. 

My scripting skills are lacking, so let me know if there is a better approach.

Thanks

---

### Post by DGortze380 on 2009-06-03
I think by simultaneously you mean run a certain set of commands, on multiple computers from the same script... ie. script doesn't wait for host 1 before moving to host 2??

If this is true, you'll want to fork the process to the background allowing the shell to continue with the next command.

ex: [http://ubuntuforums.org/showthread.php?t=382330](http://ubuntuforums.org/showthread.php?t=382330)

---

### Post by DGortze380 on 2009-06-03
man apt-get

--assume-yes
    Automatic yes to prompts; assume "yes" as answer to all prompts and run non-interactively. If an undesirable situation, such as changing a held package or removing an essential package occurs then apt-get will abort. Configuration Item: APT::Get::Assume-Yes.

---

### Post by gforster on 2009-06-03
Thank you so much!  I always know that the answer is out there, I just have trouble finding it. Thanks also for the kind and quick response. I'm not sure if I love linux more for its awesomeness or for its awesome community!

---

