---
title: "Java browsing problem"
date: 2005-10-20
forum: Desktop Environments
---

### Post by bwainscott on 2005-10-20
I am trying to utilize a CBT course that uses Java.  Using the default version of firefox that came with Ubuntu (1.0.7).  I installed the java plugin, but still no dice.  Any ideas? Thanks

Bob

---

### Post by emperon on 2005-10-20
How did you installed your plug-in ? 
You should create a symbolic link from the plugin to your firefox plugins directory with ln -s command. (Search the forums for details, i can't remember right now).  Is that what you did ?

---

### Post by bwainscott on 2005-10-20
I installed the plugin using synaptic package manager.  Is there something else I am supposed to do?

---

### Post by objorkum on 2005-10-20
If you type "about:plugins" in the adress bar, is the Java plugin there?

---

### Post by bwainscott on 2005-10-20
yes it ahows that the java plugin is installed.  I get the left side frame (Table of Contents) but when I select a chapter the right frome freezes and I get a message from the browser that the applet did not execute correctly.

Bob

---

### Post by bwainscott on 2005-10-20
OK figured this out and I feel stupid now.  Just having the plugin does not suffice, I was using a generic java plugin instead of the one you get in JRE 1.4.2.  Once I installed the runtime environment and adjusted the settings in the console all was well.

Thanks to those  who responded,

Bob

---

