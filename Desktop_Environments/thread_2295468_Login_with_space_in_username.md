---
title: "Login with space in username"
date: 2015-09-18
forum: Desktop Environments
---

### Post by jerry42 on 2015-09-18
[FONT=arial]Ran into an interesting problem this afternoon.  We have about 50 (14.04) workstations where a person can log in to the Ubuntu GUI with either a space at the beginning or the end of their username.  What ??  Exactly.  [/FONT]
[FONT=arial]
LightDM is the display manager with these DT's installed (Xubuntu, XFCE, Unity, lxde)

After authenticating (LDAP),  getting the desktop and opening a terminal,  the environment variable USER could be either of the following (if a space was added before or after username): [/FONT]
[FONT=arial]
**env |grep USER **  

*(quotes added for clarity*)
[/FONT]
[FONT=arial]**USER=" fred"**[/FONT]
[FONT=arial]or[/FONT]
[FONT=arial]**USER="fred "**[/FONT]
[FONT=arial]
If the user does add a space before or after, it breaks several of our shell scripts.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]From a security point of view, I don't think it's huge, considering the username and password must be correct, but sure would like to know how to resolve.  We could (and probably will) strip the whitespace from the $USER in the script(s), but still would like to understand/fix the larger issue.


[/FONT]

---

### Post by TheFu on 2015-09-19
I always remove leading/trailing whitespace from any programs where that is possible to enter. Perhaps the code for the login screen does that too?  Are the HOME directories built with the spaces?  What does the password file/LDAP have? 

Just curious - is AD the ldap source?

---

### Post by jerry42 on 2015-09-19
If the code for the login screen removes any whitespace, it's not doing it now.  Which, in essence, is the issue.  I am really baffled by the fact that it is allowed at all.

Home dirs have NO spaces (as a requirement).  Neither does LDAP (password/username).

We use OpenLDAP as packaged by Ubuntu.

---

### Post by TheFu on 2015-09-19
At login, I'd have the .login or .bashrc fix the USER environment variable spaces.  If it is a real program in any language except sh, ksh, bash, I'd call "getpwent()" to get the userid.

---

### Post by SeijiSensei on 2015-09-19
A quick glance at [login.c]("https://github.com/karelzak/util-linux/blob/master/login-utils/login.c") doesn't show any trimming of leading/trailing whitespace from the submitted username (lines 425 ff).  However trimming might still happen when the username is collected by whatever UI is involved and before the parameter is passed to login.

---

