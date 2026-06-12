---
title: "Launcher creation"
date: 2008-04-10
forum: Desktop Environments
---

### Post by many_miles on 2008-04-10
I have successfully created a customer launcher on my panel, but, it seems to be ignoring my full wishes...

What I want to ultimately do is to click on an icon on a panel which will start an RDP session to a specific computer that I use regularly.  (Let's call it penguin1).

For example, when I type the following at the command-line:
tsclient -x ~/.tsclient/penguin1.rdp
I am successfully presented with the login box for the Windows 2003 Server that I must use.

So, I figured I would create a launcher with that string (tsclient -x ~/.tsclient/penguin1.rdp) in the Command box.

The launcher launches the tsclient program, but, seemingly is ignoring the "-x ~/.tsclient/penguin1.rdp" portion of the command.  It brings up the tsclient program with the last Computer that was connected to in the Computer box.

I've searched for a post without success.  I've also read the appropriate section in the help for assistance, and the help would seem to indicate it should not be ignoring me.

Your time reading this and replying is greatly anticipated and appreciated.

---

### Post by tamoneya on 2008-04-10
keep the command the same but where it says type: and has a pull down box you should select: "application in terminal"

---

### Post by many_miles on 2008-04-10
Thanks for the suggestion...

I just tried that.  The only difference now is that there is an open, unused terminal window in the background, but, still not opening penguin1.

---

### Post by steelcap on 2008-06-28
I got this working by creating a .sh file with the following 

```
#!/bin/sh

# a script to connect to server with tsclient

tsclient -x ~/.tsclient/penguin1.rdp
```

make the .sh file executable and then point your launcher to the .sh file instead of the .rdp file

---

