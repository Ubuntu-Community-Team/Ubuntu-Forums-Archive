---
title: "Random password"
date: 2006-07-03
forum: Desktop Environments
---

### Post by krisravn on 2006-07-03
When a create a user I want to make a random password for that user. How do I do that?
Normally a just type 'adduser newuser' and then It ask for a couple og things, one of them is what password the user wants, here I want it to use a random password, its that possible?

Regards
krisravn

---

### Post by woedend on 2006-07-03
have you tried using the users & groups tool under the admin menu?  I'm not sure if it has that option for each user, but it does for root.  Sorry i'm not around to look at it ATM to be sure.  HTH

ps - out of pure curiosity...what is the reason for this?

---

### Post by krisravn on 2006-07-03
I need a script to make the job, so a can't use a gui toolkit

---

### Post by pepolez on 2006-07-03
From a quick search, there doesn't seem to be a way to do this but I found this shell script that will randomly generate a password and output it to the terminal. 

[http://www.osix.net/modules/article/?id=570](http://www.osix.net/modules/article/?id=570)

It could probably be adapted to perform the function you require

---

### Post by Ramses de Norre on 2006-07-03
Use the --disabled-password option with adduser.

EDIT: do you mean random password like root has by default? If so use my suggestion, otherwise look into the post above.

---

### Post by krisravn on 2006-07-03
I nedd a random password set by default. But if a use use --disabled-password, how do a see what password was generated?

---

### Post by Ramses de Norre on 2006-07-03
I think I understood you wrong, the system used for disabling root password is also called a random password, it's just an * in fact and you can set it through useradd with the --disbale-pasword option. But what you probably want is that the script generates a password for the user and tells you which password it is.

---

### Post by ardchoille on 2006-07-03
You can use a couple of commands to come up with a random password. The command is this:

```

echo password type | md5sum | cut -c1-8

```

Here's how it works. run the command with "type" replaced by something like "email" or website or friend-phone and "password" replaced with some master password that only you know and the output will always be the same 8 character password. Change what you use for "type" and you'll have a different password. 

The idea is to use the same master password with different "type" words and you only have to memorise one master password for several different things. You can get longer or shorter passwords by changing the -c1-8 to -c1-10 (for 10 character passwords) or -c1-6 (for 6 character passwords)

I use something like 
```

echo masterpass amazondotcom | md5sum | cut -c1-10

```

which outputs: e3b3b57632
Obviously, I don't use masterpass as the master password ;)

You can even pipe it through sha1sum instead of md5sum with:

```

echo masterpass amazondotcom | sha1sum | cut -c1-10

```

for a sha1sum hash. You can take it a step further and add a third and fourth item too:

```

echo masterpass 123456 abcdef amazondotcom | md5sum | cut -c1-10

```
which gives you more security because no one will know how many items you used or what they are :)

This works perfectly in a script.

---

### Post by ardchoille on 2006-07-03
I just wrote a script for this type of thing:

```

#!/bin/bash
# This script creates a random password using sha1sum

echo "Enter the master password"
read -s MASTPASS

echo "Enter the reason"
read -s REASON

echo "Enter desired number of characters"
read -s DESNUM

echo
echo "Your random password is:"
echo $MASTPASS $REASON | sha1sum | cut -c1-$DESNUM
echo

```

I hope it's helpful to someone.

---

### Post by cpbl on 2006-09-27
Folks,

krisravan does not want to GENERATE a random word, which is easy. Rather, the question was about SETTING one from a script.

I now have the same problem. I have moved from RedHat, which had the following option for the passwd command.

```
passwd --stdin <user>
```

but this seems not available in Debian/Ubuntu.

How do I write a script to set a new user's password to a given value?

Thanks!

(For those using RH, here *was* my Perl code:
```
     my $password=randomPassword(10);                                           
     my $PASSWD;                                                                
     open(PASSWD,  "|/usr/bin/passwd --stdin $user") or die "Cannot open /usr/bin/passwd: $!";                                                                 
     print PASSWD "$password\n";                                                
     close(PASSWD);                                                             
# Set the date of last password change to a special marked value (12345 days since 1970):                                                                      
     doSystem("chage -d 12345 $user");   
```

---

### Post by scottishnarn on 2007-01-07
Here's the ubuntu code to change the password of $user to $passwd

usermod -p `mkpasswd $passwd` $user

Hope this helps.

---

