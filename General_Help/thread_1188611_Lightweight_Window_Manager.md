---
title: "Lightweight Window Manager"
date: 2009-06-15
forum: General Help
---

### Post by Mattaus on 2009-06-15
Hi all,

Sorry if this belongs over in the desktop envronment section - I couldn't decide!

I'm in the process of customizing my setup and working out some kinks but one thing that has been top of my list is improving my boot times. I am building a HTPC system running XBMC and MythTV  and would like a full functionality desktop environment to fall back to for debugging and addition of new features if the need arises. There are options over on the XBMC fourms but they are more drastic, where as I am trying to just implement incremental changes.

Now I am fairly new to Linux in general so I was wondering what alternatives to KDE or GNOME people may be using or would recommend to help in this goal?

Would say using a lighter weight manager cripple anything with XBMC or MythTV? What kind of mileage can I expect from say XFCE or the like?

Any suggestions, information and general advice would be greatly appreciated.

Cheers! 

PS: I seem to remember stumbling across a thread (not sure if it was here or over on XBMC that talked about stopping the X-server from running at all until XBMC was launched. So basically you set XBMC to run on start up, and when it launched X-server ran (and only ran XBMC) hence greatly improving boot up time. I think :-| Anyone know where I could maybe look into that?

---

### Post by Chemical Imbalance on 2009-06-15
My suggestions:

1. fluxbox
2. openbox
3. lxde

---

### Post by nolliecrooked on 2009-06-15
SMAKWRM. but its still alpha.

---

### Post by Chemical Imbalance on 2009-06-15
> **nolliecrooked said:**
> SMAKWRM. but its still alpha.

Do you have a link for that?  Can't find it.  I'm curious.

---

### Post by Mattaus on 2009-06-15
Cool....I'm checking out fluxbox now. Seems I've got some reading to do though. Installing it is easy enough but I need to learn how to make sure Ubuntu loads Fluxbox when it boots instead of GNOME and then auto log in and launch MythTV and XBMC.

Hope there's a guide!

EDIT: OK I've dug up how to install it in Ubuntu:

> apt-get install Fluxbox

And have also found a guide on how to get it to launch XBMC with the Fluxbox start up script (I'm assuming this will only launch XBMC, and not the desktop but then again I could be wrong!?) I still need to find auto-login to Ubuntu but I have one question - how do I tell Ubuntu to use fluxbox? Or is that taken care of when I install it?

Oh! And if I screw it up or it does not work as I hoped how can I go back to GNOME?

---

### Post by eriqjaffe on 2009-06-15
> **Mattaus said:**
> I still need to find auto-login to Ubuntu but I have one question - how do I tell Ubuntu to use fluxbox? Or is that taken care of when I install it?You choose your session at the GDM login screen, and will be prompted if you want to make that the default session.  To change sessions (and change your default, if you so desire), just log out and then you'll be back at the GDM login screen again.  Easy peasy.

---

### Post by Mattaus on 2009-06-15
Oh...really is easy isn't it lol! One question remains though:

As I have Ubuntu auto-logging in already does this mean that if I change my default session to Fluxbox it will also automatically log in?

---

### Post by eriqjaffe on 2009-06-15
I think so, yes.  Easy enough to find out, though.  ;)

---

### Post by Mattaus on 2009-06-16
> **eriqjaffe said:**
> I think so, yes.  Easy enough to find out, though.  ;)

