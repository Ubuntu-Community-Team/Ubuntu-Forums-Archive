---
title: "need help installing bootSplash screen"
date: 2006-06-04
forum: Desktop Environments
---

### Post by randell6564 on 2006-06-04
Hello everyone!

I'm trying to install a new 'Boot screen'.

I downloaded a 'zip' file and its sitting on my desktop. It's name is: 'evil-elf-li.zip

and it's suppose to be installed as a boot screen.

Can anyone help me to install it?

Thanks!

Oh... and by the way, This is for 'Ubuntu Breezy 5.10'!

---

### Post by Rondonjin on 2006-06-04
[QUOTE=randell6564]Hello everyone!

I'm trying to install a new 'Boot screen'.

I downloaded a 'zip' file and its sitting on my desktop. It's name is: 'evil-elf-li.zip

and it's suppose to be installed as a boot screen.

Can anyone help me to install it?

Thanks!

Oh... and by the way, This is for 'Ubuntu Breezy 5.10'![/QUOTE]

It should be the same. Look in your Administration menu for 'Login Window' Supply your password and when it opens drag the file on your desktop over to the theme window, select it from the list close Login window.

Wayne

---

### Post by Nonno Bassotto on 2006-06-04
[QUOTE=randell6564]
Oh... and by the way, This is for 'Ubuntu Breezy 5.10'![/QUOTE]
Then why are you posting in a Dapper forum? :confused:
Anyway, you should be more precise. There are various implementations of boot splash programs; I can mention bootsplash, fbsplash, splashy and usplash. As you can guess from the name Ubuntu defaults the latter.
Some of these are easily themeable, some not (usplash is not), and I cannot guess what splash the theme you downloaded is for. You can search this forum for an howto with the keywords bootsplash, fbsplash, splashy or usplash, depending on what you want to install.
If you send a link to where you downloaded this thing I can be more precise.

I'm not even sure you want to install a bootsplash. Maybe that's just a grub backround? Then you can have a look here
[http://ubuntuforums.org/showthread.php?t=89916&highlight=grub+splash](http://ubuntuforums.org/showthread.php?t=89916&highlight=grub+splash)

In either cases, be sure you understand what you are doing, it is difficult (or at least tedious) to recover when you are not able to boot properly.

---

### Post by Nonno Bassotto on 2006-06-04
Sorry, maybe I didn't understand. If this is just an image to be displayed at login time, then follow Rondonjin.

---

### Post by randell6564 on 2006-06-05
> **Nonno Bassotto]Then why are you posting in a Dapper forum? :confused:
Anyway, you should be more precise. There are various implementations of boot splash programs said:**
> http://ubuntuforums.org/showthread.php?t=89916&highlight=grub+splash[/url]

In either cases, be sure you understand what you are doing, it is difficult (or at least tedious) to recover when you are not able to boot properly.

Sorry about that!

I didnt realize that I was in a dapper forum.  

Anyway...

what I'm trying to install is a new 'GDM screen' from gnome-look.org.

They are 'tar.gz' files and I dont know how to install them!

I want to add a new image to 'system>administration>login screen setup instead of using whats already available.

---

### Post by Nonno Bassotto on 2006-06-05
In system>administration>login screen setup you find an Add... button, which you can use, as the word says, to add new screens.
I'm not sure I understood well: if you already tried Add and got some error message, please let me know.

---

### Post by randell6564 on 2006-06-05
Well, I finally got it!

For some reason when the tar.gz file that I was trying to install was on the desktop, my 'login setup manager' could not see it.

But once I created a directory and moved the file into that directory, THEN I could install it with the 'login screen manager'!

Thanks!!

---

