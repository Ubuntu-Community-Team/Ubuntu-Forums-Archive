---
title: "Can I change the default shell in Ubuntu?"
date: 2005-02-13
forum: Desktop Environments
---

### Post by Sleeper Service on 2005-02-13
Hi - coming from Mandrake, I liked some of the ways the shell acted on that distro, compared with how it works in Ubuntu.

If you used tab auto-completion under Mandrake and there were two similarly named files, you'd get all the alternatives being printed so you could choose.

Also, the prompt would only contain the current directory you were working in - not the entire path.

Can I change any of these things?  I know nothing about the different shells and how their behaviour is configured, so any help would be appreciated.

Cheers.

---

### Post by scoon on 2005-02-13
Hey there, 

Here are some links that will help you tweak your BASH: 

[http://www-106.ibm.com/developerworks/linux/library/l-tip-prompt/](http://www-106.ibm.com/developerworks/linux/library/l-tip-prompt/)
[http://www.gnu.org/software/bash/manual/bash.html](http://www.gnu.org/software/bash/manual/bash.html)

Good luck and happy BASH'ing


scoon

---

### Post by Sleeper Service on 2005-02-14
Thanks, scoon.  That's helped my to sort our the way the prompt looks and sort out the tabbing issue.

But I've still got a couple of very minor gripes that someone may be able to help with...

*1.  Clear screen (tty1-6) on logout:*
When I'm using a proper terminal in tty1-6, and I log out, Ubuntu leaves the last screenfull of commands visible for the next person to see.  Mandrake clears the screen on logout, so the next user is presented with just a "login:" prompt.  Anyway to get Ubuntu to behave like that?

*2.  "You have new mail."? - no I don't!*
Again, using tty1-6, when I login I'm greeted with "You have new mail."  I don't recall asking for any mail accounts anywhere other than Opera.  Have I uninstalled some terminal mail client by accident?  Can I turn this off?

---

### Post by word_virus on 2005-02-14
*2.  "You have new mail."? - no I don't!*
Again, using tty1-6, when I login I'm greeted with "You have new mail."  I don't recall asking for any mail accounts anywhere other than Opera.  Have I uninstalled some terminal mail client by accident?  Can I turn this off?[/QUOTE]

This is probably some system process sending you mail.  See the HOW-TO post called something like "Have root's mail delivered to your inbox" for more info.

Also, for more shell customization ideas check out dotfiles.com

---

