---
title: "Where are Korganizer's config files?"
date: 2006-04-25
forum: Desktop Environments
---

### Post by argotnaut on 2006-04-25
Posted this a couple of days ago in another thread, but got no response -- let's try rewording it a bit.

I had problems using remote calendars with Korganizer, and couldn't get it to start or stay open long enough to delete them. So I deleted the folder ~./kde/share/apps/korganizer/ . This deleted the local calendar, but Korganizer is still looking for the remote calendars. When I open it in a terminal, I get a line like this for each of the remote calendars: ```
libkcal: ERROR: Can't read uid map file 'home/argotnaut/.kde/share/apps/kcal/uidmaps/remote_sgrVk5IQvX'
``` 

Where does Korganizer store the file that tells it which remote calendars to look for? Or is there something else I have to do to get it to stop looking for them?

Thanks.

---

### Post by Neo Ex on 2006-04-25
The KOrganizer configuration file is ~/.kde/share/config/korganizerrc, but inside of it I haven't seen anything about calendars, but I don't use KOrganizer... maybe the voices concerned to the calendars will only be shown if you change the calendars directory or something else. Try looking inside it or deleting it. As far as I know, KOrganizer uses KCalendar for the calendars, so try to search a kcal(endar)rc file (I don't have it, but maybe you have).

---

### Post by flebber on 2006-04-26
I would uninstall Korganizer and then slocate korganiser to see if there are any files folders still related to this available if  yes remove them and then reinstall so that you end up with a clean install. It may pay also to so the smae for Kcalendar and install both freshly and see if fault still exists.

---

### Post by argotnaut on 2006-04-30
Found it -- all of the references to remote calendars were here:

~/.kde/share/config/kresources/calendar/stdrc

I just deleted all of the remote calendar info (and corresponding ResourceKeys) and everything works fine now! No need to reinstall everything.

---

