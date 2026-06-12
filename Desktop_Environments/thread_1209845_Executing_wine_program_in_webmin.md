---
title: "Executing wine program in webmin"
date: 2009-07-10
forum: Desktop Environments
---

### Post by iljabrander on 2009-07-10
Good evening,

I hope that this is the right section for my thread.

I am searching a way to execute a wine program via Webmin commands.
To launch the program I use this command:

```

sh "/home/admin/.wine/drive_c/Program Files/EA GAMES/Battlefield1942MultiplayerDemo/lauched.sh" 

```

And this is the launched.sh file:
```

export DISPLAY=":1001.0"
cd "/home/admin/.wine/drive_c/Program Files/EA GAMES/Battlefield1942MultiplayerDemo"
wine BF1942Demo.exe +restart 1 +serverHost 1 +dedicated 1

```

I exported the DISPLAY variable on top of the shell file but I dont know if this is how it has to be.  

After executing the command in Webmin it gives me this error:
```

Make sure that your X server is running and that $DISPLAY is set correctly.
Application tried to create a window, but no driver could be loaded.

```

How can I let Webmin start a wine program in my X server? I have GDM started.
This command: echo $DISPLAY
Gives me this output: :1001.0

Or is this another problem and cant this be done in Webmin?

---

### Post by iljabrander on 2009-07-13
bump.. 
can somebody help me out?

---

