---
title: "Can't access Wally config settings"
date: 2011-02-24
forum: Desktop Environments
---

### Post by Sunships on 2011-02-24
Hello all,

I recently got rid of the different panels on my desktop and replaced them with AWN bars. However, in doing so I have lost my Wally system tray icon, which was my only means of accessing the Wally configuration tool.

Does anyone out there know of another way I can start this tool? Is there a command I can run from the CLI to bring it up?

Or, has a better alternative to Wally come out in the last few months which I should be using instead?

Thanks everyone :)

---

### Post by Phosphoric on 2011-02-24
Try
```
wally
```

seems to work for me.  Note the lower case w.

---

### Post by Sunships on 2011-02-24
Hi phosphoric. Wally is set to run on start up, so the command "wally" gives me an error message saying that an instance of it is already running. Killing wally and running that command just starts the program again. I need a command which will specifically open the configuration menu.

I am exploring other applications, and will post if I have found something a little more AWN-friendly :)

---

### Post by Phosphoric on 2011-02-25
How about uninstalling it via the software centre or synaptic package manager and then re-installing?

I've tried other wallpaper changers in the past and have settled on Wally, so good luck with finding a better one.

Keep us updated. :P

---

### Post by Sunships on 2011-03-01
Hello,

Sorry I disappeared for a while, phosphoric - I will be a bit busy with an upcoming job interview, but will hopefully get back on the hunt for a compatible wallpaper changer ASAP afterwards!

---

### Post by Phosphoric on 2011-03-01
Best of luck Sunships. [-o<

---

### Post by Sunships on 2011-04-07
Alright, this was depressingly simple to resolve in the end!

In the list of available applets for AWN is a Notification Area (systray) applet - the icon looks like a square white tray with four items on it. Adding this to my AWN bar adds icons for Banshee, Desktop-Nova, Dropbox and my network connections. 

The Desktop-Nova icon isn't very helpful though - changing wallpapers doesn't work, so I will try going back to Wally and seeing if it has a corresponding icon in this applet.

---

### Post by Sunships on 2011-04-07
Yes, Wally also has an icon provided by that applet, as do a surprising number of other applications :) Problem solved.

---

