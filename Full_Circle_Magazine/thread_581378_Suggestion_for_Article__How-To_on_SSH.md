---
title: "Suggestion for Article?  How-To on SSH"
date: 2007-10-19
forum: Full Circle Magazine
---

### Post by jacrider on 2007-10-19
In an effort to manage the computers in my house, I would like to become better versed in how to use SSH.  I have failed miserably so far.  Any chance of getting that on the editorial list?

Love the magazine.

---

### Post by catfacts on 2007-10-19
I can try to find someone but will most likely fail as i have no clue what you are talking about. But if it involves networks im a noob. But if you *really* want to help find someone who would like to write an article yourself, ask around the community cafe, search google and seek out a guru! It sounds interesting as I have multiple computers and use flash drives as my "network" but again I may not be understanding SSH.

---

### Post by mrmonday on 2007-10-21
SSH is a way of controlling a PC remotely and securely. I use it all the time :D the basic syntax is
```
ssh <user>@<host>
```
Obviously the host needs to have an ssh server running on their PC. It's a really simple way of having command line access on a remote PC. If you need a GUI, then you can use VNC. As for how to set up the server, I don't know, but I should imagine it is really just configuring a config file, then making it run automatically at start up. In the #6 Q&A there will be a simple thing about using nautilus for ssh file management. As always though, a quick google  should solve your problems :D Look for an ssh server in synaptic then google for its documentation :)

Hope this helps :)

---

### Post by ronniet on 2007-10-21
> **mrmonday said:**
> SSH is a way of controlling a PC remotely and securely. I use it all the time :D the basic syntax is
```
ssh <user>@<host>
```


Excellent, thank you for volunteering mrm, have that article on my desk asap...  :KS

---

### Post by mrmonday on 2007-10-21
> **ronniet said:**
> Excellent, thank you for volunteering mrm, have that article on my desk asap...  :KS

That's about as far as my knowledge goes on that one... However linuxgeekery has set up an SSH server, which I use...

---

### Post by ronniet on 2007-10-21
> **mrmonday said:**
> That's about as far as my knowledge goes on that one... However linuxgeekery has set up an SSH server, which I use...

Amazing isn't it how people say *'i do it **aaa**aall the time'* then when you ask them to explain it they'll point to someone else and say *'but he set it up!'*  :D

ok, we'll agree to volunteer *linuxgeekery* then...  :KS

LG, get writing, your fans await...  :D

---

### Post by TopasPV on 2007-10-22
> **mrmonday said:**
> As for how to set up the server, I don't know, but I should imagine it is really just configuring a config file, then making it run automatically at start up.

In fact, it's as simple as this:
```
sudo apt-get install ssh
```

---

### Post by ronniet on 2007-10-22
> **TopasPV said:**
> In fact, it's as simple as this:
```
sudo apt-get install ssh
```

Ooh, another volunteer...  :KS

---

### Post by linuxgeekery on 2007-10-22
I got bored and wrote a general SSH article - so this one's closed (at least a general one).  Feel free to write a more specific article - file transfers, tips n' tricks, etc.

---

### Post by jacrider on 2007-10-24
Thanks Linuxgeek.  I look forward to reading it in an upcoming issue.

---

### Post by ncappel1 on 2007-10-25
linuxgeekery, when you connect to another computer with ssh, will the remote machine display what you're doing? like an invisible person using the computer? just my curiosity.

---

