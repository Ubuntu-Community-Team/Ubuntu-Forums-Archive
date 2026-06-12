---
title: "No more shutdown or restart buttons in User Switcher Applet"
date: 2008-12-30
forum: Desktop Environments
---

### Post by Rippy on 2008-12-30
I've been playing around with AWN, Screenlets, Pidgin and Compiz settings today (on a new install of 8.10), and though I ended up uninstalling AWN and Screenlets, I seem to have messed up my User Switcher Applet (i.e. the button at the top-right).

The dropdown only displays Lock Screen, Guest Session, and Logout, instead of the usual assortment of Shutdown, Restart etc. I have no idea what caused it, though my suspicions are either Pidgin (because when running it adds those status settings to the dropdown) or AWN (because I added an applet that could shutdown/restart.

Either way, I'm wondering how to get it back to default. I've already figured out how to restore the panel to its default settings, but this doesn't help, so I'm thinking I must have to reset something else.

Any help is appreciated,

-Rippy

---

### Post by Rippy on 2009-01-02
bump? Surely there's some way to reset the menu...

---

### Post by jbruced on 2009-01-03
Could it be that you have the "logout" installed on your panel and not the "user switcher"?

Tried readding "user switcher" NOT "logout"?

Bruce

---

### Post by WelterPelter on 2009-01-03
A thread of my struggles with the same issue:
 [http://ubuntuforums.org/showthread.php?t=985433](http://ubuntuforums.org/showthread.php?t=985433)

Hopefully of some use. 

Best.

---

### Post by ianhaycox on 2009-01-03
I have the same problem and found that running the update manager, clicking 'check' and entering the root password restored the options.

I'm guessing that there is something privilege related to the options disappearing. Running other system apps might have the same effect but I haven't taken the trouble to find out.

---

### Post by Rippy on 2009-01-03
> **ianhaycox said:**
> I have the same problem and found that running the update manager, clicking 'check' and entering the root password restored the options.

I'm guessing that there is something privilege related to the options disappearing. Running other system apps might have the same effect but I haven't taken the trouble to find out.
Yep, same thing happened when I tried it, but it only lasts as long as you're logged in.

WelterPelter, I'm trying what worked for you in the thread you linked (logging in as a different user), hopefully that works.

Edit: nope, created a new "test" user account with admin privileges, logged in and then back into my account, and there's no change. For the record, it still shows up with the red power icon, there just aren't any shutdown options.

I think it's that Ubuntu uses a custom applet that isn't actually available in the applets list. Because adding "User Switcher" adds an applet identical to what I have now, i.e. without shutdown options.

Would it help if I tried deleting my .gnome directory?

---

### Post by corbinat on 2009-01-03
I've had this same problem, but managed to fix it. I don't really remember how though. It was some setting in system->preferences->appearance I think. I'll try to figure it out again

---

### Post by corbinat on 2009-01-03
Ok I was wrong. Its in System->Administration->Login Window. Click the Local tab and there should be a check-box that says "Show Actions Menu". Make sure that is checked. I'm pretty sure this is what I did to solve my problem.

---

### Post by tenchi19134 on 2009-01-03
[http://ubuntuforums.org/showthread.php?p=6488157&posted=1#post6488157](http://ubuntuforums.org/showthread.php?p=6488157&posted=1#post6488157)

---

### Post by tenchi19134 on 2009-01-03
It's the default power button action.
You didn't mess anything up.
Just right click and add the real power button.

---

### Post by Rippy on 2009-01-04
> **tenchi19134 said:**
> It's the default power button action.
You didn't mess anything up.
Just right click and add the real power button.

What do you mean, right click and add the real power button? If you mean that "Shutdown" applet, that's not what I'm looking for, because that's an actual button that brings up a shutdown/restart menu. I just want my dropdown at the top-right to give me the option to shut down again >_>

It's still displaying all the options again when I do something requiring root privileges (I just updated)...

I also tried the "Show Actions Menu" thing, it was already checked for me, so I don't think that's it. Tried unchecking and re-checking, maybe that changes something.

---

### Post by arad85 on 2009-02-10
Just thought I'd post (in case anyone else is looking) that the following post 

[http://ubuntuforums.org/showpost.php?p=6690478&postcount=9](http://ubuntuforums.org/showpost.php?p=6690478&postcount=9)

restored the suspend/hibernate/restart/shutdown options in the User Switcher applet for me.

---

