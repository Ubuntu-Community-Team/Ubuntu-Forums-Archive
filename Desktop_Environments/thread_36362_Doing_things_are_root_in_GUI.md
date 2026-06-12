---
title: "Doing things are root in GUI"
date: 2005-05-23
forum: Desktop Environments
---

### Post by jso23 on 2005-05-23
[FONT=Arial Narrow]A Linux/Ubuntu Newbie Question - 

  Sorry if this has been answered a thousand times, but how is root handled in Ubunut?  When I installed Ubuntu, it never asked me about setting up a root account.  I noticed that with my general account, I can't do squat.

  I know how to "sudo bash" in a terminal and all that, but I find it much easier to do real work inside of the X Windows System.

  How can I use root within the Gnome system (GUI, NOT terminal).

  Any help here would be appreciated!

Justin[/FONT]

---

### Post by tnilsson on 2005-05-23
[QUOTE=jso23][FONT=Arial Narrow]A Linux/Ubuntu Newbie Question - 

  Sorry if this has been answered a thousand times, but how is root handled in Ubunut?  When I installed Ubuntu, it never asked me about setting up a root account.  I noticed that with my general account, I can't do squat.

  I know how to "sudo bash" in a terminal and all that, but I find it much easier to do real work inside of the X Windows System.

  How can I use root within the Gnome system (GUI, NOT terminal).

  Any help here would be appreciated!

Justin[/FONT][/QUOTE]
 All root tasks shall be done in a terminal. The root user shall never start gnome or kde. The most common and secure way is to use sudo "the command you want to run as root".

---

### Post by Sam on 2005-05-23
Have a look [here](http://ubuntuguide.org/#usersadministration).

---

### Post by psychicdragon on 2005-05-23
You can use gksudo to run an application as root.

You shouldn't really need to do this except for administrative type tasks. Running as root all the time is a terrible idea and is why windows boxes get owned by spyware etc.

---

### Post by Burgundavia on 2005-05-24
wow, 3 answers and nobody pointed you to our excellent quick read on teh subject:

wiki.ubuntu.com/RootSudo

Corey

---

### Post by jso23 on 2005-05-25
Thank you for all your answers!

Justin

---

