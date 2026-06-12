---
title: "Cannot add Beryl and Emerald to Startup programs"
date: 2007-05-21
forum: Desktop Effects &amp; Customization
---

### Post by benbooth on 2007-05-21
Hi, got a problem that's really annoying me now.

I have installed Beryl w/ XGL for ATI, following the alternative method from UbuntuGuide.

I have my system setup really nicely, but for some strange reason I cannot add "beryl-manager" or "emerald --replace" to the startup programs!

When I add them and close the 'Sessions' window and go back in...nothing! Everything else but!

Can anyone help?

Thanks,

Ben

---

### Post by Ateo on 2007-05-21
Can you add ANY program to startup? Or is it just beryl/emerald giving you issues?

You can also try making a wrapper script that will launch both for you.

---

### Post by davbren on 2007-07-07
I have the same issue and its with all programs not just Beryl...I know other people have had the same issue, I have no clue what to do, I'm a relative n00b at this its really starting to bug me.

---

### Post by balki2005 on 2007-07-07
hello guys,

I had the same problem, but read  somewhere that you  need  change the ownership of this directory, because it's root the owner as default. And  that's the reason  that you can't create new startup programs:

[email]jonay@thunder-dragon:~/.conf[/email]ig$ ll
total 12
drwxr-xr-x 2** root  root**  4096 2007-07-07 16:04 autostart

do this and it will work again:


[email]jonay@thunder-dragon:~/.conf[/email]ig$ sudo chown -R jonay:jonay autostart
Password:
[email]jonay@thunder-dragon:~/.conf[/email]ig$ ll
total 12
drwxr-xr-x 2 jonay jonay 4096 2007-07-07 16:04 autostart
drwx------ 2 jonay jonay 4096 2007-07-07 16:14 gtk-2.0
drwxr-xr-x 2 jonay jonay 4096 2007-07-07 15:48 menus
[email]jonay@thunder-dragon:~/.conf[/email]ig$ 

regards,

balki2005

---

### Post by davbren on 2007-07-08
Ok its really cool that you have a solution, but I'm a bit of a n00b and don't  understand your explanation, is it possible to make it any clearer?

---

### Post by nmwhit06 on 2007-07-15
I also had this problem where I couldn't add any programs to my startup list in Feisty.  I tried balki2005's solution and it worked perfectly.  If you didn't understand his solution, I'll simplify it for you.  So open up a terminal window.

First you have to change your current directory:

```
cd ~/.config
```
 
Then you have you change the ownership to your username (Replace 'nate' with your username):

```
sudo chown -R nate:nate autostart
```

And then you're done.

Nate

---

