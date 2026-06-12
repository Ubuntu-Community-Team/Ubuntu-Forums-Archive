---
title: "I'm locked out of my own hdd?!!!!!!!!"
date: 2009-04-14
forum: General Help
---

### Post by FruitRocks on 2009-04-14
How do I put files into my home folder? Every time I try, it says something like "Can't fix permissions" or "Access denied." I am logged onto as root, and its not even asking for a password!! How do I fix this? 
also, how do i disable the annoying prompt when it asks me for my password when I try and perform admin functions?

I love linux.... I would hate having to switch back to Vista :mad:
p.s. i'm running Ubuntu 8.10, if that helps :)

---

### Post by 3rdalbum on 2009-04-14
It's against Ubuntu Forums policy to tell you how to disable the 'sudo' permissions elevation prompt. Doing this not only makes your computer more insecure and likely to be broken by your actions, but can also cause problems with programs that assume a fully-functioning security system.

Ubuntu also doesn't allow root logins by default, so you've obviously done some fiddling there. You should be able to put files into your home directory if you are logged in as root which makes me believe that you might have already broken something. Unfortunately I lack the knowledge to help you repair the damage you have done so you'll have to wait until someone with more knowledge can help.

---

### Post by Vaphell on 2009-04-14
well, it's because your home dir is not owned by root and apparently root account doesn't have writing priviledges in /home/username/.
why did you log in as a root in the first place? you shouldn't really do that unless you want to rescue broken system. There is sudo/gksudo to temporarily empower your normal account with admin rights

You have windows user mindset - running account with full admin rights, security features seen as annoyance :) It's much healthier to do the exactly opposite - running limited account and elevate rights when absolutely necessary. What if you accidently was about to delete some of the system folders? without any confirmation you'd happily brick your box that way.

---

