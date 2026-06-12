---
title: "Last Gnome Panel"
date: 2005-12-14
forum: Desktop Environments
---

### Post by endersshadow on 2005-12-14
Gnome won't let me remove the last panel from my desktop.  Does anybody know how to do this?  It'd be much, much, much appreciated.

---

### Post by 23meg on 2005-12-14
What error do you get? Did you try erasing its entries in gconf-editor?

---

### Post by endersshadow on 2005-12-14
[QUOTE=23meg]What error do you get? Did you try erasing its entries in gconf-editor?[/QUOTE]

It says, "You cannot delete the last panel."

And what entries would I have to erase in gconf?

---

### Post by endersshadow on 2005-12-14
Oh, hey, I've got an idea, I can just disable gnome-panel from starting on boot...I'll google it, but if you know off hand how to do that, let me know.

---

### Post by 23meg on 2005-12-14
In gconf you'd have to remove the entries below /apps/panel/toplevels I think. But since it doesn't seem to allow removing the last panel, perhaps you can disable it in System / Preferences / Sessions as a last resort.

---

### Post by endersshadow on 2005-12-14
Wow...and I knew that...some days, I question my own intelligence, you know that?

Update: Yeah, not possible.  It spits back out the default panels, even when you try deleting those.  Quite simply put, gnome-panel is like a bad case of herpes...it just keeps coming back.

Thanks for the help!

---

### Post by 23meg on 2005-12-14
Try this: in System / Preferences / Sessions / Current session, change the "Style" property of gnome-panel from "Restart" to "Normal", ```
killall gnome-panel
```, log out and save your session, log back in.

---

### Post by aysiu on 2005-12-14
I agree with 23meg.

Log out *quickly*, though, as the Gnome panel will reload in a matter of seconds (usually five to ten) after you kill it.

---

### Post by 23meg on 2005-12-14
[QUOTE=aysiu]the Gnome panel will reload in a matter of seconds (usually five to ten) after you kill it.[/QUOTE]It shouldn't, since the purpose of setting its style to "Normal" is to stop it from respawning.

---

### Post by aysiu on 2005-12-14
[QUOTE=23meg]It shouldn't, since the purpose of setting its style to "Normal" is to stop it from respawning.[/QUOTE] Oh, whoops. Thanks for the correction.

---

### Post by endersshadow on 2005-12-14
Tried that.  gnome-panel-control also fails when you do it, and it boots right back up no matter what.  Trust me, I've tried about 15 times doing it that way.

I could delete all default toplevels as well as custom toplevels, but I'm scared, because I'm in the middle of finals and don't particularly feel like it.

---

### Post by 23meg on 2005-12-14
Did you try killing gnome-panel-control?

---

### Post by endersshadow on 2005-12-14
[QUOTE=23meg]Did you try killing gnome-panel-control?[/QUOTE]

If I did that, then I'd totally defeat my purpose for killing gnome-panel...I've finally gotten my GnomeBar to totally work with Breezy, and I just wanted to get that last bugger of a panel out of there...but, sadly, it's still there...

It's okay, I can live with it :-D

---

### Post by kanem on 2005-12-14
Do you really need it to not be running? Or is it good enough to just not see it? Autohide still shows a few pixels, but I think that can be changed in gconf so that it's completely hidden when, er, hidden.

Or you could not start a GNOME session. Log into some other minimal desktop environment and start Nautilus.

---

### Post by codejunkie on 2005-12-14
i've got one question here, even if you do set gnome-panel to not restart when killed in the session manager how is it possible to killall gnome panels and log out when you have to use the panel logout option in order to do so?

---

### Post by endersshadow on 2005-12-14
[QUOTE=kanem]Do you really need it to not be running? Or is it good enough to just not see it? Autohide still shows a few pixels, but I think that can be changed in gconf so that it's completely hidden when, er, hidden.[/QUOTE]

Brilliant!

It shows just one pixel...but that's fine with me...looks awesome.  Great idea!

---

### Post by 23meg on 2005-12-14
[QUOTE=codejunkie]i've got one question here, even if you do set gnome-panel to not restart when killed in the session manager how is it possible to killall gnome panels and log out when you have to use the panel logout option in order to do so?[/QUOTE]
```
gnome-session-save --kill
``` should do it, and I bet there are other ways.

---

### Post by 23meg on 2005-12-14
[QUOTE=endersshadow]Brilliant!

It shows just one pixel...but that's fine with me...looks awesome.  Great idea![/QUOTE]

You can set how many pixels will be shown with /apps/panel/toplevels/bottom_panel_screen0/auto_hide_size in gconf, and it can be zero.

---

### Post by endersshadow on 2005-12-15
[QUOTE=23meg]You can set how many pixels will be shown with /apps/panel/toplevels/bottom_panel_screen0/auto_hide_size in gconf, and it can be zero.[/QUOTE]

I set it to zero, but it still peaks up 1 pixel just to say, "I'M HERE!"  Oh well...looks sharp, anyway.  Can't thank you guys enough!

---

### Post by 23meg on 2005-12-15
Hmm, if you mess with the options around there you should be able to get it to disappear completely, but this is just shoving it out of the way; it will still consume resources since it's running and this isn't an ideal solution.

Do a google (and forum) search, I'm sure you'll find that this has been asked and answered many times and you'll get to a real solution.

---

### Post by codejunkie on 2005-12-15
[QUOTE=23meg]```
gnome-session-save --kill
``` should do it, and I bet there are other ways.[/QUOTE]
thanks, do you know to make it just log you out to gdm without displaying the logout prompt im trying to find a couple different ways to get around that xcompmgr bug where it hides it when you click logout?

---

### Post by 23meg on 2005-12-15
You can disable the prompt in gconf; do a key search there and you'll find where.

---

### Post by endersshadow on 2005-12-15
I always do searches before I post, and the only stuff I could find was about Gnome's development and that error code being coded in.

As for logging out, I'd assume you can just kill x (the linux version of the three-fingered-salute), but that may not be the best way to just log out.

---

### Post by codejunkie on 2005-12-15
[QUOTE=23meg]Try ```
gnome-session-save --kill & reboot
gnome-session-save --kill & poweroff
```[/QUOTE]
thanks i'll give them a try.

---

### Post by 23meg on 2005-12-15
[QUOTE=endersshadow]I always do searches before I post, and the only stuff I could find was about Gnome's development and that error code being coded in.[/QUOTE]
I found these two via google:

[http://gnomesupport.org/forums/viewtopic.php?t=4773&sid=e0ea9088b1583316a352b11093d3412e](http://gnomesupport.org/forums/viewtopic.php?t=4773&sid=e0ea9088b1583316a352b11093d3412e)
[http://www.mail-archive.com/redhat-list@redhat.com/msg66064.html](http://www.mail-archive.com/redhat-list@redhat.com/msg66064.html)

I didn't search gnomesupport.org though, check it out, and post a thread there if you can't get it solved; those guys know the game.

codejunkie: I misread you; those won't help you log out to GDM, but as I said (edited) above you can disable the prompt in gconf.

---

