---
title: "Where are the compiz settings stored??"
date: 2008-02-09
forum: Desktop Effects &amp; Customization
---

### Post by KrazyPenguin on 2008-02-09
Where are the compiz settings stored??

Sorry if this question is asked elsewhere, but I did a google and searched these forums to no avail.  

Looking in /home/username i do not see a .compiz folder.

Doing a search gives 113 results, and it looks like settings are stored in several places.

The reason why I am asking this, is if I was to do a reinstall of gutsy or install hardy, i could just copy and paste the settings instead of having to go through all that tweaking again.  

Also wondering:  Is there a way to export your compiz settings??

Thank.

---

### Post by PinkFloyd102489 on 2008-02-09
/user/lib/compiz

---

### Post by Tenken on 2008-02-09
You have some compiz settings in your home folder, they're just under ~/.config/compiz

---

### Post by KrazyPenguin on 2008-02-10
I went to this location , ~/.config/compiz
 
and this is what is in the folder:

[gnome_session]
profile = 
plugin_list_autosort = true

The /usr/lib/compiz contains a lot of files that can not be opened by the user.

So these are files that I need to backup if I want to keep all of my compiz settings??

Thanks.

---

### Post by Tenken on 2008-02-10
I'm not 100% sure, but I think most of your settings are stored in gconf xml files. Try looking around in ~/.gconf/apps/compiz

---

