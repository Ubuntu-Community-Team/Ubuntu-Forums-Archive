---
title: "Cursor Selection doesn't work ??"
date: 2009-11-17
forum: Desktop Environments
---

### Post by Julian David Pitt on 2009-11-17
When I select "System-Preferences-Cursor Selection" I am given the option of 26 different cursors to choose from. However I cannot change to any of them, whichever one I select makes no difference to the on screen cursor. You will see from the screenshot that there are two buttons, to install a theme and to go to the theme folder, both of these appear to do nothing at all. Can anyone please tell me if I am doing anything wrong, thanks a lot.

---

### Post by keplerspeed on 2009-11-17
That sounds familiar, I think I found that logging out and back in or a restart updated the cursor.

---

### Post by Julian David Pitt on 2009-11-17
Gday keplerspeed (sorry couldn't resist it)
Do you mean you had to select a fresh cursor and then reboot before you could see it? Thanks.

---

### Post by cygnis1 on 2009-11-21
I am also having problems with Cursor Selection.  I installed a new Cursor Theme and was wanting to try it out.  I downloaded Cursor Selection from the Ubuntu Software Center and moved the new cursor theme into the /usr/share/icons folder.  The theme shows up in Cursor Selection, but it does not change.  I am running Karmic (clean install).  Any suggestions?
Thanks,
Cygnis1

---

### Post by nerdy_kid on 2009-11-21
select theme you want then restart?

my mouse gets really screwed up when i change themes...some apps use the old theme some use the new theme lol a reboot fixes it for me.

---

### Post by cygnis1 on 2009-11-21
I tried restarting and that doesn't work. Usually with anything I try to do in Ubuntu it is hit and miss.  Sometimes whatever I try to change will just mysteriously happen, days after I attempt a change.

---

### Post by sototallycarl on 2009-12-23
I fixed this simply by faking DMZ-White. Example: I use Oxy Black so first back up /usr/share/icons/DMZ-White to /usr/share/icons/DMZ-White.backup then copy the /usr/share/icons/oxy-black folder and rename to /usr/share/icons/DMZ-White. Open the index.theme file in your new /usr/share/icons/DMZ-White folder and change Name = Oxygen Black to Name = DMZ (White)

On a single user machine it works perfectly and it also fixed my login screen cursor which also had this forgetting my settings "feature"

---

