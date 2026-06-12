---
title: "remote desktop in ubuntu"
date: 2007-03-09
forum: Desktop Environments
---

### Post by rajeevbhatta on 2007-03-09
hi

I have started using ubuntu few months ago, working on ubuntu is easier than any other linux distro. I hae a lot of options for customizations. But recently i faced problems with connecting to my linux machine from windows xp. I installed vnc4server on my ubuntu machine and tightvnc client on my windows machine

i ran the following commands on the ubuntu

vncserver :2

and tried connecting from windows, sometimes it got connected sometimes it wont and no gnome is shown only the terminal.

then i tried realvnc, though it always connected but no gnome. i manually ran the following command

gnome-panel

though now i had a gui, it screwed up the gui on my ubuntu m/c

then i tried freenx it never could connect with unix-gnome as the session. I tried vnc session it said it is connected but nothing happened.

that is when i turned in for ur help. I need this to work as i need to access my ubuntu machine from wherever I am working.

---

### Post by srt4play on 2007-03-09
On Ubuntu, enable remote desktop via menu Sytem --> Preferences --> Remote Desktop.

Then connect to it with vncviewer from  your other machines.

---

### Post by frafu on 2007-03-09
Hello, 

srt4play is right: there is a vnc server that is included into ubuntu; by connecting to it, you can see the session used by the local user on ubuntu; a new session is not created when a user connects remotely. I think that the vnc server shipped with ubuntu is called vino. 

By the way, I have moved this thread to the Desktop Environment Forum where it might be more appropriate. 

Francesco

---

### Post by rajeevbhatta on 2007-03-09
Thanks for the reply

i am sorry i did not mention in my previous post that i have already enabled remote desktop on ubuntu but still i will try it again.

thanks for the help though

---

### Post by frafu on 2007-03-10
I think that somebody must already be logged in localy on the remote computer in order to be able to connect remotely to it via vnc. You could achieve this by enabling the automatic login in the "Login Window" Preferences under the menu System->Administration.

---

