---
title: "Best  way to Remote Desktop into Ubuntu?"
date: 2009-05-17
forum: General Help
---

### Post by rugbert on 2009-05-17
Ok, So I installed xorg and gnome onto my server so I can remote into it and take care of somethings that are easier to do graphicly buuuuut Ive run into two problems.

First and foremost, how to I remote in without user approval? I can use the terminal server client once I install vnc on both the server and client machine (right?) Or I can use remote desktop viewer. Ive used RDV before BUT a user had to be logged in to give me control with. I want to not need that user to OK me in so I can get in when no one is logged in.

Second, when I installed the server I created my normal user rugbert. Well Rugbert cant log in. the login screen doesnt recognize that username. He's listed in the users list via system -> administration -> users and groups but he is greyed out... and root isnt allowed to log in. So I had to open a terminal and create a new user to log in.. What gives?

---

### Post by ninjapirate89 on 2009-05-17
Under System -> Preferences -> Remote Desktop under the Security tab you can uncheck "You must confirm each access to this machine" Hope that helps a little.

---

### Post by rugbert on 2009-05-17
> **ninjapirate89 said:**
> Under System -> Preferences -> Remote Desktop under the Security tab you can uncheck "You must confirm each access to this machine" Hope that helps a little.


That option is not available. Im logged in as thenew user I created since I was not able to log in using the account I created on install.

---

### Post by ninjapirate89 on 2009-05-17
Oh, sorry I couldn't be of more help.

---

### Post by rugbert on 2009-05-17
No worries! I appreciate it tho!

---

### Post by rugbert on 2009-05-17
So is there no way to remote into my machine if a user is not logged in?

---

### Post by geirha on 2009-05-17
I think you'll want to try out [FreeNX](https://help.ubuntu.com/community/FreeNX) 

What is the uid of your user? ("id -u username" will show it) I believe gdm only allows users with uid >= 1000 (or maybe it's >= 500) to log in.

---

### Post by KeyserSoze93 on 2009-05-17
Try XDMCP rather than VNC if you don't need a persistent session. Preferences -> Admin -> Login Window -> Remote -> Same As Local

---

### Post by rugbert on 2009-05-17
> **KeyserSoze93 said:**
> Try XDMCP rather than VNC if you don't need a persistent session. Preferences -> Admin -> Login Window -> Remote -> Same As Local

ok, I installed xnest on my laptop so I can remote in using terminal server client. All I get is a blank screen tho.


VNC will let me log in from a windows machine too right?

---

