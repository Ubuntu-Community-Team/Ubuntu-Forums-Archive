---
title: "Bash Autocompletion Broken on Jaunty"
date: 2009-04-28
forum: General Help
---

### Post by sb73542 on 2009-04-28
Hi,

I installed Ubuntu Jaunty from the alternate CD with the "command line system" install option. Unlike previous versions, "apt-get install <TAB> no longer autocompletes package names. "apt-get remove" does autocomplete still. This is quite a significant regression. I have verified that the bash-completion package is installed.  Any tips?

Thanks.

---

### Post by freonchill on 2009-04-28
did you upgrade install or clean install?

---

### Post by sb73542 on 2009-04-28
Clean install, I tried both Kubuntu and Ubuntu "alternate install" CDs with the "command line system" install option.

---

### Post by Nero147 on 2009-04-28
I agree with freonchill. On my netbook I upgraded from the beta to stable and it doesn't autocomplete, but on my desktop, which was a clean install it worked fine. You might try a clean install and just save your home directory.

---

### Post by Nero147 on 2009-04-28
why are you using the alternative cd?

---

### Post by freonchill on 2009-04-28
did a clean install on a dell d800 laptop
had to use safe mode for the install (as the regular install did not like my nvidia graphics)

auto complete works fine for filenames; i want to say i used it for an apt-get also.

---

### Post by sb73542 on 2009-04-28
OK, just to be very clear about this, this is a CLEAN install.  It is not an upgrade.  I use the alternate CD because I want to customize my package selection.  This bug has been reproduced twice now by me.  Any way to fix it?

---

### Post by Quaxo76 on 2009-05-11
I have the same problem, but with clean installs from the regular (non-alternate) final ISO. This happens on two different HP laptops. And it really is annoying! I used autocompletion a lot with apt-get...

---

### Post by vorgusa on 2009-06-18
try:
sudo apt-get install bash-completion

you will need to log off and log back on for it to work :) enjoy

---

### Post by Quaxo76 on 2009-06-19
I tried that, it said that bash-completion is already the newest version... :( And by the way, auto-completion works with filenames and paths, it's just apt-get and aptitude that don't autocomplete...

---

### Post by vorgusa on 2009-06-19
check out this posting

[http://ubuntuforums.org/showthread.php?t=734023](http://ubuntuforums.org/showthread.php?t=734023)

hopefully it will help you out

---

### Post by Quaxo76 on 2009-06-19
OK, solved it. I'm posting the solution here in case others are affected: I just had to open the file /etc/bash.bashrc and uncomment the following section:
```
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi
```

Maybe the thread name can be updated to add "Solved"...

What I still wonder, is why I and other few people have that section commented out... for me, it was that way on 3 different computers. And that was with a clean install from the official CD...

Thank you so much for your help,
Cristian

---

### Post by geirha on 2009-06-19
By default, that section is commented out in the global bashrc (/etc/bash.bashrc), but active in each user's stock ~/.bashrc ... Do you see that section in /etc/skel/.bashrc ? Have you edited or overwritten your ~/.bashrc ?

---

### Post by Quaxo76 on 2009-06-19
In /etc/skel/.bashrc I have that section, and it is not commented out.
But I don't have a .bashrc file in my home folder. And I'm sure I haven't deleted it myself. I can't check the other two computers right now, but I'll check later if the situation is the same... Might that .bashrc file never have been installed? Or some program deleted it?
How could I regenerate the missing file on my system?

---

### Post by geirha on 2009-06-19
When a user is created, all files under /etc/skel is copied to its home folder, so just copy it from skel.
```
cp /etc/skel/.bashrc ~/
```

---

