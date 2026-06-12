---
title: "Problem with MATE 1.6 in Ubuntu 13.04"
date: 2013-07-09
forum: Desktop Environments
---

### Post by Ambidextrous on 2013-07-09
After reinstalling 13.04 to fix an incomplete upgrade from 12.10 I was faced with Unity :(.  I had been using Gnome Fallback, but since no updates are planned I decided to try MATE, a fork of Gnome 2.  First, after some research, I installed MATE:

*sudo*[I] apt-get update 
sudo apt-get install mate-archive-keyring 
sudo apt-get update 
sudo apt-get install mate-core 
sudo apt-get install mate-desktop-environment[/I]

Then I removed Unity:

*sudo apt-get --purge unity** (I think)

and rebooted.

No Unity.  :D

But no MATE either.  Just my desktop background.  I got a terminal open (Ctrl-Alt-T) and used a command beginning X :1 (I'm sorry I'm not more specific but I'm posting this in Windows from memory and I can't scroll back through my terminal commands to check).  It worked.  I had the MATE DE.  I was a happy man!  I made a few tweaks and rebooted to see if MATE would load automatically (I'm the sole user so I have Ubuntu set to automatically log in).

Nope.  And the clever command I'd used before wouldn't work either.  I ran *sudo apt-get install lightdm* just to make sure I hadn't inadvertently removed or otherwise trashed it.

Any suggestions about how to fix it?

TIA

Terry

---

### Post by silv3rm00n on 2013-07-10
Xfce or Lxde is better. Install one of them.

---

### Post by Ambidextrous on 2013-07-10
> **silv3rm00n said:**
> Xfce or Lxde is better. Install one of them.

At the moment I'm not interested in debating the merits of DE's, just in getting the one I have installed to work.  I suspect that if I installed another it wouldn't work either, because I think there's a step missing from my logon process, and I don't know how to revert to manual logon from the command line.

---

### Post by grahammechanical on 2013-07-10
Re-install and this time do not remove Unity. You most probably removed ubuntu-desktop as well. A lot of stuff is inter-dependant.

---

### Post by buzzingrobot on 2013-07-10
You could try "apt-get install ubuntu-desktop" and see how far that gets you.

But, as suggested, your best bet is to reinstall Ubuntu and then MATE.  

If you are desparately short of drive space or don't want Unity around for other reasons, there are a few how-to's around claiming to describe how to safely remove Unity from a MATE system.  Check at the forum at the MATE site -- mate-desktop.org -- for those.Another  approach is to do a minimal Ubuntu install and then install MATE. (Usually via the mini.iso and a network install.)

If I really didn't want Unity hanging around, I'd go the minimal install route, rather than take the risks involved in removing it after the fact.

However, MATE by itself does not include a good number of the applications that you might need and that are included in a standard Ubuntu install.  For example, if you need a GUI tool to blank and burg CD's and DVD's, there isn't one in MATE.  If you install Brasero, it brings in a considerable number of Unity packages as dependencies.

Installing large and complex package collections like MATE usually creates many dependency links with and between existing software components. That's why you lost so much when you zapped Unity.

---

### Post by Ambidextrous on 2013-07-11
> **buzzingrobot said:**
> You could try "apt-get install ubuntu-desktop" and see how far that gets you.

But, as suggested, your best bet is to reinstall Ubuntu and then MATE. 

Not very far... so I reinstalled 13.04, using the "delete" option and then installed MATE as described earlier, WITHOUT removing Unity.  But Unity still loads after I log on.  What do I need to do to get MATE to load instead?  (And I promise, I have spent a couple of hours reading various "How to install MATE" articles and they all ended with:

*"sudo apt-get install mate-desktop-environment*
That's it."

Well, in may case, that's definately NOT it.  There's clearly another step...

---

### Post by cradom on 2013-07-11
Do you get a login screen? Try logging out and click the button upper right of the text box and select Mate.

---

### Post by buzzingrobot on 2013-07-11
The instructions here ([http://wiki.mate-desktop.org/download](http://wiki.mate-desktop.org/download)) have always worked for me, several times.

You are logging out and then selecting MATE from the dropdown list in LightDM?

---

### Post by Ambidextrous on 2013-07-11
> **cradom said:**
> Do you get a login screen? Try logging out and click the button upper right of the text box and select Mate.

Holy ####, that's a button?  Could it possibly be more obscure? That may be the single most counter-intuitive process in my six years with Ububtu. Thank you!

[Switch to "Pushing my luck" mode]

Is there a way to logon to MATE automatically, bypassing the logon screen? (I'm the only person with access to this PC and I consider the security risk acceptable.)

Thanks again.

---

### Post by Ambidextrous on 2013-07-11
> **buzzingrobot said:**
> The instructions here ([http://wiki.mate-desktop.org/download](http://wiki.mate-desktop.org/download)) have always worked for me, several times.

That's where the steps outlined in my initial post (without the uninstallation of Unity) came from.  Thanks.

---

### Post by buzzingrobot on 2013-07-11
> **Ambidextrous said:**
> Holy ####, that's a button?  Could it possibly be more obscure? That may be the single most counter-intuitive process in my six years with Ububtu. Thank you!

[Switch to "Pushing my luck" mode]

Is there a way to logon to MATE automatically, bypassing the logon screen? (I'm the only person with access to this PC and I consider the security risk acceptable.)

Thanks again.

That's where any other desktops you may install show up, too, on LightDM. MATE just has the misfortune of parking an emopty white dot there. I'm not aware of any display mananger that handles things very differently.

Dig around in MATE's settings for the auto logon,

---

### Post by Buntu Bunny on 2013-07-14
> **Ambidextrous said:**
> Holy ####, that's a button?  Could it possibly be more obscure? That may be the single most counter-intuitive process in my six years with Ububtu. Thank you!

[Switch to "Pushing my luck" mode]

Is there a way to logon to MATE automatically, bypassing the logon screen? (I'm the only person with access to this PC and I consider the security risk acceptable.)

If you have more than one DE installed, you likely have no way to bypass the login screen. But it should "remember" the last DE you logged into so that you don't have to select it each time.

---

