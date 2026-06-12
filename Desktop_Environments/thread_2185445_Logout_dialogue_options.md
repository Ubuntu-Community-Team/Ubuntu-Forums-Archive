---
title: "Logout dialogue options"
date: 2013-11-02
forum: Desktop Environments
---

### Post by sejhog on 2013-11-02
Is it possible to remove the "Log Out" button from the "Log out dialogue" box (the box that appears with ctrl-alt-del) ?
I am using xubuntu 12.04 with a gnome colors theme.
I have removed the suspend & hibernate buttons but ideally would like to only be left with the Restart and Shutdown buttons.

Alternatively, is there a way to create a main (applications) menu option for shutdown and this would popup a "really shutdown?" dialogue
and a restart menu option whichs pops up with "really restart?" 
Thank you.

---

### Post by JKyleOKC on 2013-11-03
> **sejhog said:**
> Is it possible to remove the "Log Out" button from the "Log out dialogue" box (the box that appears with ctrl-alt-del) ?
I am using xubuntu 12.04 with a gnome colors theme.
I have removed the suspend & hibernate buttons but ideally would like to only be left with the Restart and Shutdown buttons.

Alternatively, is there a way to create a main (applications) menu option for shutdown and this would popup a "really shutdown?" dialogue
and a restart menu option whichs pops up with "really restart?" 
Thank you.If you're referring to the actions available from the "Action Buttons" panel applet that's normally at the extreme right end of the top panel in Xubuntu, right-click the button and select its "Properties." This will get you a dialog that has a list headed "Actions" which lists all of the possible actions for the applet. Simply un-check both of the "Log out" entries, save the changes, log out and log back in (or restart if you no longer can log out) to get the changes loaded into RAM, and you should have what you want.

I never use the ctrl-alt-del shortcut since I'm used to it always forcing a restart; I doubt that these instructions will modify the dialog to which you refer, however. [s]For that one, go to System -> Settings -> Startup and browse the tabs. As I recall one of them controls what is shown by that dialog.[/s]

EDIT: Ignore that previous sentence; I just checked and found I was totally wrong. It's Settings -> Settings Manager -> Sessions and Startup, and doesn't have anything about that dialog except whether to show it at all, or not. Gotta be somewhere else, or I've been dreaming...

In my systems, using the "Action Buttons" panel applet, both the Shutdown and Restart choices automagically show a 30-second countdown dialog; no need for any special menu.

Hope this helps!

---

### Post by sejhog on 2013-11-03
Thanks for the reply, but when I've used the "action buttons" to restart or shutdown it happens immediately with no chance to cancel.
The ctrl-alt-del dialogue box is the same one I get if I click on the applications menu Log out or the action button log out option.
I might just have to look into running a shutdown command at logout (is this possible?)

---

### Post by sejhog on 2013-11-03
The "session menu" button does give the 30 second countdown but I don't seem able to edit it so I end up with all of the Logut, suspend, hibernate, lockscreen options as well as shutdown & restart. It would be good if I could just add these two options to the Applications Menu.

---

### Post by JKyleOKC on 2013-11-05
I'm in the middle of changing my internet services so am a bit late responding. On my systems, the "properties" choice on the logout button of the top panel allows two settings: "Session menu" or "action buttons." I have it set to "Session menu" and can enable or disable each of the items to be shown on the menu. Note that there are two "Log out" choices; one provides the dialog and the other does not.

Also, I am running xfce 4.10, not the standard 4.8, via the PPA -- and this may makes things slightly different, although as I recall they were the same before I installed the 4.10 version.

---

