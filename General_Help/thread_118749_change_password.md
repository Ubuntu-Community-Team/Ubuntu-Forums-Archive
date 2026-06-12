---
title: "change password"
date: 2006-01-17
forum: General Help
---

### Post by jsmidt on 2006-01-17
I posted something like this a few days ago but I want to be more clear:

I was wondering how to use sudo, but make it so that my user password is different than the password for sudo.  

If I run "passwd jsmidt"  in the terminal it changes both my user and sudo password.  How can I make them seperate.  Use one to log in, and the other to do superuser things.  I know su works like this but I would like to keep sudo.

---

### Post by soulestream on 2006-01-17
interesting question. I went through man sudo and didnt see anthing that looked like it would help. You could create a second user and then use sudoers option to sudo as a different user, but then your permissions/ownership is probably going to get screwed up.

Maybe you should clarify why you would want to do this. You can limit the commands a sudoer has access to, maybe that would be a better option.

then use su for the rest.

soule

---

### Post by lamego on 2006-01-17
I havent tried this, but maybe "sudo passwd root" will do it ?

---

### Post by soulestream on 2006-01-17
> I havent tried this, but maybe "sudo passwd root" will do it ?

wouldnt that just change your su password?


soule

---

### Post by lamego on 2006-01-17
That would change the root user password, as far as I understand it should be the one required for both su/sudo .

---

### Post by jsmidt on 2006-01-17
Yeah I've been searching too.  Sudo locks your root password.  Thanks for the help.

---

### Post by manicka on 2006-01-17
Basically what you want is to be able to use 'su' like in other distros with a different  password for admin tasks...no?

You can activate the root account using this howto

[http://www.ubuntuforums.org/showthread.php?t=31053](http://www.ubuntuforums.org/showthread.php?t=31053)

Then use 'su' instead of 'sudo' at the CLI

N.B. I would recommend only using this method to activate the root account for 'su' purposes and would not recommend logging into an x session as root... for any reason.

---

