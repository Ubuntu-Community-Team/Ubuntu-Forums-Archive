---
title: "remote desktop to a windows machine"
date: 2006-06-10
forum: Desktop Environments
---

### Post by sbuntu on 2006-06-10
I am linux newbie and would like your help in this

How do i do a remote desktop to a windows xp machine(work computer) from xubuntu 6.06 ( home )

Please advise

---

### Post by Dalik on 2006-06-10
From the menu.

Applications -> Internet -> Terminal Server Client

This application will allow you to connect to RDP (Remote Desktop) and VNC servers and some others.

Enter the IP address of the machine you wish to connect to, in the protocal option select RDP.  Click connect and it will work if you have a connection to this work computer, you will then be asked for your login details as normal.

Cheers

---

### Post by sbuntu on 2006-06-10
I have xfce environment.I dont see neither Internet nor Terminal server Client
anywhere.

Does it come with Gnome or KDE desktop ?

Do i need to install any packages to have rd

Please help

---

### Post by mgmiller on 2006-06-10
With a default install of gnome, you get the terminal server client.  Very easy to configure. For protocol, use RDPv5 and if you have the bandwidth, under the display tab, for colors choose Use specified color depth and select High Color (16 bit).  It will look and behave just like a windows XP remote desktop session.

---

### Post by scokar on 2006-06-11
[QUOTE=sbuntu]I am linux newbie and would like your help in this

How do i do a remote desktop to a windows xp machine(work computer) from xubuntu 6.06 ( home )

Please advise[/QUOTE]


from a command line, you can type: 

rdesktop -g WidthxHeight machinename&

eg

rdesktop -g 1024x768 myserver&

instead of machinename, you can also use an IP address.

of course you may need to install rdesktop first :) 

sudo apt-get install rdesktop

---

### Post by sbuntu on 2006-06-11
done !

Thanks

I installed rdesktop using synaptic and bam!

It works fine now

Thanks

also i found that inorder to exit from the rdesktop(if you are in full screen mode ,
you wont find the icon to exit the rdestop) you type ALT + CTRL + ENTER and it works

---

### Post by rumli on 2006-06-12
A couple of rdesktop command-line flags that I found very useful were -f and -r:

For example:
```
rdesktop -f -r disk:sync=/home/[user]/sync [windows_xp_machine]
```

"-f" makes rdesktop start up in fullscreen mode.  (As you mentioned, use <ctrl>-<alt>-<enter> to toggle between windowed and fullscreen modes.)

"-r disk:sync=[dir]" shares a folder between your local (Ubuntu) and remote (Windows) machines.  The [dir] directory must exist on your local machine and must be specified by absolute path name (e.g., use "/home/[user]/sync" instead of "~/sync" when specifying [dir]).  The folder will be accessible on the remote machine from the "My Computer" window.  You can then transfer files between the machines by copying to and from this folder.

---

### Post by shredswithpiks on 2006-06-12
don't forget, the package gnome-rdp is handy front end for rdesktop.

---

### Post by pathfinder on 2006-06-12
wow...i tried the remote desktop and i must say its more quicker than the classic one from windows...ubuntu has a way for everything!!!:D 

one problem though...i can't save the password to the file and when i type it into the form the program doesnt pass it to the windows logon tool...so i must type it manually....

---

### Post by sbuntu on 2006-06-15
[QUOTE=rumli]A couple of rdesktop command-line flags that I found very useful were -f and -r:

For example:
```
rdesktop -f -r disk:sync=/home/[user]/sync [windows_xp_machine]
```

"-f" makes rdesktop start up in fullscreen mode.  (As you mentioned, use <ctrl>-<alt>-<enter> to toggle between windowed and fullscreen modes.)

"-r disk:sync=[dir]" shares a folder between your local (Ubuntu) and remote (Windows) machines.  The [dir] directory must exist on your local machine and must be specified by absolute path name (e.g., use "/home/[user]/sync" instead of "~/sync" when specifying [dir]).  The folder will be accessible on the remote machine from the "My Computer" window.  You can then transfer files between the machines by copying to and from this folder.[/QUOTE]



Seems like a handy tip.

Infact i was very annoyed when i couldnt paste what i copied from my ubuntu box to the remote machine and the hour glass kept showing.I had to CTRL + ALT + DEL to kill the windows process.

"windows_xp_machine" 
that you were talking, is it the ip address of the machine ?

---

### Post by eentonig on 2006-06-15
It's explained in the man page of rdesktop. It's only possible when you're windows box is configured to not always prompt for the password.

---

### Post by rumli on 2006-06-16
[QUOTE=sbuntu]
"windows_xp_machine" 
that you were talking, is it the ip address of the machine ?[/QUOTE]

Yep.

---

### Post by 22bsti on 2007-12-07
if your running xfce and dont want as many dependencies tsclient is another option for a front end.

---

