---
title: "Gnome Panel will not customize"
date: 2005-09-28
forum: Desktop Environments
---

### Post by bulldogzerofive on 2005-09-28
Made a mistake.

I don't like the ubuntu default look, so i made a user called baseline and customized it to my liking, so now when i make a new user account, all i have to do is type 

$sudo cp -r /home/baseline/* /home/new_user/
$sudo chown -R new_user:new_user /home/new_user

It works like a charm.  However, the Gnome Panels are locked for all the new accounts i create, meaning that while new users get the desktop i like (which is important because the other users in the house are not particularly computer literate and i need to spend time explaining how things work to them), they cannot customize it to the way they like.  You can right click on the panels to open properties, but the dialogue box has a warning at the top that says that some of the properties are locked, and indeed nothing can change.  I cannot change the look, color, add a launcher, or anything else.  So, does anyone know how to fix this?  Also, does anyone know where the configuration file for the panel is?  I have not been able to find it but they are (in my limited experience) usually easier than the GUI boxes.

Thank you

mat

---

### Post by bulldogzerofive on 2005-11-21
I am not sure what caused this, but the next time i rebooted (which was a while), the problem went away on its own.

---

