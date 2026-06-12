---
title: "Putty like software"
date: 2009-06-01
forum: General Help
---

### Post by bizhat on 2009-06-01
I want to regularly connect to several remote servers. On windows, i used putty, with host name and key saved for each servers.

I installed putty on ubuntu, which won't allow me to enter user name as part of host name.

When i enter IP address

> 76.76.18.19

It connected to server and asked user name.

When i enter user name along with IP, putty failed to connect, it used to work in windows.

> root@76.76.18.19

Any other program where i can save different SSH accounts and just double click it to access the server with key login ?

---

### Post by evermooingcow on 2009-06-01
You can set up SSH to log you in without a password:
[http://linuxproblem.org/art_9.html](http://linuxproblem.org/art_9.html)

You enter
```
ssh username@hostname
```in the terminal to connect. If you include this line in a script maybe you can run it by double-clicking. I'm not sure - I've never tried setting anything up to work from a double-click.

---

### Post by fermulator on 2009-06-01
Indeed, that's an interesting annoyance.

According to OSALT, there's really no "decent" PuTTY alternative.
[http://www.osalt.com/putty](http://www.osalt.com/putty)

Do you require (really want) to use a GUI solution?  The reason I ask is because it might be simpler for you to simply write an alias for each server you would normally connect to.

For example, I have an alias to connect to my server (via SSH) using my private key.  In .bash_aliases:
```
alias sshserver='ssh -X -i ~/.ssh/id_rsa server_ip_address'
```

If you don't want to deal with private/public keys, you could do something like:
```
alias sshserver='ssh username@server_ip_address'
```

To keep things clean, (if you have a LOT of servers), you could create a new file for all of your SSH aliases, perhaps called ~/.bash_aliases_ssh and include it from your .bash_rc file.
> alias myserver1='ssh -X user1@ip_address1'
alias myserver2='ssh -X user2@ip_address2'
alias myserver2='ssh -X user2@ip_address3'

Now, it's very simply to ssh:
 1. Open a terminal
   * OptionA: ALT-F2, 'gnome-terminal'
   * OptionB: Super+Space (gnome-do), "gnome-terminal'
   * OptionC: Applications --> Accessories --> Terminal
 2. Execute your desired ssh alias:
   * start typing "ssh", use tab for autocomplete.
 3. It will prompt for your password (unless you're using public/private keys)

If you really want a GUI to do this, I'm afraid I don't know what to suggest.  Sorry I can't be any help on that route.

---

