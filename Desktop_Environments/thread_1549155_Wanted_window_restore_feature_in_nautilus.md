---
title: "Wanted window restore feature in nautilus"
date: 2010-08-09
forum: Desktop Environments
---

### Post by sulekha on 2010-08-09
Hi all,

suppose an Ubuntu or Linux user is using GNOME and he/she has opened too many folders , suddenly he/she has to shutdown/ switch off machine due to power failure or some other unexpected reasons , now when he/she reboots the machine he/she can't remember the folders he/she had opened earlier so there should be a window restore feature for nautilus in Ubuntu or Linux in general


Ubuntu or Linux should implement the same window restore feature in nautilus similar to the one existing in Mozilla firefox

see the screen shot here:- [http://s529.photobucket.com/albums/dd339/aarklon/?action=view&current=nautilus-restore.png]("http://s529.photobucket.com/albums/dd339/aarklon/?action=view&current=nautilus-restore.png")

---

### Post by Zorgoth on 2010-08-09
My problem with that is that usually I don't open a folder for very long...  It is rare that you would have to.  When I open my home folder, I want to go to my home folder, not get a message about whether I want to open a bunch of folders I didn't bother to close last time I shut down my computer.

Now, perhaps a command line switch "nautilus --restore-session" would be a good idea.

---

### Post by sulekha on 2010-08-12
I have found a solution :-

There is a setting in "gconf-editor" to tell gnome to save your windows on logout, and re-open them on the next login. Look under **"/apps/gnome-session/options" for "auto_save_session"**

but then this feature should be enabled by default in linux distros
BTW , every one please vote here:-  [http://brainstorm.ubuntu.com/idea/25464/]("http://brainstorm.ubuntu.com/idea/25464/")


[COLOR="Red"]only in one situation this feature is  not working properly. I opened many folders, then i killed nautilus using the application "Force quit" , but when started nautilus  from command line it is not restoring all the windows which were open[/COLOR]

---

### Post by mcduck on 2010-08-12
Like it says, the feature saves your running applications *on the logout*, so it's not going to help you if you kill any programs or your system crashes or anything like that.

---

