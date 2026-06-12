---
title: "Whats up with kuser"
date: 2005-05-24
forum: Desktop Environments
---

### Post by brk3 on 2005-05-24
Whats up with kuser, whenever I try to add a user to certain groups and press ok its just crashes straight away. I saw this bug on bugzilla but obviouly nothings been done about it.
This means I cant give my brother a linux account because when I try to add him to the audio groups etc kuser crashes. This isnt good enough.. :(

Anyone know what can be done? Is there a command line tool to add a user to groups?

---

### Post by JonahRowley on 2005-05-24
[QUOTE=brk3]Is there a command line tool to add a user to groups?[/QUOTE]

Of course there is ;)  **sudo adduser**.  You might need to add some extra groups to the new user, things like dialout, cdrom, audio, etc.  I don't know how friendly this process is, but it can get done.  You can also just launch the Gnome tool to add new users.  I think it's available through **gnome-control-center**.

---

### Post by Cygnus on 2005-06-13
I also get crashes in kuser. I manage to create the users though, But when I uncheck ( or check ) the checkbox for inactive account I crash. So to activate the accounts I have to "sudo passwd new_user".

By the way I was going to see if anyone had entered this in the bugdatabase but I first get a question if I want to accept an certificate (which I do) but then I get asked about the vertificate password. Where do I get that password ?

---

### Post by chandra on 2005-06-13
1. To add a new user from the command line, do the following:

	sudo adduser LoginNameOfNewUser

and answer the questions as asked.  You need not fill in all fields, but you should set the user password and the full name of the user.  The default shell is bash.

2. You may add the new user to typical users' groups, one group at a time, by doing the following:

	sudo adduser LoginNameOfNewUser cdrom
	sudo adduser LoginNameOfNewUser floppy
	sudo adduser LoginNameOfNewUser audio
	sudo adduser LoginNameOfNewUser plugdev
	sudo adduser LoginNameOfNewUser video

(I am unsure of plugdev but think it is the group for devices like USB flash drives.)

3. The new user is assigned a group ID (gid) that is identical with their login name by default.  If you wish that user to have read access to your files, do

	sudo adduser LoginNameOfNewUser YourLoginName

4. Vice versa, if you wish to have read access to the new user's files, do

	sudo adduser YourLoginName LoginNameOfNewUser

5. Confirm the assigned groups by doing

	groups LoginNameOfNewUser

This command line fix is needed because the Kuser setup in Kubuntu does not work properly at present.

---

### Post by Takis on 2005-06-13
This is a rather poor effort on KUser's side, I think. Basic administration programs should not be crashing left, right and center, *especially* when all it needs to do is run a shell command! I'm guessing it's probably reading/writing its data directly to the appropriate file and having jigs with that. If I get a bit of time (and learn how to use adduser, etc) I might write a simple GUI that works through command line interfaces.

Keep an eye on this thread in the coming months.

---

### Post by Cygnus on 2005-06-14
I don't think it's a good idea to create yet another tool for doing these things. Just confusing for the user. Better find out why Kuser is crashing and fix it.

---

### Post by Takis on 2005-06-14
He-ey open source. Good point.

After having a quick look at it, it shows three modes it "can work in". Not so sure if it does actually work. The modes are File, LDAP and System.
System just reads settings, it doesn't allow any writes.
I'll see if I can implement something.

---

### Post by Takis on 2005-06-14
[http://lxr.kde.org/source/kdeadmin/kuser/](http://lxr.kde.org/source/kdeadmin/kuser/) 
Euuuuuugh that's a lot lot more code than I was expecting/hoping for.

---

### Post by suziequzie on 2005-11-04
[QUOTE=chandra]1. To add a new user from the command line, do the following:

	sudo adduser LoginNameOfNewUser

and answer the questions as asked.  You need not fill in all fields, but you should set the user password and the full name of the user.  The default shell is bash.

2. You may add the new user to typical users' groups, one group at a time, by doing the following:

	sudo adduser LoginNameOfNewUser cdrom
	sudo adduser LoginNameOfNewUser floppy
	sudo adduser LoginNameOfNewUser audio
	sudo adduser LoginNameOfNewUser plugdev
	sudo adduser LoginNameOfNewUser video

(I am unsure of plugdev but think it is the group for devices like USB flash drives.)

3. The new user is assigned a group ID (gid) that is identical with their login name by default.  If you wish that user to have read access to your files, do

	sudo adduser LoginNameOfNewUser YourLoginName

4. Vice versa, if you wish to have read access to the new user's files, do

	sudo adduser YourLoginName LoginNameOfNewUser

5. Confirm the assigned groups by doing

	groups LoginNameOfNewUser

This command line fix is needed because the Kuser setup in Kubuntu does not work properly at present.[/QUOTE]

Okay, after using kuser (which caused problems: kde could not be loaded) I tried using this method. And still the problem exists. While loading kde, an error message occurs while loading the panel. For some reason it could not talk to klauncher. :( 

I am using kde3.5 beta 1 on Breezy, if that helps any. Please advise, as I am looking forward to teaching my boyfriend (said new user) how to use linux.

suziequzie

---

