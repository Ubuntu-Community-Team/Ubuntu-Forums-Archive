---
title: "changing the default image viewer"
date: 2005-03-20
forum: Desktop Environments
---

### Post by wellery on 2005-03-20
How do I change the default image viewer? Gnome website says that I should be able to do this in the preferences -> File Types and Programs. I'm not sure if that was with an older version of Gnome. I don't have this option.

---

### Post by bored2k on 2005-03-20
[QUOTE=wellery]How do I change the default image viewer? Gnome website says that I should be able to do this in the preferences -> File Types and Programs. I'm not sure if that was with an older version of Gnome. I don't have this option.[/QUOTE]
 In your file browser "home" / nautilus whatever you call it , right click on the image > Properties > Open With > and select your application. That file type will open with that always. You do have gnome's option but I dont remember where it is right now ^_^ .

---

### Post by wellery on 2005-03-24
I already tried that before posting this thread and that didn't work. I'm not sure why. It did work when I was using ubuntu warty but it doesn't work with hoary

---

### Post by poyner on 2005-04-14
[QUOTE=bored2k]In your file browser "home" / nautilus whatever you call it , right click on the image > Properties > Open With > and select your application. That file type will open with that always. You do have gnome's option but I dont remember where it is right now ^_^ .[/QUOTE]
as noted above... this doesn't work in hoary..... how can I change the default application for opening images. Thanks

---

### Post by jpadfield on 2005-04-25
[QUOTE=bored2k]In your file browser "home" / nautilus whatever you call it , right click on the image > Properties > Open With > and select your application. That file type will open with that always. You do have gnome's option but I dont remember where it is right now ^_^ .[/QUOTE]

I have managed to get this to work for one particular application.  Once you have done the properties open with step have a look in you /home/user/.local/share directory.  The system copies the applications here but did not assign the permissions correctly.  

Right click on this copy of the application and then select permissions from the menu
Select the Permissions tab
In they are not selected check all of the Execute boxes.

You should now be able to double click on your files and open them with your chosen image viewer.

I hop this helps :-)

---

### Post by tread on 2005-04-25
Hmm, I am not sure I understood that above suggestion, must take a look at the .local directory in more depth.

Before I do that though, here is how I fixed the same problem (it's a hack really).
I wanted to open all text files in gvim and not gedit. Since the first directory in my path was /usr/local/bin, I created a symbolic link called gedit there pointing in reality to gvim. So whenever nautilus wanted to execute gedit, it found it in /usr/local/bin first and loaded that.

---

### Post by DeadOne on 2005-05-28
Hey, I figured it out, and in case someone else hasn't already here it goes:

Right-clic any pic (of the specific filetype you're trying to set up) and click {roperties. The in the "Open With" tab select whatever you want to use and confirm. Done.

---

