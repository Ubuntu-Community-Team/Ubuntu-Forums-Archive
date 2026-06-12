---
title: "Edit the startup file"
date: 2005-12-17
forum: General Help
---

### Post by filipenetto on 2005-12-17
Hi people ..

Somebody know where is the startup file, who have the applications wich will start with the system ?

Thanks !

---

### Post by aysiu on 2005-12-17
Any reason you want to go to the file as opposed to going to System > Preferences > Sessions > Startup Programs?

---

### Post by filipenetto on 2005-12-17
Owww, sorry. I know this, but, I want to edit a file who have an application that I want to remove ... This application is the amaroK, that starts with the system.

Tks !

---

### Post by aysiu on 2005-12-17
You want to remove AmaroK altogether?
Or you want to not have AmaroK start when you boot up?

---

### Post by filipenetto on 2005-12-17
Right, the second option: remove it from startup.

---

### Post by aysiu on 2005-12-17
Just a guess, but maybe you could try going to System > Preferences > Sessions and choosing "Automatically save session." Close AmaroK, then log out.

---

### Post by filipenetto on 2005-12-17
All right, it works !

Thank you very much aysiu !!! :p

---

### Post by prizrak on 2005-12-17
It actually can be done with going to System>Preferences>Sessions>Startup Programs. There you look for the entry for any program you don't want started and click delete. If it's not in the list then Aysiu's way :)

---

### Post by thojoh on 2006-02-03
hi!

I was hopeful that this thread ("Edit the startup file") would help me with my question (which has to do with startup actions as well), but I haven't been lucky with it yet.

Here's my problem, maybe someone can help:

I want ubuntu to automatically run the command "setxkbmap" on startup.

At the moment I always have to open a terminal after startup and type the command by hand, then everything works fine. (for some reason, if I don't do that, the keyboard layout is not the one I chose in Preferences>Keyboard)
So obviously it would be nice if the computer does this automatically.

I tried adding 'setxkbmap' in  
System>Preferences>Sessions>Startup Programs, but it doesn't seem to work. Maybe because this is only for programs?

If you can, please give me a hint how I can do this correctly...

---

### Post by dcstar on 2006-02-03
[QUOTE=thojoh]
.......
I tried adding 'setxkbmap' in  
System>Preferences>Sessions>Startup Programs, but it doesn't seem to work. Maybe because this is only for programs?

If you can, please give me a hint how I can do this correctly...[/QUOTE]
Try adding it in with the full path (as found using "whereis setxkbmap").

---

### Post by thojoh on 2006-02-09
That did the trick, indeed...

Thanks dcstar!  :p

---

### Post by Cross020 on 2007-02-25
Im having the same issue, although what i installed was beryl. Now i cant click on anything when x starts up. Can anyone tell me how to remove beryl from my startup from the command console?

Thanks!

---

