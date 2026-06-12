---
title: "Should ubuntu session startup program be 1-2min slow?"
date: 2008-02-04
forum: Desktop Environments
---

### Post by .neo on 2008-02-04
I have to stratup firefox upon auto-login and have it auto-restart in case firefox process fails.

For those purposes I've been advised to use a while loop script, which I did... The script works fine if I call it from terminal myself ie. Firefox will start in a second or two. The problem I have is that when I add the script call as the only entry to "Startup Programs" (I've disabled/unticked all the others) in System>Preferences>Sessions Firefox (command line goes: "sh /firefox-forever.sh") it takes, literally, a minute or two to start Firefox upon login?

However, I noticed that if immediatelly after login (whilst still waiting for Firefox to start) I try to open a terminal in the just started Gnome session and type in it "ps -e", I do see that bash process was started (there's a line there that goes something like "4465 pts/0 00:00:00 bash")...?

Any way to check what's taking Gnome so much to start Firefox up from the script?! Are there any other ways to see what's going to be started when Gnome log in occurs? 

Plz help, I've run out of ideas... :) I've even tried changing the chmod on firefox-forever.sh file - which is in / - to mode 4755 <- that means executable in hope that should help, right?!

A COUPLE OF NOTES

As stated earlier, the bash process starts upon login which is set to be auto-login in the System>Administration>Login Window>Securit>Enable Automatic Login...? And, what might be of some importance too, I've just installed minimal Gnome on my machine! Not the whole ubuntu-desktop virtual package, which would be very wasteful in my case...

Any help would be greatly appreciated! TIA

**EDIT**

*Another thing I've just noticed is that there's a loooong delay (again a minute or two) if I try to click shutdown before the shutdown/restart/log out/switch user dialog appears!?*

PLEASE ANY1 HELP!

---

