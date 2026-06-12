---
title: "Unity and tightvnc"
date: 2011-05-20
forum: Desktop Environments
---

### Post by m_gustafsson on 2011-05-20
I have a laptop running xvnc4viewer to access a desktop running tightvnc server, and I have problems running Unity when accessing the desktop with this setup. Every time that I log in to the tightvnc server the Gnome desktop is automatically picked and I cannot change it to Unity.

Both the laptop and the desktop run 11.04 and if I sit locally at them, i.e. not using tightvnc, I can run Unity on both of them, with the same user.

The first time I accessed the desktop with xvnc4viewer the laptop was running 10.10 though, and then something complained about not being able to run Unity and switched to Gnome in the xvnc4viewer. Since then I am stuck with Gnome.

I have tried to re-install tightvnc server and remove all its files, but with no success. 

Anyone, who knows how to switch to Unity on my Desktop when running it over vnc? Thanks :)

/M

---

### Post by tonezone on 2011-05-24
I am having exactly the same problem and using ubuntu 11.04. Tightvnc is great, it seems to use less bandwidth out of the box, and allows for even greater bandwidth reduction using compression and quality reduction. I was using about 100 kB/s using with 640x480 graphics and tight compression enabled. Vino which is the default vnc server was maxing out my connection at over 1 MB/s. Also tightvnc is using significantly less processing power than vino was. Since unity is the default desktop on ubuntu and gnome is used by tightvnc, I cannot access any programs that were started in unity using tightvnc. I am also having some strange errors where tightvnc will suddenly disconnect, and I cannot connect to the same xserver session again I need to create a new session. These errors may just be from running tightvnc and vino simultaneously or not restarting or updating after installing tightvnc server, and I'll update if these errors go away.

---

### Post by m_gustafsson on 2011-05-25
Looking in the folder: /usr/share/xsessions/ there seems to be some 
files that are used to pick the current session, or is this not how they are used?
If this is how they are used, what is it that decides which file to use?

tonezone: are you also using xvnc4viewer? Good (for me) that I am not alone :)

/M

---

### Post by tonezone on 2011-05-25
No I am using tight vnc viewer and tight vnc server with the command vncviewer and tightvncserver respectively. I see two files named guest_restricted in the folder /usr/share/xsessions/. I know when I connect with tight vnc viewer, if vino is display 0 and tight vnc server is display 1 then vncviewer <servername>:0 or vnc <servername> connect me to vino and vncviewer <servername>:1 connects to tight vnc.

---

### Post by tonezone on 2011-05-27
I found another rather strange error. Whenever I type the letter d it minimizes whatever window I am on.

---

### Post by m_gustafsson on 2011-05-30
> **tonezone said:**
> I found another rather strange error. Whenever I type the letter d it minimizes whatever window I am on.
If you go to System-Preferences-Keyboard Shortcuts you will find the action to be performed when pressing "d". Just try and disable it.

/M

---