haha yes I know - I'm just at work at the moment and I seem to do all my hardcore thinking about non-work related stuff while I'm...well at work lol. I've got a list as long as my arm of stuff I want to do tonight when I get home but I know it's weeks worth of mucking about :(

I'll try it out tonight (if I get MythTV working) and let you know how I get along.

Thanks for the help.

---

### Post by lovinglinux on 2009-06-16
I'm not an expert on the subject, but as far as I know [KDE](http://en.wikipedia.org/wiki/KDE), [Gnome](http://en.wikipedia.org/wiki/GNOME), [XFCE](http://en.wikipedia.org/wiki/XFCE) and [LXDE](http://en.wikipedia.org/wiki/LXDE) are [Desktop Environments](http://en.wikipedia.org/wiki/Desktop Environment), not [Window Managers](http://en.wikipedia.org/wiki/X_window_manager). On the other hand, [ Openbox](http://en.wikipedia.org/wiki/ Openbox), [Fluxbox](http://en.wikipedia.org/wiki/Fluxbox), [Metacity](http://en.wikipedia.org/wiki/Metacity), [Compiz](http://en.wikipedia.org/wiki/Compiz) are Window Managers, which runs on the top of one of the Desktop Environments.

Nevertheless, I guess you can run fluxbox or openbox without a Desktop Environment (see quote below).

> 
From [http://en.wikipedia.org/wiki/Comparison_of_desktop_environments](http://en.wikipedia.org/wiki/Comparison_of_desktop_environments)

Some exceptions must be noted here. Window managers like Fluxbox, wmii and Ratpoison operate independently of a desktop environment and were written with this objective in mind. Additional hand-picked applications add functionality such as a panel and volume management which gives them some of the qualities of a full DE. This contrasts the behaviour of WMs like Metacity and KWin which were not written with the objective of operating independently of a DE.

If you are looking for a Window Manager, then you might find some info in this [comparison chart](http://en.wikipedia.org/wiki/Comparison_of_window_managers). My guess you need a Desktop Environment, so take a look at this [comparison chart](http://en.wikipedia.org/wiki/Comparison_of_desktop_environments). You might also want to try [Enlightenment](Enlightenment), which is pretty fast, although not stable.

---

### Post by Mattaus on 2009-06-16
Argh! Where did you come from lol? 

I'll read up on all that though I am now pretty confused. I just remembered the local Linux guru is at work today so I might go pick his brains for a bit. Not saying you're wrong (as I clearly have no clue) I just want to make sure I know exactly what I'm doing before I do it.

I've already built this system 5 times in a week (hardware and software issues)

EDIT:
> 
Nevertheless, you I guess you can run fluxbox or openbox without a Desktop Environment (see quote below).

Ah I think maybe that is why it was suggested in the first place - as I have no need for the desktop unless I am debugging (everything is run through XBMC) and I have found a way to make FLuxbox launch specific applications on start up.

Guess I'll have to try and see :)

---

### Post by lovinglinux on 2009-06-16
> **Mattaus said:**
> Argh! Where did you come from lol? 

I'll read up on all that though I am now pretty confused. I just remembered the local Linux guru is at work today so I might go pick his brains for a bit. Not saying you're wrong (as I clearly have no clue) I just want to make sure I know exactly what I'm doing before I do it.

I've already built this system 5 times in a week (hardware and software issues)

EDIT:


Ah I think maybe that is why it was suggested in the first place - as I have no need for the desktop unless I am debugging (everything is run through XBMC) and I have found a way to make FLuxbox launch specific applications on start up.

Guess I'll have to try and see :)

Yep, it is confusing. For instance, it seems that Elightenment is not a full DE, but a shell (whatever that means :)). Nevertheless, I think you are on the right path with Fluxbox, since you don't need the bells and whistles of a full Desktop Environment like Gnome or KDE. 

I'm also interested on this subject now, because Gnome 3 is heading towards something I don't really like with the new Gnome Shell. It seems that it will have it's own window manager integrated and we won't be able to use use Compiz with it. So, I'm thinking about using an alternative DE, but unfortunately there isn't many options if I want to keep Compiz.

---

### Post by Mattaus on 2009-06-16
Yeah as far as I can tell Fluxbox is as basic as you can get, and you simply add in features you want by editing the startup file...or something along those lines.

Like I said I have other things I need to sort out before I can try Fluxbox, so I'm a good week away from using it (unless everything goes smoothly, which in Linux is rarely the case).

One question I may need more info on though is if I quit XBMC (the only app I want Fluxbox to run) then what do I get? Command line or a desktop?

Guess there is only one way to find out.

---

### Post by lovinglinux on 2009-06-16
> **Mattaus said:**
> One question I may need more info on though is if I quit XBMC (the only app I want Fluxbox to run) then what do I get? Command line or a desktop?

You get the desktop.

> **Mattaus said:**
> Guess there is only one way to find out.

I would recommend making tests on a Virtual Machine, so you can mess with it all you want.

---

### Post by Mattaus on 2009-06-16
> I would recommend making tests on a Virtual Machine, so you can mess with it all you want.

That is a very good idea lol. Will do.

---

