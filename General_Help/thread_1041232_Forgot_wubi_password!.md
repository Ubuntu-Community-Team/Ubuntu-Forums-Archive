---
title: "Forgot wubi password!"
date: 2009-01-16
forum: General Help
---

### Post by tombom62 on 2009-01-16
I forgot my user/password and installed wubi, and it asks me for it, but i don't know it, any way to recover it?

---

### Post by endrit10 on 2009-01-16
Turn your computer on.

Press ESC at the grub prompt.

Press e for edit.

Highlight the line that begins kernel &#8230;&#8230;&#8230;, press e

Go to the very end of the line, add rw init=/bin/bash

press enter, then press b to boot your system.

Your system will boot up to a passwordless root shell.

Type in passwd username

Set your password.

Type in reboot

If this doesnt work you can alternatively try this:

Turn on your computer, and as soon as you the Press Esc to enter grub message, press the escape key.

Select the option that says (recovery mode).

Your PC will boot into a shell. Once you get a command prompt, type "passwd username" where the username is your username. 

Enter a new password when prompted, and again when prompted again

Type reboot to reboot your system

Another way is to boot into the system via a live cd open up Applications->Accessories->Terminal
then mount your ubuntu drive if its on /dev/sda1 do this:
mount /dev/sda1/ /media/sda1
Then we chroot into the system:

---

### Post by tombom62 on 2009-01-16
thanks, i am in Windows now, but I will reboot and try that.  I'm a total n00b, so I will come back for more help I am sure.:):popcorn:

---

### Post by nickej on 2009-01-16
New person here, with the exact same trouble.

I've gotten to the root shell with no trouble, but instead of prompting me to input a new password, it's given me a "helpful" list of options such as -a to report the status of all accounts or -d to delete the password of the named account.

Following the helpful hints and entering "passwd -d MyUserName" doesn't do anything but reload the list and the prompt.

Trying the rout of adding "rw init=/bin/bash" to get to the root prompt did precisely the same thing.

Any advice much appreciated.

---

### Post by nickej on 2009-01-16
Never mind. Turns out I was entering a slightly altered (extra letters at the end) version of the correct username. This allowed me to log in and access the "passwd" command, but not have any effect. Reminding myself of the precise username through "ls /home" fixed everything.

It's always the wetware that's the screwiest.

---

### Post by tombom62 on 2009-01-17
Good I got it to work too, thanks.
SOLVED

---

### Post by endrit10 on 2009-01-17
You're welcome.
Too bad noone here will help ME with MY problem.

---

### Post by tombom62 on 2009-01-17
I'd help, but I am more of a n00b than you, sorry.

---

### Post by endrit10 on 2009-01-17
Thats what i mean, there is noone that is helping and this is getting on my nerves.

---

### Post by montanabrooks on 2011-01-29
For some reason my ubuntu partition will not accept my password.  I loaded it with Wubi, and when I choose the ubuntu partition and try to gain access it didn't like my password.  My user name is very creative "noname1" 

When I follow this procedure below, it does not recognize my username...weird....Any thoughts?  I have double checked on the boot prompt into ubuntu. Thank you. I tried the other suggestion but can not get to that kernal.... line or reference point only the GRUB> prompt:
[COLOR=Red]Turn on your computer, and as soon as you the Press Esc to enter grub message, press the escape key.

Select the option that says (recovery mode).

Your PC will boot into a shell. Once you get a command prompt, type "passwd username" where the username is your username. 

Enter a new password when prompted, and again when prompted again

Type reboot to reboot your system[/COLOR]

---

### Post by montanabrooks on 2011-01-29
Got answer here.  [http://psychocats.net/ubuntu/resetpassword](http://psychocats.net/ubuntu/resetpassword)

The user name that was displaying on the screen of the ubuntu login prompt, was not the correct username.  It was displaying windows 7 login name.  So, when I went to change the username at the grub command prompt, I would be putting in the wrong user name.  So I used the ls /home to display the usernames to make sure I was entering the correct username within ubuntu. It came up with a different user name....as suspected..

---

