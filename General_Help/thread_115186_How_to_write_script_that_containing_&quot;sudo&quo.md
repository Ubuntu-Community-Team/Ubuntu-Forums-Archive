---
title: "How to write script that containing &quot;sudo&quot;"
date: 2006-01-10
forum: General Help
---

### Post by healychan on 2006-01-10
Hello all,

After we type "sudo xxxxxx", it will prompt for the password. I am wondering how sudo get our input. Is it from stdin?? If it is, can I write a script that passing the password using "echo"??

The reason I ask this question is I would like to write a script to connet to wireless access point after startup. I used to do this now
```
sudo iwconfig wlan0 essid "XXXXX"
sudo ifup wlan0
```

I would like to write one script for "home" and the other for "school". This allow me to choose which access point to connet.

Thanks for any advice:smile:

---

### Post by Gray. on 2006-01-10
Maybe you could replace the first sudo with gksudo then it will pop up a box asking for the password. Then after that the other commands requiring sudo should work (since it has a time limit).

---

### Post by healychan on 2006-01-10
Thanks for your advice. 

But I would like to do it with sudo. The reason is that I am a Computer Science student. I just want to find out more of my Ubuntu box. I need to know every single bits in my box. It is kind of learning:razz:

---

### Post by schilcha on 2006-01-10
[QUOTE=healychan]After we type "sudo xxxxxx", it will prompt for the password. I am wondering how sudo get our input. Is it from stdin?? If it is, can I write a script that passing the password using "echo"??
[/QUOTE]

This is not really an answer to your question, but a different approach...
Writing a script that echo's the pwd seems a bit brute to me (storing the pwd in plain text -- I hate to do that, although you sometimes have to, eg for fetchmail or smb-mounts).
BUT, what you can do is to reconfigure sudo to explicitly allow the execution of the two commands without password. Here's an example from my /etc/sudoers:
```

schilcha  smithers = NOPASSWD: /usr/bin/po* roadRunner

```
This allows me (schilcha) to execute the pon and poff scripts (to dis/connect a VPN) without entering a pwd. (Make sure to use "visudo" to edit this file!!!)

See "man sudoers" for details on the syntax

Good Luck!

---

### Post by healychan on 2006-01-10
After reading the man page of sudo. I find that I can use the flag -S to cause sudo to get pwd from stdin. Therefore, I may be able to pass the pwd using "echo".

Someone told me that we can disable the sudo for some commands. I couldn't found the file to configure sudo. Any ideas??

---

### Post by BigMurph on 2006-01-10
Sudo configuration file is /etc/sudoers.

To edit this file type "sudo visudo".

Make sure you read up on the syntax of the sudoers file. There can be NO mistakes or visudo will not let you save the changed sudoers file.

Read the man pages for visudo and sudoers. There are also some examples online. Search for "sample sudoers file".

---

### Post by hw-tph on 2006-01-10
Try reading expect(1). You can also make use of the autoexpect script which comes with the package - it's in /usr/share/doc/expect/examples.


H&#229;kan

---

### Post by healychan on 2006-01-10
May I ask what is that "expect" doing. How does it related to "sudo"?????

---

### Post by Whatsisname on 2006-01-10
why don't you do what schilcha said? It is much safer and secure, and applies to any situation without comprimising the rest of your system.

---

### Post by healychan on 2006-01-10
[QUOTE=Whatsisname]why don't you do what schilcha said? It is much safer and secure, and applies to any situation without comprimising the rest of your system.[/QUOTE]
Thanks for all the advice from you guys. But I really don't need any tools or application.

As I mentioned before, I fancy sudo only because this is part of my studies. I have no problem with accessing the network. What I am doing is for fun, explore my OS, playing around with it.

---

### Post by quonsar on 2006-01-10
> Thanks for all the advice from you gays.

thay, no problem thweetie!

---

### Post by hw-tph on 2006-01-13
[QUOTE=healychan]May I ask what is that "expect" doing. How does it related to "sudo"?????[/QUOTE]

Expect is a means to feed a programmed response to a defined string. You can write complete scripts or use it inline in a bash script. It is very useful for creating FTP scripts and similar uses.


Håkan

---

