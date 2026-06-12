---
title: "Removing compiz"
date: 2006-09-05
forum: Desktop Environments
---

### Post by beercz on 2006-09-05
I am sure that this topic has been covered elsewhere, but I am unable to find how to ***completely*** remove compiz.

Since yesterday's update I have had major problems getting compix to work again.  I have following lots of solutions provided by others in this and other forums, all to no avail.

So I am going to start again from scratch.

Therefore, before I start I need to know how to ***completely*** remove all previous compiz settings, including those in gconf.

Can anyone offer any suggestions?

Thanks

---

### Post by bulldog on 2006-09-05
That,s not necessary.

Do the folowing,
Remove everything in preferences-->sessions--> starting apps which is pointing to compiz.
[compiz-start.py/thefuture or what ever]

Then look in your running session [middle tab in sessions] and remove everything what's pointing to compiz.

Than add to your starting apps tab /usr/bin/compiz-start.

Remove gsetcompiz if you haven't done that it's no longer in use.

Logout and in and everything should be working again.

You now configure your plugins with "csm" in your console.
This opens a configuration tool for you to play with.

Try this I pretty confident that everything is getting to work for you again.

---

### Post by beercz on 2006-09-05
> **bulldog said:**
> That,s not necessary.

Do the folowing,
Remove everything in preferences-->sessions--> starting apps which is pointing to compiz.
[compiz-start.py/thefuture or what ever]

Then look in your running session [middle tab in sessions] and remove everything what's pointing to compiz.

Than add to your starting apps tab /usr/bin/compiz-start.

Remove gsetcompiz if you haven't done that it's no longer in use.

Logout and in and everything should be working again.

You now configure your plugins with "csm" in your console.
This opens a configuration tool for you to play with.

Try this I pretty confident that everything is getting to work for you again.

Nope :-(

Thanks for the reply bulldog.

Obviously something has got messed up on my system, hence my need to remove compiz and start again.

Thanks again bulldog.

Any other suggestions anyone?

---

### Post by beercz on 2006-09-05
> **bulldog said:**
> That,s not necessary.

Do the folowing,
Remove everything in preferences-->sessions--> starting apps which is pointing to compiz.
[compiz-start.py/thefuture or what ever]

Then look in your running session [middle tab in sessions] and remove everything what's pointing to compiz.

Than add to your starting apps tab /usr/bin/compiz-start.

Remove gsetcompiz if you haven't done that it's no longer in use.

Logout and in and everything should be working again.

You now configure your plugins with "csm" in your console.
This opens a configuration tool for you to play with.

Try this I pretty confident that everything is getting to work for you again.

Nope :-(

Thanks for the reply bulldog.

Obviously something has got messed up on my system, hence my need to remove compiz and start again.

Thanks again bulldog.

Any other suggestions anyone?

---

### Post by bulldog on 2006-09-05
Is nothing working?

Try 

chmod 755 ~/.compiz -R

If your settings in csm don't stick.

If all fail it's a pitty but if you want to remove it all,do the HowTo you followed in reverse order or else you can do the following.

Just remove your compiz-start out of your sessions menu and gedit your xorg.conf to the original and restart.
This will compiz not allowed to startup again.

---

