---
title: "How do I setup a custom gnome session?"
date: 2009-06-30
forum: Desktop Environments
---

### Post by kenneth.cochran on 2009-06-30
I'm trying to setup a custom gnome session that looks like Windows to give the users something familiar until they get use to the normal gnome desktop. I've seen plenty of tips on making gnome look like Windows but I want to retain gnome's original settings as well.

I'd like to give the user a choice when they login.

Any idea if this is possible?

---

### Post by linuxrockz on 2009-06-30
Just create a new user 
System > Administration > Users and Groups

Unlock the window by clicking on unlock and entering administrator password.
Now add a new user.

Make any changes you like in the new user account to make it look like windows.

Your original settings will be untouched in the administrator account.
You will also get option to login into any account you wish at the login screen.

But ubuntu will surely look alien with a bliss wallpaper and a blue start panel :lolflag:

May be you can convert some windows addicts to ubuntu in this way.

All the best.

---

### Post by kenneth.cochran on 2009-06-30
Perhaps my intentions weren't clear enough in my original post. I'm setting up a computer lab for a school using LTSP and I would like to give the users the option of loading the standard gnome desktop or one customized to look like Windows. The user accounts are going to be authenticated against Active Directory.

Creating two separate user accounts for each user just isn't a realistic solution.

The rest of the school's computers run windows. This will be the school's first experience with Linux (I've used it off and on for at least a decade). The hard drives in the lab computers are failing. I don't have the time and the school doesn't have the money to keep replacing them. So the solution I came up with was turning them into thin clients.

I chose linux for a few reasons:

[LIST=1]
[*]Its free
[*]Its secure
[*]It runs better on the lab computers than Windows did
[/LIST]
Windows terminal services is another option and if the users simply refuse to accept Linux I'm still keeping it on the back burner. My main concern with it is the upfront cost for licenses. The school is already exceeding the number of CALs they have. Convincing them to use Linux would kill two birds with one stone.

This isn't the only obstacle I face. The school relies on a program which is only supported on Windows. I contacted the creators and they said they'd never tried it with wine but were more than happy to use us as ginnie pigs. :-)

If I can make this project a success I'll have an easier time migrating the rest of the school down the road.

---

### Post by ~sHyLoCk~ on 2009-06-30
Hmm not sure if [this]("https://wiki.ubuntu.com/CustomXSession") will help. But you know what you can do is install another DE, KDE,XFCE  ,LXDE, and customize it to make it look like windows. Now when you login pick that from the sessions menu in GDM Login window.

---

