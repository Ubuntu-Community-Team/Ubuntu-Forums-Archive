---
title: "Sudo command isnt working"
date: 2005-10-10
forum: Desktop Environments
---

### Post by firesquad on 2005-10-10
for some reason the sudo command doesn't seem to work on my ubuntu system. whenever i use the sudo command for anything it comes up with the same message each time 

cannot find ubuntu with GetHostBysomething something i can't remembr the rest but it wont let me do anything like add users or stuff

help!!:confused:

incase you havent guessed im a newbie

---

### Post by heimo on 2005-10-10
Boot in recovery mode (hit esc at the beginning of boot process to enter grub menu) - I'm not 100% but I think this way you get "root shell" automatically. If not, use Live CD to do the same (in this case you need to mount your root partition first). Edit /etc/hosts file and make sure you have a line like this at the beginning:
```
127.0.0.1       localhost.localdomain   localhost       ubuntu
```
where ubuntu is the hostname of your system (run command *hostname*) to find out. Reboot normally. That's my best guess.

If you need to do it using Live CD, I can try to give you more details.

---

### Post by firesquad on 2005-10-11
It didn't work but thanx anyway

doesn't matter i solved the problem myself.
all i had to do was go into sessions at the login screen and choose the session for repairing the system if you can't log on normally (no. 5).
when youve logged on in this session it disables the permissions so anyone can alter any file. then i entered this in the terminal:

[COLOR="Blue"]gedit /etc/hosts[/COLOR]

then altered it the way you told me.. i reset the machine and logged on normally and low and behold ......... i was able to change the date, add users and use the sudo command

yaay:razz:

---

