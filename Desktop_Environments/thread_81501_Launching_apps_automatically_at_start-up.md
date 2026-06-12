---
title: "Launching apps automatically at start-up"
date: 2005-10-24
forum: Desktop Environments
---

### Post by red devil on 2005-10-24
Hi,
I'm running Ubuntu 5.10, a new install, and I want to have Blam RSS feed reader start automatically when I login to GNOME, in the same way the panel applets such as weather monitor etc run.
Does anyone know any easy way to achieve this?
Thanks
Red Devil

---

### Post by mostwanted on 2005-10-24
Go into System > Settings > Sessions, click on the third tab and insert your command ;)

I'm using the Danish version of Gnome, so the path might not be called exactly that, but you'll find it.

---

### Post by red devil on 2005-10-24
Ah, thanks for that Mostwanted - now if you'll forgive a completely newbie question, what is the command I need to enter (sorry, I'm still learning this command-type stuff). I checked in the properties section of my Blam panel icon, and that simply says 'blam' in the command field, which seems a little simplistic to me.
Red Devil

---

### Post by Stormy Eyes on 2005-10-24
Go to **System -> Preferences -> Sessions**, and you can specify which apps launch at startup. If you want something more flexible and don't mind tinkering, I've [written a HOWTO](https://wiki.ubuntu.com/CustomXSession).

---

### Post by autocrosser on 2005-10-24
You're right on mate!!  I start Gkrellm that way + a few other apps.

---

### Post by autocrosser on 2005-10-24
Just type the name of the app into the area--all lower case....
 
[quote=red devil]Ah, thanks for that Mostwanted - now if you'll forgive a completely newbie question, what is the command I need to enter (sorry, I'm still learning this command-type stuff). I checked in the properties section of my Blam panel icon, and that simply says 'blam' in the command field, which seems a little simplistic to me.
Red Devil[/quote]

---

### Post by davebgimp on 2005-10-24
[QUOTE=mostwanted]Go into System > Settings > Sessions, click on the third tab and insert your command ;)

I'm using the Danish version of Gnome, so the path might not be called exactly that, but you'll find it.[/QUOTE]

Yeah it's a bit different.

   1. Choose System->Preferences->Sessions.
   2. Click on the Startup Programs tab.
   3. Use the Add, Edit, and Delete buttons to manage programs to run at startup.

When you click add, type in the name that calls the program (I've never used it, but I'm guessing it's blam. If you're not sure, take a look for it in /usr/bin/ to get the correct naming.)

---

### Post by red devil on 2005-10-24
Thanks guys - very helpful.
Red Devil

---

