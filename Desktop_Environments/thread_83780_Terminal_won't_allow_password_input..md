---
title: "Terminal won't allow password input."
date: 2005-10-29
forum: Desktop Environments
---

### Post by ubuntugranasx on 2005-10-29
I just installed ubuntu yesterday. I am a linux newbie so if this question has a no brainer answer, I apologize. When I was using the terminal at first; I typed a command, it asked for a password, I gave it one no problem; but now when it asks for a password(even though the screen is focused on the terminal), I can't input it. If you type something, it does nothing.  If anyone could help it would be greatly appreciated. Also, Can anyone show me how to select my WinXP to boot on default?

---

### Post by HermanAB on 2005-10-29
Password entry is not displayed in a terminal.  You have to type 'blind'.  Just type the password and press enter.  If you have a knowing slip of the finger, press backspace ten or twenty times, then type it again and press enter.

Cheers,

Herman
[http://www.aerospacesoftware.com/linuxhowtos.html](http://www.aerospacesoftware.com/linuxhowtos.html)

---

### Post by madsmaddad on 2005-10-29
Similarly, I installed Ubuntu yesterday, blowing away Mandake 10.1 because it wouldn't see my USB stick, and ubuntu didn't ask for a root password, so I have no idea what it might be.

Any help?


Thanks,

---

### Post by ubuntugranasx on 2005-10-29
[QUOTE=HermanAB]Password entry is not displayed in a terminal.  You have to type 'blind'.  Just type the password and press enter.  If you have a knowing slip of the finger, press backspace ten or twenty times, then type it again and press enter.

Cheers,

Herman
[http://www.aerospacesoftware.com/linuxhowtos.html](http://www.aerospacesoftware.com/linuxhowtos.html)[/QUOTE]
Thanks. Would you happen to be able to tell me how to set my WinXP as default for start up?

---

### Post by ubuntugranasx on 2005-10-29
[QUOTE=madsmaddad]Similarly, I installed Ubuntu yesterday, blowing away Mandake 10.1 because it wouldn't see my USB stick, and ubuntu didn't ask for a root password, so I have no idea what it might be.

Any help?


Thanks,[/QUOTE]
I think I heard something about root accounts being disabled as default for ubuntu.

---

### Post by Spug on 2005-10-29
Ubuntu does not have a root account by default. Instead, you should use the *sudo* command to run any command that requires root access (i.e. *sudo apt-get*), and input your own password when prompted. If you'd rather want a root account, run *sudo passwd root* to give the root account a password.

---

### Post by NewbieNik on 2005-10-29
Terminal will not display your password when typing, why let people know how long your password is?

root as a user IS enabled, but you need to configure Ubuntu if you want to log-in as it, but why do that when you can "sudo" commands nice and safely?

To make another OS your boot default, use gedit ot alter /boot/grub/sources.list and set the default number to 4 (On a standard install) this number will increase by 2 for each new kernel update. You will need to use "sudo gedit" to do this.

The root password can be set or changed by using "sudo passwd root" type in your current password, hit return, type in the password you want for root, hit return, re-type that password. Voila!

Think that covers everything

---

### Post by ubuntugranasx on 2005-10-29
My problems are solved now.:p Thanks to all you people who responded.

---

