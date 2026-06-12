---
title: "Root password works in terminal but not desktop."
date: 2005-08-06
forum: Desktop Environments
---

### Post by NPN_Transistor on 2005-08-06
I installed my Ubuntu in expert mode, and it asked me to set a root password. So, I typed in a password and installed. 

When I open a terminal and type "su", it asks me for the password, and I type it in and it works.

But, when I start up a program that needs root priveleges (like synaptic), it asks me for the password. When I type it in, it says the password is incorrect.

I tried this multiple times, and every time it works when I type "su" in the terminal, it works and every time I try to type in the root password in Synaptic it doesn't work.  :-? 

Right now the only way for me to access Synaptic/any graphical tool that requires root priveledges, is to type "su" at the terminal and type in "synaptic" or the name of the program.  :mad: 

P.S. when I try to "sudo" a program from the terminal, E.G. "sudo synaptic", it says, "[username] is not in the sudoers file.  This incident will be reported." 

Help would be appreciated. Thanks in advance.

---

### Post by wytzehoekstra on 2005-08-06
well type in the following in a root terminal:

*export EDITOR=gedit && sudo visudo*

Then add:

*system_username ALL=(ALL) ALL*

At least you will be able to open all the root priveleged programms.
The catch here is that you won't need a passw to open them.
Just click on it and it will open.
Maybe you will have to set the "Users and Groups" properly I  am still working on that.

---

### Post by Fed7 on 2005-08-06
[QUOTE=NPN_Transistor]I installed my Ubuntu in expert mode, and it asked me to set a root password. So, I typed in a password and installed. 

When I open a terminal and type "su", it asks me for the password, and I type it in and it works.[cut] Thanks in advance.[/QUOTE]

You can abble the root user with the command:

#sudo passwd root

Insert the password and ...... enjoy yourself ;-)

To remove root user do:
#sudo passwd -l root

By
Fede

P.S: Google is your friend! Try with key:"root user ubuntu" ;-)

---

### Post by C38a7r1zvl on 2005-08-06
Just use the password of your primary user. The Ubuntu developers changed the kdesu (have no idea how the according program is called in Gnome) program so that it requires the mentioned password although it asks for the root pass ;)

I personally don't like this approach but haven't found a way to change it back to "normal" behaviour yet. Anybody? :)

---

### Post by Fed7 on 2005-08-06
[QUOTE=dePOLL]Just use the password of your primary user. The Ubuntu developers changed the kdesu (have no idea how the according program is called in Gnome)[cut][/QUOTE]

"gksu $nameapplication"

[QUOTE=dePOLL]
I personally don't like this approach but haven't found a way to change it back to "normal" behaviour yet. Anybody? :)[/QUOTE]

I'm agree!

By

---

### Post by NPN_Transistor on 2005-08-06
I think I've made some progress but it still doesn't work!  ](*,) 

OK, so when I start Synaptic or something like that, it asks for a password, I type my normal user password in, (not the root password, my user password) and now it says: 

Failed to run /usr/sbin/synaptic:
Child terminated with 1 status

(This doesn't just happen with Synaptic, it happens with any app that needs root priveledges)

---

### Post by NPN_Transistor on 2005-08-07
Okay, I have worked around this problem by logging into Gnome as root and doing administrative tasks that way. 

But I still would like some help  because it does get a little annoying to log out every time I have to install software/etc.  ](*,) 

Sudo doesn't work, and when I start a program that requires administrative priveledges, it asks me for a password. If I type in my root password, or my user password, the program fails. However, "su" works in the terminal.

---

### Post by whoiam55 on 2005-08-07
I think something confusing going on here, ubuntu/Kubuntu will not ask you root password every time, check for that box again, sometime it ask you(user) password to perform some administrative tasks (I know strange, but it's true)

I'ev set root and my password same to avoid such things ;)

---

### Post by NPN_Transistor on 2005-08-08
Yes, it is confusing, but when I type in my USER password, NOT my root password, the program either doesn't start up or it says, "Child terminated with 1 status" 

Also sudo doesn't work, when I try to sudo something it says, "[username] is not in the sudoers file. This incident will be reported."

---

### Post by hashimoto on 2005-08-08
I think this implicates that your username is not in the sudoer's list, hence you are not allowed to do administrative tasks with sudo (or any graphical too, like synaptic, which require it). To fix, see wytzehoekstra's comment earlier above. "system_username" in that message means your user name.

---

### Post by NPN_Transistor on 2005-08-09
Okay, thanks everyone! Now it works! I just got confused and didn't read the first post!  :-#

---

