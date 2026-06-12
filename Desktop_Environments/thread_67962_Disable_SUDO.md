---
title: "Disable SUDO??"
date: 2005-09-21
forum: Desktop Environments
---

### Post by karuptdata on 2005-09-21
Is it possible to disable sudo and use the regular su then password style in terminal?

---

### Post by egon spengler on 2005-09-21
**sudo passwd root** should do it

---

### Post by bsussman on 2005-09-21
And to answer your question - yes you can disable sudo for any user.

** Be careful to set the root password as above first!**

I see a possibility of screwing yourself up otherwise (needing to be fixed by booting recovery mode).

Then edit the /etc/sudoers file. If you have the plain default, which looks something like this:

 ```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults		!lecture,tty_tickets,!fqdn

# User privilege specification
root	ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin  ALL=(ALL) ALL
``` 

**  NOTE THAT the right way to edit this will be:**

 ```
> su -
> visudo
``` 


 I recommend you change:

 ```
%admin  ALL=(ALL) ALL
``` 

to

 ```
#%admin  ALL=(ALL) ALL
```

To comment it out.

That way you can easily go back if you want.

***As with all security related changes, test  the change to see if it has the desired result.***

You might consider learning and configuring sudoers more for you needs, rather than going to the (riskier) old way (su and root password).

---

### Post by karuptdata on 2005-09-21
ok the reason that i wanted to do this was because a friend and i where having a discussion about security and we both thought that the su way is a bit more secure as far as remote access using terminal and executing scripts i could be wrong which way is more secure against attacks in your opinion??

---

### Post by bsussman on 2005-09-21
In my opinion, the ubuntu feature of disabling the root account (no password) is waay more secure than having a enabled root account. It is not possible to login as root on a box-stock ubuntu system.

The fact that you have to have membership in the admin group is pretty secure unless you are fast and loose with your passphrase (of course you are generating your login passwords using passphrases and disallow regular password access in ssh).

The added benefit is the sudo audit trail.

How many users do you have?  make sure they do not all have membership in admin.

sudo allows many limitations on usage.

I like it. I think the ubuntu way (in this particular area) is pretty good, especially for the target audience and even for more experienced users.

---

### Post by karuptdata on 2005-09-21
Thats what i thought but a friend of mine disagreed....LOL so let me ask you this i have enabled the root account already is there a was to disable again besides in gdmsetup??

---

### Post by bsussman on 2005-09-21
```
> man shadow sez:
``` 

 >  If  the  password  field  contains some string that is not
       valid result of crypt(3), for instance ! or *, the user will not be  able
       to use a unix password to log in, subject to pam(7). 

therefore I would:

 ```
>sudo vi /etc/shadow
``` 

and change:

 ```
root:encryptedpasswordgibberish:13025:0:99999:7:::

``` 
to:

 ```
root:*:13025:0:99999:7:::
``` 
[b]
ONLY CHANGING THE GIBBERISH TO *
[/b]
I believe this is how it was before you set the password.

**BTW there may be a less technical way to do this.**

I looked at mine but I have set the root pswd cuz I sometimes find extended sessions of sudo this and sudo that to be tedious.

---

