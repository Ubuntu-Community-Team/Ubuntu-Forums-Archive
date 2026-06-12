---
title: "evolution uninstalled during upgrade and now won't reinstall."
date: 2008-05-28
forum: Desktop Environments
---

### Post by luke16 on 2008-05-28
Anybody know why this happened or what I can do to fix it?

$ sudo apt-get install evolution
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  evolution: Depends: evolution-common (= 2.22.1.1-0ubuntu2) but 2.22.1.1-0ubuntu3 is to be installed
E: Broken packages

---

### Post by werries on 2008-05-28
go to synaptic manager, hit custom filters, and go to broken.
install that/those to fix the broken ones.
then go in synaptic, search evolution.
you need to install evolution-common and evolution

---

### Post by luke16 on 2008-05-28
Nothing shows up when I select broken filter.

---

### Post by luke16 on 2008-05-30
Now update manager is coming up and saying that I need to do a partial upgrade to install all packages and that won't even work, telling me that it could not calculate the upgrade.

---

### Post by krcabrer on 2008-05-30
In my case the situation was worst.

It desinstall all my ubuntu studio desktop, bars, and many other
programs... 

I try to reinstall and it appears the same problem but it says that

  ubuntustudio-desktop: Depende: alacarte pero no va a instalarse
                        Depende: gnome-about pero no va a instalarse
                        Depende: gnome-applets pero no va a instalarse
                        Depende: gnome-panel pero no va a instalarse

and I try to install alacarte, then it asks for
gnome-about, then for gnome-panel and finaly I get:

Los siguientes paquetes tienen dependencias incumplidas:
  gnome-about: Depende: gnome-desktop-data (= 1:2.22.2-0ubuntu1) pero 1:2.22.2-0ubuntu2 va a ser instalado
E: Paquetes rotos

I try to fix with synaptic and it does not show any "broken" package.

The evolution program now is desinstalled, all the ubuntu desktop also.

thank you for your help!!!

Kenneth

---

### Post by luke16 on 2008-05-30
Using synaptic instead seems to help with updating vs using update manager in that it actually worked without saying anything about this "partial update" thing. Synaptic is telling me that apparently evolution needs an older evo-common file that was updated, which is why it doesn't want to run.

evolution:
  Depends: evolution-common (=2.22.1.1-0ubuntu3) but 2.22.2-0ubuntu1 is to be installed
 Depends: evolution-data-server but it is not going to be installed


> **krcabrer said:**
> 

Los siguientes paquetes tienen dependencias incumplidas:
  gnome-about: Depende: gnome-desktop-data (= 1:2.22.2-0ubuntu1) pero 1:2.22.2-0ubuntu2 va a ser instalado
E: Paquetes rotos


It looks like you have the same general problem. I think the people who manage the updates have gotten careless with what updates they post.

---

### Post by mick316 on 2008-05-30
I had this problem just now after I updated. What I did to fix the problem is:mark for reinstallation the evolution-common  then go to package, Force version and select 2.22.1.1-0ubuntu3, you will have to do this also for a couple of other dependancies, once done you can install evolution again.

---

### Post by krcabrer on 2008-05-30
> **mick316 said:**
> I had this problem just now after I updated. What I did to fix the problem is:mark for reinstallation the evolution-common  then go to package, Force version and select 2.22.1.1-0ubuntu3, you will have to do this also for a couple of other dependancies, once done you can install evolution again.

Thank you for your help.

It works again!!!

You save my life!!! :)

Now, how can you trust the updates? Which updates can I trust on?

Thank you very much for your help.

Kenneth

---

