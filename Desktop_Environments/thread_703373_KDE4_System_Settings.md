---
title: "KDE4 System Settings"
date: 2008-02-21
forum: Desktop Environments
---

### Post by JustinAlf on 2008-02-21
I cannot change my system settings in KDE 4 at all.  Everythging is shaded and will not work!  Even in ROOT!, Anyone have any ideas?

---

### Post by jose_ramirez on 2008-02-22
Hi,

Sometimes I like to "play" with the desktop settings and suddenly I'm not able to see anything. What I usually do is press ctrl+alt+f2 to go to the prompt. On your home directory you should have a .kde4 directory, you can delete everything and restart kde (ctrl+alt+backspace).

Good luck, Jose.

---

### Post by JustinAlf on 2008-02-26
Do I deleate the folder as well?

---

### Post by benerivo on 2008-02-26
It doesn't matter if you delete the folder itself, or not. Either way the result is that there are no configuration files so it makes new default based ones (including the parent folder if neccasary) next time you start something that needs them. Personally i think it's easier just to delete the whole .kde4 folder, then log back in.

---

### Post by jose_ramirez on 2008-02-26
> **JustinAlf said:**
> Do I deleate the folder as well?

Yes, go ahead and delete the folder, no data will be lost, just the settings.

---

### Post by JustinAlf on 2008-02-27
Well, I posted that on a work computer.  I came home and I didn't even have a .kde4 folder.  

Also, it's only the date and time settings and the KDM-Manager and a few other things that don't work.  I can get to the editing menus for them, but they are grayed out.  Do I need to download the KDE4 equivalents to these or what?

---

### Post by jose_ramirez on 2008-02-27
> **JustinAlf said:**
> Well, I posted that on a work computer.  I came home and I didn't even have a .kde4 folder.  

Also, it's only the date and time settings and the KDM-Manager and a few other things that don't work.  I can get to the editing menus for them, but they are grayed out.  Do I need to download the KDE4 equivalents to these or what?

Hi,

Please go to your home directory and do a ls -la and post the results.

Regards,

Jose

---

### Post by eitje on 2008-04-01
Actually, I'm having the same problem as the original poster - he's just not doing a very good job of explaining himself.

Let me try again for him, while also bumping this thread.

I log into my system, which is currently running the Kubuntu 8.04 beta with KDE4.  After my desktop loads completely, I open the Application Loader in the lower left corner of the screen.  I then select the "System Settings" icon that was pre-loaded into my Favorites menu.

From that screen, I can manage things like "Desktop", "Accessibility", and "Keyboard & Mouse".  All of the tabs on each of those pages are accessible and usable to me.  However, if I navigate into "Date & Time" or "Login Manager" (as examples), I cannot modify any of the values there.  All of the options are greyed out and not selectable.

In the past - with KDE3 - there had always been an option to "Enable Administrator Mode", which would allow me to make changes.  That option appears to no longer be available, which is really annoying.

Does that better explain the situation I believe we're having here?

---

### Post by landstalkerx on 2008-05-11
try doing sudo /usr/lib/kde4/bin/systemsettings
I was having the same problem and it worked for me

---

### Post by JustinAlf on 2008-05-14
That also worked for me.  Is there any way to perminantly set it to sudo so that I don't have to type that in all the time?

---

### Post by sixstorm on 2008-05-15
> **JustinAlf said:**
> That also worked for me.  Is there any way to perminantly set it to sudo so that I don't have to type that in all the time?

Yeah, I'd like to know this as well.

---

### Post by JustinAlf on 2008-05-15
I"m to the point where I have given up on KDE 4.  In my opinion, this peice software should still be in the beta phase, as it does not perform very well at all.  This, is a prime example of a peice of software just not working the way it's intended to.  Instead of tarnishing the good name of KDE, they should have waited.  Just an opinion.  I"m done testing KDE4 for now.  I"ll go back to XFCE and Gnome for awhile.

---

