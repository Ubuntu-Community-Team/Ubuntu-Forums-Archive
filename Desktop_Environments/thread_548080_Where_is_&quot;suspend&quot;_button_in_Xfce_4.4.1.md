---
title: "Where is &quot;suspend&quot; button in Xfce 4.4.1?"
date: 2007-09-10
forum: Desktop Environments
---

### Post by saul_2110 on 2007-09-10
Hi. I'm running Xubuntu Dapper Drake and recently installed Xfce 4.4.1. 
Before installing, there were the buttons "suspend" and "hibernate" in the logout dialog but after installing Xfce 4.4.1, they disappered. 
Does anyone know how to put them back?. 
Thanks.

---

### Post by ryno519 on 2007-09-10
Yep.

Go to Settings -> Settings Manager -> Sessions and Startup

and check the boxes 'Show Hibernate Button' and 'Show Suspend Button'

---

### Post by saul_2110 on 2007-09-10
> **ryno519 said:**
> Yep.

Go to Settings -> Settings Manager -> Sessions and Startup

and check the boxes 'Show Hibernate Button' and 'Show Suspend Button'

Those boxes are no longer there in Xfce 4.4.1. But thanks anyway :).

---

### Post by ogara0c9 on 2007-09-20
Is there no settings manager button, or is the entire settings menu gone?  Also how was the install of 4.4.1 on Dapper.  How would you recommend upgrading from Beta1?  I really just want the ability to change unfocused windows somewhat transparent which is missing in Beta1.

---

### Post by x1a4 on 2007-09-20
> **saul_2110 said:**
> Those boxes are no longer there in Xfce 4.4.1. But thanks anyway :).

Really? :shock:  I'm using 4.4.0 and they're still there.  Anyway,  open ~/.config/xfce4-session/xfce4-session.rc edit these lines: 
```
HibernateButton=true
SuspendButton=true
```

---

### Post by saul_2110 on 2007-09-20
> **ogara0c9 said:**
> Is there no settings manager button, or is the entire settings menu gone?  Also how was the install of 4.4.1 on Dapper.  How would you recommend upgrading from Beta1?  I really just want the ability to change unfocused windows somewhat transparent which is missing in Beta1.

In "Sessions and Startup" there are two tabs (General and Advance Settings [or so]) but the checkboxes are gone.

> **ogara0c9 said:**
>  how was the install of 4.4.1 on Dapper.  How would you recommend upgrading from Beta1? 

To install Xfce4.4.1 on Dapper, go to xfce.org and download the source. Also there are some instructions for the installing in Documentations > 4.2 documentation > Installing. And the order and dependencies for compiling the packages is in Documentation > Requierements. 
In my experiance, install all dependencies even the "optional" and their respective "dev" package.
Some packages, after the ./configure step, show the features they have enable for the making. Check it out and if there is a feature you want that is not enabled, go to the REAME or review the output of the configure to find out what package is missing and install it (including its "dev" package).
I think there is also a binary but haven't use it.

> **ogara0c9 said:**
>  I really just want the ability to change unfocused windows somewhat transparent which is missing in Beta1.

For the transparency, check out the REAME of the soruce package xfwm4. What you are looking for (I think) is the activation of Composite.

Hope I helped. Good luck.

---

### Post by saul_2110 on 2007-09-20
[QUOTE=x1a4] Really?  I'm using 4.4.0 and they're still there. Anyway, open ~/.config/xfce4-session/xfce4-session.rc edit these lines[\QUOTE]

It didn't work... But thanks. I suppose they removed that feature.

---

### Post by ogara0c9 on 2007-09-20
> It didn't work... But thanks. I suppose they removed that feature.

That stinks.  Can't imagine why the option would be taken out.

> For the transparency, check out the REAME of the soruce package xfwm4. What you are looking for (I think) is the activation of Composite.

The funny thing is that composite is working for option options (transparent moving, etc.) but like your situation, this particular option for inactive windows is missing.  I'll first check the source code (like a good soldier) and then look into the upgrade (since I don't use hibernate or suspend at this time :-?)

---

