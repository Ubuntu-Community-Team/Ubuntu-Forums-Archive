---
title: "User login &quot;fails&quot; - goes to shell (xterm/termnial) instead of window manager (gdm)"
date: 2010-01-30
forum: Desktop Environments
---

### Post by ager-wick on 2010-01-30
I had this peculiar problem with an eee PC 901 running Ubuntu karmic 9.10 Netbook Remix, which I couldn't fin any other people writing about having solved, so I had to do it the hard way.

What hapened:
Certain users, when logging in would not fail, but go to an xterm shell instead of the window manager. I could issue the following commands to gain a relatively complete netbook remix environment:
[B][FONT="Courier New"]metacity &
gnome-panel &
netbook-launcher &[/FONT][/B]
It's not perfect but better than nothing!

Creating a new user account actually solved the problem - the new user had no issues. Upon trying to copy the user directory from the old to the new user (and logging in and out a few times), something (currently unknown) happened, which made the new users login go straight to xterm, just like the old one. After this, emptying the user's directory completely still didn't help, nor did deleting the user and creating a new user with the same name. Creating a new user with a different name worked fine all the time.

I then issues this command to see what files existed outside the user's homedir with the name of the user as part of the file name:
([COLOR="Red"]replace $uid with the username[/COLOR] of the user you're having issues with)
[B]
[FONT="Courier New"]sudo du -a / | grep $uid | grep -v "/home/"
[/FONT][/B]
This drew my attention to this file:
/var/cache/gdm/$uid/dmrc

I noticed that deleting the entire directory /var/cache/gdm/$uid/ solved the problem temporarily - the user could then log in without issued. However, after logging out, the file would be recreated and the problem woud reappear.

This was the content of the file /var/cache/gdm/$uid/dmrc :
[B][FONT="Courier New"][Desktop]
Session=xterm
Language=en_GB.UTF-8
Layout=us	altgr-intl[/FONT][/B]

The content will of course very depending on your locale.
Now for the fix:
Change the Session line to:
[FONT="Courier New"]**Session=gdm**[/FONT]
You can do thhis by using this command:
[FONT="Courier New"]**sudo nano /var/cache/gdm/$uid/dmrc**[/FONT]
(again, replace $uid with the username)

Then it works fine!

I have no idea why this happened, but at least now if anyone else gets the same problem, the solution is here.

---

