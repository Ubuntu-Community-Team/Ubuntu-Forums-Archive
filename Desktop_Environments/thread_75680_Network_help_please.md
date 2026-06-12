---
title: "Network help please"
date: 2005-10-14
forum: Desktop Environments
---

### Post by NZ-Wanderer on 2005-10-14
HI all, please excuse the terminology in this message, I just gonna say it how it is...

I have 2 computers linked together via a high speed switch which in turn is connected to my router...

On main computer I have:
1a) XP Pro (Games only)
1b) Breezy
1c) vmware XP Pro

On second computer I have
2a) XP Pro (Games only)
2b) Breezy

Now, my problem is this.........

I do not have a clue on how to get 1a talking to 2b
I do not have a clue on how to get 1b talking to 2a or 2b
I do not have a clue on how to get 1c talking to 2a or 2b
I do not have a clue on how to get 2a talking to 1b or 1c
I do not have a clue on how to get 2b talking to 1b or 1c

I have got 1a talking to 2a and vice-versa (that was easy)

Can anybody possibly help me??? (remembering that I am brand new and am able to follow instructions, but do not know anything :rolleyes: :rolleyes:  )

---

### Post by manicka on 2005-10-14
This should get 1a talking to 2b and 2a talking to 1b, and probably most of your other combos :)

[http://www.ubuntuforums.org/showthread.php?t=26438&highlight=samba+howto](http://www.ubuntuforums.org/showthread.php?t=26438&highlight=samba+howto)

---

### Post by NZ-Wanderer on 2005-10-14
Thank you for the reply, much appreciated...

I tried the how-to that you suggested, went fine till I got down to 

sudo smbpasswd -a `whoami`

for a start terminal threw back 

bash: whoami: command not found

then when I took away the ' ' and replaced the whoami with my first name (john) it asked me for New SMB password: which I typed in a password and then did it again when I retyped it...

went to my small computer and browsed to mshome (I use mshome instead of workgroup) and sure enuff there was a "Ubuntu server now listed...
However, when I enter in "john" and my password it changes the john to ubuntu\john and wants the password again.. - it will not accept it and always changes the name to what I just said..... :(

---

### Post by manicka on 2005-10-14
You need to replace whoami with your username

In your case

sudo smbpassword -a john

---

### Post by NZ-Wanderer on 2005-10-14
Yup, I did that, but as I said previously it won't let me in..

UPDATE: I rebooted all computers about 3 times, reset the network connections on the windows computer, then SHORTENED
netbios name = main_ubuntu_server
down to
netbios name = main_ubuntu
and IT WORKS.....

I honestly don't know why it does, but it is...

Soo, now I have 2a talking to 1b...

Will try the others tomorrow, after last nights big wait for breezy I need sleep.... :) :)

---

### Post by manicka on 2005-10-14
[QUOTE=NZ-Wanderer]

I honestly don't know why it does, but it is...

Soo, now I have 2a talking to 1b...
[/QUOTE]

I'd say it's because you made windows look for new settings and stopped it using settings that it had cached.

The joys of working around Windows ;)

---

