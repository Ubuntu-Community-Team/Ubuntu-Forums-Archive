---
title: "admin tools not starting"
date: 2005-11-06
forum: Desktop Environments
---

### Post by fm1234 on 2005-11-06
When I start an admin app like update or network admin, I enter the user password but then nothing more happens. Same problem if I start it from the command line, w.g., sudo network-admin

I've made sure the root account is locked by entering sudo passwd -l root

Any clues?

TIA,
Fernando

---

### Post by r4ik on 2005-11-07
The password doesnt show up while typing.
Type the password hit enter and you are on youre way.

---

### Post by hashimoto on 2005-11-07
I got a similar problem twice (mine and bros PC) after an expert install. Nothing that requires sudo works, e.g. Synaptic. Expert install asks for root password but never sets the first user on the sudoers list. I had to manually insert it with visudo.

So, to me this sounds very much like your username is not in the sudoers list. Try running visudo in terminal and check that your username is listed.

Also, a question arises: Are you sure the su/root is really locked/disabled? If nothing happens with applications that are supposed to use sudo, then how did you make sure that su was disabled?

---

### Post by fm1234 on 2005-11-07
[QUOTE=hashimoto]I got a similar problem twice (mine and bros PC) after an expert install. Nothing that requires sudo works, e.g. Synaptic. Expert install asks for root password but never sets the first user on the sudoers list. I had to manually insert it with visudo.

So, to me this sounds very much like your username is not in the sudoers list. Try running visudo in terminal and check that your username is listed.

Also, a question arises: Are you sure the su/root is really locked/disabled? If nothing happens with applications that are supposed to use sudo, then how did you make sure that su was disabled?[/QUOTE]

Thanks hashimoto, that was indeed it. I did an Expert install and sudoers had only the root permissions. I didn't check whether root is locked or not. I just issued the command as I had seen in another forum thread. What does it do in fact? refuse su or login to root?? I'm still figuring out this sudo stuff...

Bye,
Fernando

---

### Post by hashimoto on 2005-11-08
[QUOTE=fm1234]Thanks hashimoto, that was indeed it. I did an Expert install and sudoers had only the root permissions. I didn't check whether root is locked or not. I just issued the command as I had seen in another forum thread. What does it do in fact? refuse su or login to root?? I'm still figuring out this sudo stuff...

Bye,
Fernando[/QUOTE]

Glad i could be of help!

You can find more informatin on sudo here:
[https://wiki.ubuntu.com/RootSudo?highlight=%28sudo%29](https://wiki.ubuntu.com/RootSudo?highlight=%28sudo%29)

---

### Post by Bentu on 2005-12-09
I'm having this same problem, but none of the aboe has resolved it. I set a root password and even using that only one or two of the admin tools will work. When selected I get either the round curser spinning for awhile and then it stops, nothing happens at all, or I get to put in my pasword before that happens. I'm open for suggestions, maybe I need to reinstall?

Ben

---

### Post by sjh on 2005-12-09
[QUOTE=Bentu]I'm having this same problem, but none of the aboe has resolved it. I set a root password and even using that only one or two of the admin tools will work. When selected I get either the round curser spinning for awhile and then it stops, nothing happens at all, or I get to put in my pasword before that happens. I'm open for suggestions, maybe I need to reinstall?

Ben[/QUOTE]

Just a long shot, but I had the same problem after I messed with my hosts file (/etc/hosts).  Best as I can tell, the loopback is needed to validate passwords.  I would look there first.

Good Luck
SJH

---

### Post by Bentu on 2005-12-12
Thanks for the reply. I have another machine with ubuntu installed on it, so I checked the file /etc/hosts in this machine with it. They are both identical, so no luck there. I may end up having to reinstall it, if I can't figure out what files the admin tools come from, but I don't like doing that, it's one of the many things that I can't stand about Windows.

Ben

---

