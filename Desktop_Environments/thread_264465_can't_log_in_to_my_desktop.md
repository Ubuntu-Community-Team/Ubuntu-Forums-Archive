---
title: "can't log in to my desktop"
date: 2006-09-24
forum: Desktop Environments
---

### Post by tomslopez on 2006-09-24
I have a problem trying to log in to my desktop, for a couple of weeks now I have been having this problem, I boot my computer up I get to the log in screen I type in my username then my password and hit enter and it doesn't start to load the desktop, what it does is it goes to a black screen for a couple of seconds asking for my username again and immediately it goes back to the log in screen, it does that everytime I enter my username and password. Is there anything I can do to fix that? please help me out.
btw I have a lot of info on my hard drive so reinstalling the OS would be my last option.
Thanks in advance.

---

### Post by happy-and-lost on 2006-09-24
Did you remove something like bluetooth using synaptic?

If you did, you may have removed the ubuntu-desktop package.

Login on the black screen and "sudo apt-get install ubuntu-desktop"

---

### Post by tomslopez on 2006-09-24
> **happy-and-lost said:**
> Did you remove something like bluetooth using synaptic?

If you did, you may have removed the ubuntu-desktop package.

Login on the black screen and "sudo apt-get install ubuntu-desktop"

Do I have to have the computer connected to the internet?, I have DSL.

---

### Post by oskar.hansen on 2006-09-24
I've have just got the eksact same failure on my laptop. Dont know if it has anything to with new updates or something?

But I temperary fixed it by creating a new user, but that's not a final solution for me... :( But i can log in...

When it happends it buggers about something "glibc" what's that??:confused: 

hope someone can figure this out, dont wanna lose my great install [-o<

---

### Post by oskar.hansen on 2006-09-24
okay googled about it, and this is what saved me...


I removed the ~/.gconf ~/.gconfd and ~/.gnome folders. 

afterwards i could log in again! :D but my gnome-setup was ofcause gone, but that dossent matter right now.. :)

hope it works for you too.. :)

---

### Post by tomslopez on 2006-09-24
How do you delet the ~/.gconf ~/.gconfd and ~/.gnome folders?

---

### Post by oskar.hansen on 2006-09-25
> **tomslopez said:**
> How do you delet the ~/.gconf ~/.gconfd and ~/.gnome folders?

first, when you get the log-in screen hold down Ctrl+Alt+F1

Now you get another loginscreen (in textmode) login here.

If you ls -a now, you will see a list of all your folders, including the hidden.
Make sure you are in your homefolder (you sould be if you logged in with your normal username.) To be sure tab "pwd" in the terminal. The output should be something like /home/[Yourusername]
First, make a backup (in case it's not working)
Eksample:
cp -r .gconf .gnconf_backup
then remove the original folder
rm -r .gconf
do this with the 2 others.

run "sudo reboot"
Now you can log in as normal?

---

