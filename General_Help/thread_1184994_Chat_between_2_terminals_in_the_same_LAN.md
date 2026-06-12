---
title: "Chat between 2 terminals in the same LAN"
date: 2009-06-11
forum: General Help
---

### Post by GenesisOrion on 2009-06-11
This is my first post and if I'm not following the rules of the forum please let me know that, thank you. 

Here's  my problem, waht command can I use to chat between 2 terminals, the pcs are on the same LAN under a router Thomson, how can I use the command echo to communicate between these 2 terminals?  Or any other command that can help me? I just wanna chat with my partner..

Second question: What command should I use to copy files from a pc to another pc with the terminal?

Thank you so very much, any help would be appreciated.

Greetins from Mexico ;)

---

### Post by Iowan on 2009-06-11
Look for information on **wall** - start with **man wall**.  Filesharing will probably require a server of some sort to be installed (Ubuntu has several clients pre-loaded. I've listed some help pages [here]("http://ubuntuforums.org/showpost.php?p=7429692&postcount=6"). Though Samba would work, it's a li'l complex for simple file transfer. NFS is the native method.

---

### Post by jerome1232 on 2009-06-11
You could check out finch, it's Pidgin but works in a text based console. You can use your regular messenger accounts or the bonjour protocol allows for messenging across the lan.

Here's a little screenshot and some basic usuage intructions for finch, I love it.

[http://coderstalk.blogspot.com/2008/09/finch-howto-use-pidgin-via-terminal.html](http://coderstalk.blogspot.com/2008/09/finch-howto-use-pidgin-via-terminal.html)

---

### Post by GenesisOrion on 2009-06-12
Thanks for the help. but I wass thinking in something more simple:

I have read  the man of wall and talk, wall is for post a kind of message and all the users will receive it (only if they have activated the msg y on terminal, but that doesn't matter if you're sudo), but I only can send that messate to the users of my PC, later with the comand talk when i wanna see the pc's that are on the same LAN with who command, I only can see this:

genesisorion@genesisorion-desktop:~$ who
genesisorion tty7         2009-06-11 21:12 (:0)
genesisorion pts/4        2009-06-12 00:06 (:0.0)
genesisorion@genesisorion-desktop:~$ 

How can I send a message to another terminal using the IP of that PC without using the username?

---

### Post by GenesisOrion on 2009-06-12
After some st. google search, I've founded crypcat.

[http://ubuntuforums.org/showthread.php?t=907675](http://ubuntuforums.org/showthread.php?t=907675)

---

