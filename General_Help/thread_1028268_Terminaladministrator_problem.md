---
title: "Terminal/administrator problem"
date: 2009-01-02
forum: General Help
---

### Post by Admiral Yi on 2009-01-02
Hello,
I am running Ubuntu 8.04 using Wubi. The account I am using has no administrator privileges for some reason. I created another account which also does not have administrator privileges. I have tried to switch this in the users and groups menu, but it will not let me select the administrator option. Because of this I cannot use synaptic or add/remove to get new programs. 

My second problem is with the terminal. On my main account (the one I created during the installation process) I cannot use the 'sudo' command. When it prompts me for my password I cannot type it. On my second account There is some text above the 'user@computer:~$' line which is not present on the account that cannot use terminal. On this account I can use the 'sudo apt-get install' command to install programs and it works fine, so why not on the main account?

I hope this makes sense to somebody, because I can't see what i'm doing wrong...

---

### Post by wmdiem on 2009-01-02
what do you mean you cannot type the password when prompted? sudo never displays the password as it is typed.

---

### Post by ibutho on 2009-01-02
If you can create accounts on your installation, then you have administrator privileges because normal users cannot do this. When you are prompted for a password, you will not see anything on the screen when you are entering it. Its a feature not a bug.

---

### Post by Admiral Yi on 2009-01-02
I know it doesn't appear, but it doesn't actually register that I typed anything. Here is a sample:

joseph@joseph-desktop:~$ sudo apt-get install gnome-art
[sudo] password for joseph: 
joseph@joseph-desktop:~$ 

In this case I typed my password (correctly) and hit enter. Nothing happened. On my other account when I do this it actually does something and starts installing. 

Also, I can no longer create new accounts because when I try to 'unlock' the user settings thing freezes and later says that "an unexpected error has occurred"

---

### Post by wmdiem on 2009-01-02
if it didn't get the password it should return and say password incorrect. When it doesn't display anything that usually means that the program ran without printing anything. 
You might try switing to root (sudo su root) and running the command without sudo in front.

---

### Post by Admiral Yi on 2009-01-02
I tried what you said, once again got the same thing:

joseph@joseph-desktop:~$ sudo su root
[sudo] password for joseph: 
joseph@joseph-desktop:~$ 

This copied off my terminal page. Nothing happens when I input my password. When I do it wrong, this happens:

joseph@joseph-desktop:~$ sudo su root
[sudo] password for joseph: 
Sorry, try again.
[sudo] password for joseph: 

It seems to only happen when I give the right password or no password at all. I thought about changing my password, but I can because it won't let me unlock the account and edit it!

---

### Post by hyperdude111 on 2009-01-02
sudo does not show the password, but it still works. Just type your pass and ignore the fact you cant see

---

### Post by Admiral Yi on 2009-01-02
I am ignoring the fact i can't see! I type my password correctly and hit enter! It doesn't recognize it! Here is an exact plan of what I do:

1) Open terminal
2) Type 'sudo apt-get install' then package name
3) Hit enter
4) Terminal prompts me for password, so I type it.
5) It waits for a second, then just comes up with 'joseph@joseph-desktop:~$' again

When I do it on another account I created before I had the access error it works fine...

---

### Post by Admiral Yi on 2009-01-02
Still having these problems, anyone out there who can help?

---

### Post by wmdiem on 2009-01-02
this is out of my league. I have a feeling it is not going to be a nice easy fix. 
Just out of curiousity does gksu work? like, gksu xterm ?

---

### Post by Admiral Yi on 2009-01-02
When I try to run that it asks for my password in a different window. When I enter it it says: 

**Failed to run xterm as user root.**

The underlying authorisation mechanism (sudo) does not allow you to run this program. Contact the system administrator.

---

### Post by wmdiem on 2009-01-02
yeah the only thing I can think to do is reinstall, but someone else might know how to fix it.

---

### Post by Admiral Yi on 2009-01-03
Bump

---

### Post by benson444 on 2009-01-03
What groups are you a member of?
```
groups
```

---

### Post by benson444 on 2009-01-03
If the groups command output doesn't include admin then you can add yourself by booting into recovery mode with
```
adduser username admin
shutdown -r now
```

---

