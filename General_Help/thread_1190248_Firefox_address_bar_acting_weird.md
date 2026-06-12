---
title: "Firefox address bar acting weird"
date: 2009-06-17
forum: General Help
---

### Post by nereid on 2009-06-17
Hi folks,

I've got a curious problem and I haven't found a solution for it anywhere, so I will ask here ;)

I'm currently using Jaunty and from time to time the Awesome bar in FF 3 will stop working. I can use it to enter any URL and navigate to that site but the bar won't display a drop down list anymore. The whole thing gets really weird, as the bar will work normally again after some time.

I hope, that someone has a solution to this problem. It would even help, to know, that I'm not the only one encountering it ;)

Thanks in advance.

---

### Post by pytheas22 on 2009-06-17
A quick, but messy, fix would probably be to refresh your Firefox configuration by typing:
```

mv ~/.mozilla ~/mozilla-OLD
```

The downside of this command is that it will cause your entire Firefox configuration--including extensions--to go back to the defaults, erasing any customizations you may have applied, as well as web history; depending on how much time you've spent customizing Firefox, this may not be acceptable to you.  However, you might be able to find just the part of your .mozilla directory that contains the files relevant to the awesome and refresh only that part, leaving the other settings intact; I'm not sure where exactly Firefox stores information for the awesome bar.

---

### Post by lovinglinux on 2009-06-17
> **pytheas22 said:**
> I'm not sure where exactly Firefox stores information for the awesome bar.

The file is *places.sqlite*. Just delete it and things should be fixed.

---

### Post by pytheas22 on 2009-06-17
> The file is places.sqlite. Just delete it and things should be fixed.

Thanks for that information.  In this case, typing this command should refresh the awesome bar configuration:
```

mv ~/.mozilla/firefox/*.default/places.sqlite ~/.places.sqlite-OLD
```

Then restart Firefox.  Do the problems go away?

---

### Post by nereid on 2009-06-19
Thanks for your answers.

Deleting the database didn't really help. Also a "VACCUM" command via sqlite3 didn't do the job. The drop down part of the bar is still sometimes disabled.

---

### Post by pytheas22 on 2009-06-19
Sorry that didn't help.  I wonder if it's a global problem with Firefox, rather than something specific to your user account.  To test, create a new account.  The next time the awesome bar breaks in your primary account, log in under the new account and see if it's broken there as well.  If so, it's a global problem with your Firefox installation, and reinstalling it in Synaptic might help, especially with the 'remove completely' option.

---

### Post by nereid on 2009-06-19
Do you really think, removing and reinstalling it, would help?

I could try to remove the main account, although I would only do this as a last resort ;)

---

### Post by pytheas22 on 2009-06-19
> Do you really think, removing and reinstalling it, would help?

It might.  If the problem is with the system-wide installation of Firefox--in other words, the global configuration files in /etc/firefox-3.0 that apply to all users--then reinstalling it with:
```

sudo apt-get remove --purge firefox
sudo apt-get install firefox
```

might solve the problem, because it would set those configuration files back to the defaults. (Make sure the system isn't going to remove anything else important when you uninstall Firefox.  It shouldn't, but check the output just to be safe.)

On the other hand, if the problem has to do with your personal user settings--the files stored in /home/yourname/.mozilla--then reinstalling Firefox would not help.
> 
I could try to remove the main account, although I would only do this as a last resort

You don't need to do that.  Just create a second account (without removing your primary one) and see if Firefox works there.  If so, then you know the problem is not global, and we can look harder at your personal user settings to figure out what might be wrong.  But if Firefox is broken under all user accounts, then we know it's a global problem and can deal with it accordingly.

---

### Post by nereid on 2009-06-20
Thanks for your patience :)

I'll try it out this weekend.

---

### Post by adrianx on 2009-06-20
I have noticed a similar problem with Firefox in Jaunty. Sometimes, the Awesome bar doesn't drop down **and** text fields in web pages lose focus when my mouse leaves the browser window - e.g. when I place the mouse cursor on a Gnome panel.

---

### Post by Legace on 2009-06-20
Have you tried using Firefox with Compiz disabled?

---

### Post by hyperdude111 on 2009-06-20
I have posted this on a few firefox threads and it has worked so i'll try again here.
> 
Go to Home the press "ctrl-H" go into the .mozilla folder.

rename the firefox folder to firefox.bak and it should work.

---

