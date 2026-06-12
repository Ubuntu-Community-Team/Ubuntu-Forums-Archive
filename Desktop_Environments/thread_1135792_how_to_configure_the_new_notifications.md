---
title: "how to configure the new notifications?"
date: 2009-04-24
forum: Desktop Environments
---

### Post by iamnotthemessiah on 2009-04-24
im pretty sure i saw a post some weeks ago while i was still in intrepid about how to configure the new notifications, where on the screen they would appear and such, and how to go back to the old style notifications but after googling and searching the forums for the last 20 mins i decided to ask instaed

---

### Post by mjota on 2009-04-24
Another with the same problem here...

---

### Post by timbalisto on 2009-04-24
Right-click on the main menu bar (Applications, Places, System) and choose "Edit Menus" in System/ Preferences is an item called "Pop-Up Notifications" make sure the box next to it is checked then close it. It wasn't visible by default on mine either. 
It doesn't give many options, it's pretty useless in my opinion. Hopefully they'll add more options later.

---

### Post by Aearenda on 2009-04-24
I think the 'Pop-up notifications' preference item is for the old system. To revert, you have to install gnome-stracciatella-session and then use F10 to select that session at login time.

---

### Post by variableenigma on 2009-04-24
Ummm, what?

I'm so annoyed with these new notifications! I don't need to know EVERY SINGLE TIME one of my buddies signs on or off, for example. It's seriously distracting and I want it to stop.

I tried adding the "Pop-Up Notifications" thing to my menu, but even if I change the options, it doesn't make any difference at all. (For example, if I want them to show up in the bottom-left, they still always pop up on the top-right.)

There HAS to be some way to change the preferences! I, too, have been googling this topic (probably for 45 minutes or more), and I see lots of "there's going to be this new feature" type of information, but nothing useful..

---

### Post by Aearenda on 2009-04-24
Maybe I wasn't clear. You can switch back to the old notification system by installing the gnome-stracciatella-session package in Synaptic Package Manager, or by doing this in a terminal:
```
sudo apt-get install gnome-stracciatella-session
```

Then log off, and when the login screen comes up, press F10 to get the options menu. Choose 'Select Session' then choose 'Gnome (without Ubuntu specific components)'. It will ask whether to make the change permanent as you proceed to log in.

I recommend that you persevere with the new system - I didn't like it at first, but after tweaking the Update Manager notification and my Pidgin settings (that's where login notifications come from), I'm happy with it. Mackenzie's comments at [http://ubuntulinuxtipstricks.blogspot.com/](http://ubuntulinuxtipstricks.blogspot.com/) are helpful for Update Manager.

---

### Post by variableenigma on 2009-04-24
Ah.. That is a little bit more clear. I apologize if my first reply sounded rude/angry- I've been very irritable lately, so even when I'm trying to be nice/calm, I probably don't always come across that way. :(

The reality is, I WOULD prefer to stick with the new one, but I want it to update me on the things that I want to be updated on, not every little thing!

The part I'm still confused about is the Pidgin settings.. :confused: How do I change them? (I'm usually really good at figuring this kind of thing out, but like I said, lately I've had a pretty short fuse, and this is just driving me nuts! I feel like pulling out my hair! lol)

---

### Post by variableenigma on 2009-04-24
OH- I got it. It's a plugin!

So to change the new notification preferences in Pidgin, you go to "Tools" -> "Plugins", and it's the one called "Libnotify". You can edit them by clicking "Configure Plugin" or turn them off completely by unchecking it.

:D yaaaay! Sorry for all the complaining- I hope this info helps others!

---

### Post by Aearenda on 2009-04-24
No need to apologise. I'm glad you have worked it out!

---

### Post by chenz on 2011-05-12
Thanks for the tip with gnome-stracciatella-session. I recently updated to 10.04LTS, and the "new" notifications are simply horrible.

---

### Post by Aearenda on 2011-05-13
After so long using the 'new' notifications, I can't imagine *not* using them now!

---

