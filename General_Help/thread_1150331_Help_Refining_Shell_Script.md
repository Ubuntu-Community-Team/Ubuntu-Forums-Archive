---
title: "Help Refining Shell Script"
date: 2009-05-06
forum: General Help
---

### Post by jperez3 on 2009-05-06
I have ran through the process of setting up virtual mailboxes with Postfix/Dovecot 

and it worked like a charm. However I needed some help refining a shell script I made that incorporates the commands to add users and restarting dovecot.

Here's my shell:
 [html]
#!/bin/bash
clear
echo "enter email address:"
read fname
adddovecotuser $fname;
echo "enter email password:"
read upass
mkdovecotpasswd $fname $upass;
/etc/init.d/dovecot restart;
chmod 755 -R /home/vmail;
chown -R vmail:vmail /home/vmail;
exit
[/html]The problem I have is that when users are added the accounts are not readable by default so the above shell makes them readable so they can be used. 

 
What I would like is to make this script process a command and halt if there is an error. Currently it just keeps going until the script has ran it's course. Can anyone help?

Thanks again

---

### Post by Brandon Williams on 2009-05-06
```
#!/bin/bash
set -e
etc...
```

If you 'set -e' as the first command in your script, then it will exit immediately if any 'simple command' fails (i.e. exits non-zero).

See 'man bash' for more details about what 'simple command' means in this context.

---

### Post by KyleBrandt on 2009-05-06
Bash keeps the exit status of the last command in the special variable $? .  So you can also put something like this after a specific command:

```

if [[ "$?" != 0 ]]; then 
   echo "foo"
   exit 1 
fi

```

You can also use if directly with the command.

```

if ! grep 'foo' file; then
   echo "Couldn't find it"
   exit 1
fi

```

---

### Post by sisco311 on 2009-05-06
```

echo "enter email password:"
read upass

```

If you wish to hide the password for security reasons:
```
trap "stty echo ; exit" 1 2 15
stty -echo
read -p "Enter e-mail password:" upass
stty echo
trap "" 1 2 15

```

---

