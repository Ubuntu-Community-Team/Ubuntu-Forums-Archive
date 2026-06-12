---
title: "How can I install software without being logged in as a user."
date: 2009-02-20
forum: General Help
---

### Post by mprogrammer on 2009-02-20
Hi I'm trying to install software on ubuntu and I'm logged in as a normal user. when the screen prompts me to enter the password I enter my admin user password which of course it rejects because the user in session is not that admin user. Do I have to log out and log in again as an admin or is there a way I can get around this without having to log out?

I know one answer maybe use the terminal but is there another way to do that without using the terminal? I mean using gnome?

---

### Post by mprogrammer on 2009-02-20
another question is there actually a user called root or what's meant by that is the name I entered when I setup ubuntu?

---

### Post by mb_webguy on 2009-02-20
The password you enter when prompted should be that user's login password, not the admin user's password.  You're not logging in as a different user, you're simply gaining temporary administrative privileges.

As to your second question, "root" is the standard superuser (or in Windows terms, Administrator) account in Linux and other Unix-based systems.  It is disabled by default in Ubuntu, requiring you to enter your password to gain temporary administrative privileges, which is both easier and safer than logging in as root.

---

### Post by mprogrammer on 2009-02-20
I know, but I didn't grant myself those privileges as a root. So I was wondering if there's a way that I can do that as in su root? or did you mean I don't need those privileges??

---

### Post by adult swim on 2009-02-20
what happens when you type in the user password for the user you are logged in as?

---

### Post by mb_webguy on 2009-02-20
The account created when you installed Ubuntu automatically has the ability to gain temporary admin privileges by entering its password when prompted.  If you made an additional account for yourself using System->Administration->Users and Groups, then unless you specified otherwise when you created the account, it can't gain temporary administrative privileges.  In this latter case, you would have to log in using the former account, and then enter your password when prompted to gain temporary administrative privileges.

[This page]("https://help.ubuntu.com/community/RootSudo") might shed some light on things.

---

### Post by dcstar on 2009-02-20
> **mprogrammer said:**
> Hi I'm trying to install software on ubuntu and I'm logged in as a normal user. when the screen prompts me to enter the password I enter my admin user password which of course it rejects because the user in session is not that admin user. Do I have to log out and log in again as an admin or is there a way I can get around this without having to log out?
.........

The default account that was set up when Ubuntu was installed has administrator rights and can install software, if subsequent accounts have been created without admin rights then they cannot do administrator tasks like installing software.

You need an account with administrator rights to give the account those rights, or just have the admin rights account install the software.

---

### Post by mprogrammer on 2009-02-20
thanks a lot guys!! I'm still wondering about the word root though is there another user other than the first account created call "root" or that's just a label??

---

### Post by adult swim on 2009-02-20
or if you wanted to make things a little more complicated, but not too much, you could grant the user that you are now root priveleges.

---

### Post by jocko on 2009-02-20
> **mprogrammer said:**
> I know, but I didn't grant myself those privileges as a root. So I was wondering if there's a way that I can do that as in su root? or did you mean I don't need those privileges??
Ubuntu don't use a "root" account, but the first user (the one created during install) have the right to gain temporary administrative rights by using sudo.
If you need to run a command with administrative privileges, just type "sudo" before the command in a terminal and type your own password.
Gui programs that asks for a password also does not ask for any root password, it asks for the user's password.
So, as long as you log in as the user you created during install (or another user that is member of the group "admin"), just type the password it asks for (= your password).

---

### Post by jocko on 2009-02-20
> **mprogrammer said:**
> thanks a lot guys!! I'm still wondering about the word root though is there another user other than the first account created call "root" or that's just a label??
Actually, there is an account named "root", but by default it does not have a password, which makes it impossible to login directly into that account.
That's a security feature which makes ubuntu a little bit safer than other linux distributions.
A user that is a member of the admin group can still become logged in as root in a terminal by any of these commands:
```
sudo su
sudo -i
sudo -s
```
But usually you just need to run one single command with admin rights:
```
sudo [COLOR=Blue]*command*[/COLOR]
```

---

### Post by mprogrammer on 2009-02-20
Thank you that's clarifying.

---

