---
title: "Lockdown Gnome with Pessulus/Sabayon"
date: 2007-11-16
forum: Desktop Environments
---

### Post by christian.paratschek on 2007-11-16
Hi!

I plan to deploy some computers in kiosk mode, so I tried and installed Pessulus and Sabayon.

I created a new user (unprivileged) with the normal user creation tool. Then I installed sabayon and created a new profile.

But: sabayon keeps crashing when I do something. Sometimes it crashes as soon as I try to remove a single icon. Sometimes I can change some settings before it crashes. I managed to create a profile (saving my session after every change and restarting sabayon several times). Then I told sabayon to use my newly created lockdown profile for the kiosk user. 

But sabayon didn't apply the changes to the user profile. When I log in as kiosk user, I get a normal desktop.

Pessulus on the other hand is a very nice tool to lock down Gnome and Epiphany. But I can't do everything with it of course because I never get a chance to remove the Gnome Menu.

So I need sabayon. What is going wrong here? Is my installation somehow borked or is sabayon alpha-quality software?

Regards,
christian

---

### Post by lns on 2007-12-14
Sabayon doesn't seem very stable to me. I've (tried to) use it on a few different systems, and with even basic things like clicking "Edit" on a newly created profile, it crashes.

I've commented on bugzilla.gnome.org..

[http://bugzilla.gnome.org/show_bug.cgi?id=491797]("http://bugzilla.gnome.org/show_bug.cgi?id=491797")

Maybe if more people add comments it will get taken care of..?

---

### Post by nippal on 2008-02-07
i'm seeing the same crash when clicking "edit"  :guitar:
what gives?

---

### Post by keenboy on 2008-02-25
I'm getting exactly the same!!

All I want to do is lock my LTSP server down so that users cannot change the background image, delete or move the desktop launchers and edit menus!

Lockdown allows me to lock the panels but nothing else, gconf-editor is confusing and it doesn't let me do all of the above. It will let me lock the desktop but the desktop launcher icons disappear!

So I turned to sabayon, which looks as if I can do most things I want to do however I haven't been able to test this because it keeps crashing!

And to rub salt into the wound the error tells me to send the contents of a log file that doesn't exist to as a bug report!

:x](*,)

---

### Post by zorkerz on 2008-03-24
im not sure i really understand how this all goes. I have created a unprivileged guest user, can I then use the pessulus lockdown editor to prevent functions only for that guest user?

---

