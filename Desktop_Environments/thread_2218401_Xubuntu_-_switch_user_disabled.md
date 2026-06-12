---
title: "Xubuntu - switch user disabled"
date: 2014-04-20
forum: Desktop Environments
---

### Post by abovett2 on 2014-04-20
I've just upgraded a Xubuntu PC to Trusty, and "switch user" is greyed out on the old "Action buttons" (the personal menu normally at the right of the top panel on Saucy, and left in place because I upgraded from saucy). "Switch User" is missing altogether from the new "Whisker" applications menu. On another PC I had installed the Trusty beta, now updated, the Whisker menu has a "switch user" icon at the bottom, but it's greyed out. Anyone know why? Both PCs have two users set up.

I haven't yet done a clean install of Trusty - can anyone tell me if the "switch user" icon on the Whisker menu is present and working on a clean install?

Thanks

Andy

---

### Post by Toz on 2014-04-20
In Trusty, with light-locker in place of xscreensaver, the switch users method is now to lock the current session and in the unlock dialog, specify the new user's credentials and a new session will be created for you. I created a [bug report]("https://bugs.launchpad.net/ubuntu/+source/xfce4-whiskermenu-plugin/+bug/1285440") for this during testing that has some more info.

---

### Post by abovett2 on 2014-04-21
OK - thanks. I had already realised that you could switch that way (lock, select user) - it was the greyed out "switch user" options I was concerned about. I'm guessing they are left-overs because my installations are upgrades from earlier versions.

Thanks

Andy

---

### Post by Smiff2 on 2014-04-25
i just ran into this issue and i think it will prevent my using Xbuntu which is a shame. i have a hot-seat LAN and need users to be able to easily go back to their existing sessions (ideally from a taskbar applet that allows them to click their name, whether they are logged in or not, like Gnome2 had), and not for example keep starting new sessions. is there a more elegant solution to this currently?

---

### Post by ccrs8 on 2014-04-25
The new session is only created for new users.  If a new user logs in after an existing user locks their session, if the new user locks their session and the original user goes back to log in, they will be brought back to their existing session.  Exact same functionality as old method, just different interface (with an extra click).

---

### Post by Toz on 2014-04-25
> **Smiff2 said:**
> i just ran into this issue and i think it will prevent my using Xbuntu which is a shame. i have a hot-seat LAN and need users to be able to easily go back to their existing sessions (ideally from a taskbar applet that allows them to click their name, whether they are logged in or not, like Gnome2 had), and not for example keep starting new sessions. is there a more elegant solution to this currently?

Actually, you will connect to an existing session, if it exists. Example:
- user1 logs in (new session)
- user1 locks workstation
- user2 logs in (new session)
- user2 locks workstation
- user1 logs back in (connects to existing session)

---

### Post by Smiff2 on 2014-04-25
thanks that sounds hopeful, i will have to play with the UI and see how it works.
is there a way of adding a button (ideally to the panel, but i guess shortcut on desktop would do) to take you to a user name select menu, directly from running session? i.e. not having to first lock the session, which could be confusing for a hot seat situation and tends to lead to people using others' sessions..

---

### Post by Toz on 2014-04-25
> **Smiff2 said:**
> thanks that sounds hopeful, i will have to play with the UI and see how it works.
is there a way of adding a button (ideally to the panel, but i guess shortcut on desktop would do) to take you to a user name select menu, directly from running session? i.e. not having to first lock the session, which could be confusing for a hot seat situation and tends to lead to people using others' sessions..
Yes, you can enable the "Switch Users" option on the Whisker Menu (the new Xfce menu) if you are using it. Right-click the menu and select "Properties". On the "Behavior" tab, there is an option for "Switch Users". This will add a "Switch Users" icon in the Whisker Menu. 

If you want a launcher, just create one with the "dm-tool switch-to-greeter" command.

---

### Post by Smiff2 on 2014-04-27
thanks that works but might be difficult for users to find, as its just  small unlabelled icon. not sure how to display this best yet but it  should be possible. XFCE is back in consideration:

i also ran into problem that locking wasn't working due to lightlocker  not running but manually starting it seems to be ok, might be a live  session issue!

There's no way to change lightdm-gtk-greeter to show a list of usernames  is there? (lightdm-gtk-greeter is what Xubuntu uses that's right?). the way it works with a drop down menu is ok for a few users but  different to what my users are used to, which is a complete list of names displayed vertically. 
lightdm-gtk-greeter seems to  have very limited config options, really all cosmetic. I could install  lightdm-unity but that pulls in loads of gnome.


[SIZE=1]edit: actually this is going to be a problem sorry. Is there any way to fix the "action buttons" panel item to:
[/SIZE]
[SIZE=1]1) make the switch user button either do something or remove/hide it?
2) remove/hide the shutdown and restart options. i don't mind these being on the lockscreen or login screen but i don't want users shutting down direct from their session.
similarly the logout dialogue gives you too many options, i want a simple "yes/no" like ubuntu has.
i should probably start new topic sorry.[/SIZE]

edit2: Sorry, Got it! the Action Buttons applet has options that pretty much do what i want! great. this is looking workable again :)

edit3: just realised i'm not running latest XFCE because one in Xbuntu 14.04 is 4.10/4.11? i might wait and see what 4.12 offers before i commit to using it! i've personally been using XFCE for a while on my own desktop and although 4.10 was much better than 4.08 there are various niggles relating to file management (SMB reconnection, file renaming,) that i'd rather avoid. i'm considering MATE also.

thanks for the advice.

---

