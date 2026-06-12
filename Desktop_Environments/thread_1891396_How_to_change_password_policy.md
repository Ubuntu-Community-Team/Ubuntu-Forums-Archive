---
title: "How to change password policy"
date: 2011-12-05
forum: Desktop Environments
---

### Post by forsubhi on 2011-12-05
I try to change my password to 321 but ubuntu tell me that you must choose longer password , what is the solve ? 
please help me !

---

### Post by lisati on 2011-12-05
> **forsubhi said:**
> I try to change my password to 321 but ubuntu tell me that you must choose longer password , what is the solve ? 
please help me !

It's not a good idea to post your password in a public forum because there's too much risk of the bad guys finding it. 

Have you tried using a longer password like the error message suggests?

---

### Post by Paddy Landau on 2011-12-05
A good password is a longer one with a mix of uppercase letters, lowercase letters, digits and other symbols.

See [GRC's Password Haystacks]("https://www.grc.com/haystack.htm") for a fun measure.

If I remember correctly, Linux requires at least six characters, and the password must be "suitably complex" (whatever that means).

---

### Post by forsubhi on 2011-12-05
I want to use short password because every time I want to install program from software center , ubuntu require my password , is there any way to prevent this behavior

---

### Post by Paddy Landau on 2011-12-05
Well, there is a way, but we **strongly** recommend that you do not.

The reason why Linux is free of viruses is precisely because of its security model.

Diverge from the model at your own risk!

If you really want the answer, we can give it to you, but be warned that it's a bit complicated for a newbie.

Please get used to the idea of typing your password when you install or deinstall programs. Once you have typed your password a few times, your fingers will learn the motion and you will be able to type your password quickly.

Think about this: the little time you spend typing your password is much, much less than the huge amount of time you would spend clearing your system of viruses (not to mention the irritation, frustration and anger)!

Believe me, it's worth following the security model. It's been tried-and-tested over many years, and it is one reason why banks (for example) like to use Linux for their servers.

---

### Post by tersogar on 2011-12-05
When doing a fresh install the system will allow the use of a 3 digit password but if I have a longer password in place and want to go to 3 digits, the change is not allow. A stronger password is desirable but the question remains on how to accomplish that task.

---

### Post by Paddy Landau on 2011-12-05
There are three ways that I know of to change the password. I do not know if any of them will allow a password shorter than 6 characters.

[LIST=1]
[*]Open *About Me*. Select *Change Password* and follow the instructions.
[*]Open *Users and Groups*. Select your name; *Change* (next to "Password"); *Set password by hand*; follow the instructions.
[*]Open a *Terminal*. Type [FONT=Courier New][SIZE=2]passwd[/SIZE][/FONT] and press Enter. Follow the instructions. (Warning: It is possible that this method may not change your keyring password, which will cause you problems; however, I am not sure about this.)
[/LIST]
Please do not choose password [FONT=Fixedsys]123[/FONT], because you have posted it on this forum. Having said that, anyone who does manage to hack into your system would [guess your password]("https://www.grc.com/haystack.htm") within seconds with a three-character password

---

### Post by forsubhi on 2011-12-05
I want the answer for educational purposes and my password now is 3 digit 
why don't I able to change it from 3 digit to another 3 digit

---

### Post by Paddy Landau on 2011-12-05
> **forsubhi said:**
> I want the answer for educational purposes and my password now is 3 digit 
why don't I able to change it from 3 digit to another 3 digit
Sorry, I can't answer that. At a guess, I suppose that the installer somehow bypasses the usual password check; it shouldn't do so, and so it should be reported as a bug.

Have you tried the three options I gave? Did none of them work?

---

### Post by haqking on 2011-12-05
it is all down to PAM

man pam.d
man pam_unix
cat /etc/pam.d/common-password

changes that can be made for complexity and length [http://www.deer-run.com/~hal/sysadmin/pam_cracklib.html](http://www.deer-run.com/~hal/sysadmin/pam_cracklib.html)

---

### Post by sisco311 on 2011-12-05
> **forsubhi said:**
> I want the answer for educational purposes and my password now is 3 digit 
why don't I able to change it from 3 digit to another 3 digit

By default, there is a PAM rule which prevents non-root users to set up a weak password. The installer runs as root, that's why you're allowed to choose a weak password for your user at installation time.

You have many options. You can set up a short/weak password as root. Or change the PAM rule to allow regular users to setup a short password. Or you could create a polkit rule to allow your user to install software via Software Center without a password. Or you could configure sudo to allow your user to install software via apt-get or Synaptic without a password.

Some useful links:
[http://en.wikipedia.org/wiki/Pluggable_authentication_module](http://en.wikipedia.org/wiki/Pluggable_authentication_module)
[http://hal.freedesktop.org/docs/polkit/](http://hal.freedesktop.org/docs/polkit/)
[http://ubuntuforums.org/showthread.php?t=1132821](http://ubuntuforums.org/showthread.php?t=1132821)
[uhelp]community/RootSudo[/uhelp]

---

