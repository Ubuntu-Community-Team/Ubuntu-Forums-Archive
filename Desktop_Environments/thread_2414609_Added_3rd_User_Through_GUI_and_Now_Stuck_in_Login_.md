---
title: "Added 3rd User Through GUI and Now Stuck in Login Loop"
date: 2019-03-12
forum: Desktop Environments
---

### Post by msanchez on 2019-03-12
I was logged in to my desktop, Kubuntu 18.04. New laptop, new install. No issues. I created a 2nd admin user on the machine. Switched user sessions and logged in successfully. Then Created a 3rd admin user on the machine. Switched user sessions and was stuck in login loop. Tried to switch back to the other successful user sessions and now I'm stuck in a login loop for any user account. All of this was done through the Settings > User Mgmt GUI. 

Until now, I've had no issues with this install or the original 2 user accounts. ](*,) Other factors of consideration: It is the minimal install. Only software I have added thus far is Git, through apt install. Chrome browser. Lastpass extension for Chrome. That's it. 

I've seen other related threads to login loop. It's not .Xauthority. This is KDE and I have not found any solutions or issues posted for KDM. 

Help me Obi Won...

---

### Post by TheFu on 2019-03-12
Have you attempted to use a different, non-GUI, tty to login?   try <ctl>-<alt>-F2 at any point and try to login.  F1-F6 should provide ttys. F7 is the GUI, at least on my Ubuntu variant.  

Once logged in, check the userids ... use the 'id' command. Honestly, I haven't created any userids using a GUI in over 15 yrs.  Are all the names lowercase and unique?  All ASCII (7-bit) characters?

---

### Post by deadflowr on 2019-03-13
kdm hasn't been used in Kubuntu in 6 or 7 years.
Older versions still supported would use lightdm, and newer versions now use sddm.
(sddm defaults to start the graphical display at tty1/vt1/F1/take-your-pick)

For what it's worth, Kubuntu 18.04 should also come with a wayland session (marked as plasma on wayland in the dropdown session listing).
So perhaps double check that's the issue. (It's a long shot, but could be...)

---

### Post by msanchez on 2019-03-13
I checked from tty. All 3 users have an id. Checked /etc/passed with ask. All 3 have a home folder. All 3 usernames are alpha only. 

I tried changing the password of one. Still in login loop. 

I supposed I could delete the 2 added accounts and home folders and see if the original account starts working. That sounds a little stupid. But everything worked until I added the 3rd user. 

> **TheFu said:**
> Have you attempted to use a different, non-GUI, tty to login?   try <ctl>-<alt>-F2 at any point and try to login.  F1-F6 should provide ttys. F7 is the GUI, at least on my Ubuntu variant.  

Once logged in, check the userids ... use the 'id' command. Honestly, I haven't created any userids using a GUI in over 15 yrs.  Are all the names lowercase and unique?  All ASCII (7-bit) characters?

---

### Post by TheFu on 2019-03-14
The point of asking for the 'id' command was for you to post it here so someone else might check the setup. Sorry if that wasn't clear. I don't use KDE and don't use 18.04 (too new for our needs), but I've had 30+ users on 16.04 servers, no issues.  But those systems didn't have any GUI, pure servers.

Sometimes the boot-loop is due to GPU drivers.  If you can login using ssh or from flash-media, can you check the X11 log file in /var/log/? Anything funny there. This assumed the desktop is still using X11 and not Wayland.

BTW, we don't top-post here.

---

### Post by msanchez on 2019-03-14
> **TheFu said:**
> The point of asking for the 'id' command was for you to post it here so someone else might check the setup. Sorry if that wasn't clear. I don't use KDE and don't use 18.04 (too new for our needs), but I've had 30+ users on 16.04 servers, no issues.  But those systems didn't have any GUI, pure servers.

Sometimes the boot-loop is due to GPU drivers.  If you can login using ssh or from flash-media, can you check the X11 log file in /var/log/? Anything funny there. This assumed the desktop is still using X11 and not Wayland.

BTW, we don't top-post here.

Sorry about the top post. And no, didn’t realize you wanted the id  output here. Here it is. And FYI, I deleted the 2 other accounts, but still have the login loop issue. Will check logs next. 

uid=1000(michael) gid=1000(michael) groups=1000(michael),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),116(lpadmin),126(sambashare)

TIA,

---

### Post by TheFu on 2019-03-15
> **msanchez said:**
> uid=1000(michael) gid=1000(michael) groups=1000(michael),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),116(lpadmin),126(sambashare)

I don't think adding userids had anything to do with the root issue.  Showing them for all 3 accounts is what I really intended.

A login loop is often caused by driver problems. GPU drivers, especially. I'm not the best help for that. Sorry.  

But can you boot from alternate media - like a flash drive and look at the boot logs on the HDD? Any errors or warnings should be logged.

---

