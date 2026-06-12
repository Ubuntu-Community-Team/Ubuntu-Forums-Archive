---
title: "Doom 3 freak sad as hell"
date: 2005-07-31
forum: Gaming &amp; Leisure
---

### Post by storybookhero on 2005-07-31
hey I have a copy of Doom 3 native for linux and I have the copy for windows. I have successfully installed it on suse 9.3 and it worked beautifully...infact better than the windows version. but for some reason I'm having trouble installing it in Ubuntu. It keeps telling me that Its unable to save the executable file to the location /usr/doom3/bin. 

I've tried to run the install again and again and no luck..please help

---

### Post by Mishura on 2005-07-31
Eh?  "/usr/doom3/bin?" ?  Asking to "SAVE" the executable?  This is during the install process, right?

Usually, it puts the executables in "/usr/local/games/doom3" and symlinks the "doom3" executable to "/usr/local/bin".  Then everything should work...  Can you give some more details?

Here's something you "can" try, in the meantime:

Download the Linux installer from ID Software's FTP site (ftp.idsoftware.com) and browse around til you find the doom (or doom3) folder, and its under the /Linux folder.  it will be the smaller file,  the bigger one is the demo.
Run it.
Then copy all your *.pk4s into the base directory (I forget what the folder name is called... all Quake/Doom games have em..)

Symlink "doom3.sh" to /usr/bin or /usr/local/bin using the command:  ln -s /usr/local/games/doom3/doom3.sh /usr/local/bin/

Should just work nicely.  *Should*.

---

### Post by Curlydave on 2005-07-31
Probably another permission error.

---

### Post by varunus on 2005-07-31
Did you run the installer with "sudo"?  It wants to copy files to places only root can access, so you need to start it with sudo...

---

### Post by artinla on 2005-08-01
I can tell you from experience that our kernel has a real issue with the type of copy protection that they use on D3.  IF you happen to be using a burned copy of D3, forget it.

I had to go out and buy a legit copy to install the expansion pack.

Just an FYI.

You might try a sudo chmod 755 /usr/bin to give read and execute permissions to everyone for /usr/bin.

If that doesn't work, you might try 775 instead, temporarily to see if that fixes it.

Good luck,

Art

---

### Post by FNM on 2005-08-29
[QUOTE=varunus]Did you run the installer with "sudo"?  It wants to copy files to places only root can access, so you need to start it with sudo...[/QUOTE]

How do I do that?

---

### Post by TristanMike on 2005-08-30
[QUOTE=FNM]How do I do that?[/QUOTE]just add "sudo" without quotes, before whatever you type in the terminal ie "$ sudo blah blah"

---

### Post by FNM on 2005-08-30
[QUOTE=TristanMike]just add "sudo" without quotes, before whatever you type in the terminal ie "$ sudo blah blah"[/QUOTE]

bstckwll@ubuntu:~$ sudo .doom3-linux-1.1.1282-demo.x86.run
sudo: .doom3-linux-1.1.1282-demo.x86.run: command not found
bstckwll@ubuntu:~$

Am I missing something? Why is it so difficult to run a .run file?

---

### Post by ACK!! on 2005-08-30
[QUOTE=FNM]bstckwll@ubuntu:~$ sudo .doom3-linux-1.1.1282-demo.x86.run
sudo: .doom3-linux-1.1.1282-demo.x86.run: command not found
[email]bstckwll@ubuntu:~$doom3-linux-1.1.1282-demo.x86.run[/email]

Am I missing something? Why is it so difficult to run a .run file?[/QUOTE]


why have you got a dot in the command.

To tell linux of any type to run a command in the current dir as root:

sudo ./doom3-linux-1.1.1282-demo.x86.run

instead.

If the command is right its not that hard.  I just wish I had the hw to run doom3.

:(

---

### Post by twowheeler on 2005-08-30
It's not difficult.  Change that to "sudo ./doom3-linux-1.1.1282-demo.x86.run".  

The dot in front of the file name means it is a file name that starts with a dot.   Usually those are hidden config files.  You don't want that.

The dot-slash "./" is completely different.  It means "look for the file in the current directory."   Then it sees the rest of the string as the name of the file to run.

This is not different in ubuntu vs. any other linux flavor.  This is basic command line usage. 

BTW make sure the file has executable permissions.  You can check that with "ls -l".

---

