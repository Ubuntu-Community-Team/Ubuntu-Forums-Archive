---
title: "desktop doesn't correspond to /home/user/Desktop !"
date: 2010-09-25
forum: Desktop Environments
---

### Post by nagaprathyush on 2010-09-25
Hii, am fairly new to ubuntu-linux.

While I was trying to drag the Desktop icon to the places sidepane in nautilus file browser so that I can have it above Documents icon, I accidentally dropped it in Documents icon. I immediately deleted the "Desktop" shortcut that was created in "/home/user/Documents" but it was too late already and the damage has been done. When I try to create a new document on my desktop, it says
"Error while coying to Desktop
There was an error getting information about the destination.
Show more details
Error stating file '/home/user/Documents/'
Desktop':No such file or directory"
Now, I know that my desktop now is pointing me to a location in Documents folder which doesn't exist at all. I tried looking for any available settings/options in gconf-editor, but only in vain. 

Is there a way to get my desktop back at all ? :confused: 
Thanks, in advance for your help and time.....

---

### Post by mrhhug on 2010-09-25
check your permissions on the Desktop folder

ls -l /home/user/

---

### Post by nagaprathyush on 2010-09-25
hii, thanks for the reply Mr.Hug...I followed your instructions and got the following output.

drwxr-xr-x  2 user user  4096 2010-09-26 04:09 Desktop

I understand permissions, but whats that number 2 after the permissions ?

---

### Post by mrhhug on 2010-09-25
thats a hard link count [http://en.wikipedia.org/wiki/Ls](http://en.wikipedia.org/wiki/Ls)

im sure your logged in as user

this thread might help you [http://ubuntuforums.org/showthread.php?t=554132](http://ubuntuforums.org/showthread.php?t=554132)

---

### Post by nagaprathyush on 2010-09-25
haa, got it! thanks again for the help mrhhug....
I restarted and everything on my desktop reverted back magically to its default :D

---

