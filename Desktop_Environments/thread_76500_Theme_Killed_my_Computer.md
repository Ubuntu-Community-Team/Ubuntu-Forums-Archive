---
title: "Theme Killed my Computer"
date: 2005-10-15
forum: Desktop Environments
---

### Post by trubblemaker on 2005-10-15
I'm New to Ubuntu ... Just installed on my laptop.  Then I did an upgrade. And know when I try to boot up before I get to the Login Screen it says.

"There was an error loading the theme Human
Bad size specifier scale"

and when you click on OK it takes you to a login prompt that does nothing ....
You can't login; your screwed..

OK, I look around the forums, one says do an apt get and all is fine. I don't have wirless at home yet so it's not an option, I can burn to cd and move it over so I try out some different themes, 
I edit /etc/gdm/gmd.conf  change Human to : alphacube 
-> Now I'm getting the error message
"There was an error loading the them NewHuman
Can't open file /usr/share/gdm/themes/alphacub/alphacube.xml" 
K but the kicker is that there is a file there and it is named alphacube.xml and it appears well formed.
Just for kick's I also tried NewHuman and Industrial and both gave the same error.  I do Note the Human doesn't have a Human.xml file but doesn't create the error. 

Please help.

---

### Post by dbloom on 2005-10-15
i had an issue where i couldn't use the graphical greeter to log in after upgrading to breezy from hoary. 

first, i backed up the old gdm.conf file.  then i copied the gdm.conf.dpkg-dist as gdm.conf.  that seemed to do the trick for me although i think my issue may have been more specifically with that config file.  note that the gdm.conf.dpkg-dist file is in the same folder as gdm.conf.

---

### Post by trubblemaker on 2005-10-15
well kindof but not really, I get a login screen no worries but then when I log in I get

"there was an error creating the child process for this terminal"

(no style selected?)

---

### Post by trubblemaker on 2005-10-15
K so maybe it my gnome configuration as the new files kindof works kinda doesn't.... why do i feel a looking up way to much documentation coming on?

---

