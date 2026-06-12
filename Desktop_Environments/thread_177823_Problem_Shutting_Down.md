---
title: "Problem Shutting Down"
date: 2006-05-16
forum: Desktop Environments
---

### Post by sportsfan986 on 2006-05-16
In the proccess of installing updates I lost the buttons for shutting down and rebooting.  When I click on the logout button it has the other four buttons, but no longer shut down or restart.  Thanks for your help.

---

### Post by Dr. Nick on 2006-05-16
[quote=sportsfan986]In the proccess of installing updates I lost the buttons for shutting down and rebooting.  When I click on the logout button it has the other four buttons, but no longer shut down or restart.  Thanks for your help.[/quote] 
Do you have kde and gnome installed? I just recently learned that shutdown and restart can be messed up if your using kdm in gnome or gdm and kde. If that isnt the case I dont know.

---

### Post by angkor on 2006-05-25
I have the exact same problem. I'm using kdm to start gnome and I don't have the Restart of Shutdown buttons in the Quit.. dialog. Just one big Hibernate button on the lower row.

I'm not using kdm out of choice though. It's because of an unresolved issue with gdm:

[http://www.ubuntuforums.org/showthread.php?t=172924](http://www.ubuntuforums.org/showthread.php?t=172924)

---

### Post by Ramses de Norre on 2006-05-25
You're just not able to shutdown gnome when loaded with kdm.. But you can use sudo init 0 for shutdown and sudo init 6 for reboot.
Or shutdown to set a time to wait before shutting down ```
sudo shutdown -[h,r] t
```  h: system halt; r: reboot, t=time to wait in minutes, now for doing it immediately.

---

### Post by angkor on 2006-05-25
[QUOTE=Ramses de Norre]You're just not able to shutdown gnome when loaded with kdm.. But you can just use sudo init 0 for shutdown and sudo init 6 for reboot.[/QUOTE]

I know. I use 'sudo shutdown -h now' or 'sudo reboot' but I'd like to have these buttons for my gf. ;) 

I'd really prefer using gdm again though, but I have no idea how to get that back in order.



Edit: *smiles* Stop editing your post when I'm replying! ;)

Edit2: Are you *really* using the 'Default Style April Fools'?? :);)

---

### Post by Ramses de Norre on 2006-05-25
> **angkor]
Edit: Stop editing your post when I'm replying!  said:**
> 
I always see typo's and bad phrases after I posted..
[QUOTE=angkor]
Edit2: Are you *really* using the 'Default Style April Fools'?? :);)
Ooh yes!:D :cool:

---

### Post by Dr. Nick on 2006-05-25
[quote=angkor]I know. I use 'sudo shutdown -h now' or 'sudo reboot' but I'd like to have these buttons for my gf. ;) 

I'd really prefer using gdm again though, but I have no idea how to get that back in order.



Edit: *smiles* Stop editing your post when I'm replying! ;)

Edit2: Are you *really* using the 'Default Style April Fools'?? :);)[/quote] 
If using gdm to launch kde or kdm to launch gnome I dont think their is a way to get the buttons, what you could do though is to make a simple script and add it to the panel and give it  a pretty icon to make it a simple process

Here is a example of one that should shutdown
```

#/bin/sh

gksudo shutdown
``` 
Just drop that into a new text file and save as "shutdown" and then go to the permissions and make it executable, then add a panel shortcut and it should be pretty simple



OT
I think im gonna be sick after trying out the april fools style, cant think of any worse color combo :)

---

### Post by angkor on 2006-05-26
Thanks, I'll do that since I'm unable to fix gdm.

---

### Post by [cz]_vd on 2006-05-30
At first: I am sorry for my terrible english.

So I had exactly same problem and I was not able to solve it. But before 3 minutes I have played with GDM setup and ... I don't know exactly what I did, but shutdown and restart buttons have appeared.

Here is all what I did (but I don't know if it will be work and I don't know how are these options calling in english):
- change GDM theme
- check "Show menu actions" (or something) and the choice below
- in "security" (fourth from left) tab I pressed the button on the bottom (X-Server settings (?)) and I was trying to change some options there. Then I confirmed that dialog and then I reverted changes back and confirm again (in same dialog - X-Server settings). 
- accept changes

That's all folks friends. Maybe it will be helpfull.

Sorry again for my weak english. And be patient if this post is totally unuseful crap.

---

### Post by dolphinsonar on 2006-09-19
Go throught these steps first, it might be this simple:

System > Administration > Login Window .... [x] Show Actions menu (check this)

[IMG]http://static.flickr.com/86/247725707_ac81551db9.jpg?v=0[/IMG]

---

