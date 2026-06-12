---
title: "Shortcut to launch program under other user?"
date: 2005-05-26
forum: Desktop Environments
---

### Post by Hug It on 2005-05-26
Is it possible to create a shortcut or launcher that will start a program as another user? Specifically I'd like to create a shortcut for another user to launch Kismet and have it run with my credentials.

---

### Post by MrTom on 2005-05-26
gksu --user MYUSERNAME COMMAND

will do that using a graphical password prompt

su MYUSERNAME

changes user in a terminal

--MrTom

---

### Post by Hug It on 2005-05-27
Thanks for the information. I like gksu but unfortunately I don't think either of those will work being kismet runs from a terminial. I know how to start it up manually but I was hoping to create a shortcut that would essentually open a terminal, su, supply or prompt for password and then run kismet.

Would it just be a matter of scripting it and assigning that script to the launcher?

---

### Post by tread on 2005-05-27
Yup, scripting and sudo -u should do it I think. You cannot store the password though .. there will definitely be a prompt for a password.

---

### Post by MrTom on 2005-05-27
I think i understand what you want to do now :)

create a new launcher with the Command Field something like:

gksu --user USERNAME 'gnome-terminal --command kismet'

which launches a terminal under the permissions of USERNAME then runs kismet in it.

or you could do

sudo -u USERNAME kismet

and click the run in terminal checkbox. The first one gives you shiny GUI password prompt though.

---

