---
title: "Your last session lasted less then 10 seconds"
date: 2006-08-28
forum: Desktop Environments
---

### Post by derek_fisher on 2006-08-28
I am currently using ubuntu-6.06-beta2,in vmware, Windows host,linux guest(I am beginner,so cannt go without windows)
here is the details(I typed them word by word,even I dont know what does it tell):
/etc/gdm/PreSession/Default:Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default:running: /usr/bin/sessreg -a-w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "root"
/etc/gdm/Xsession:Beginning session setup
/root/.profile:line 9:mesg:command not found
/etc/gdm/Xsession:line 73; ls:command not found
/etc/gdm/Xsession:Executing default failed, will try to run x-terminal-emulator
/etc/gdm/Xsession:line 224:exec:x-terminal-emulator:not found

probably i did something wrong to /etc/.profile


the problem is how could I login to this system, 
failsafe gnome could not work at all;
i can login to failsafe terminal,it is said that used to fix the problem of system,but I found that most of command could not work under this mode, but only "cd"and"kill"could work(NO sudo,ls,rm,apt-get,etc.),but which process to kill?? i dont know..

I check some forum in the website,,
try ctrl+alt+F1 to bypass the system,but could not work;
rescue with install-ubuntu.iso,, no difference at all;
using some other command(sigh!!!only "cd""kill" could work)


so in this case,how could I enter the system, and what should i do next??

---

### Post by mjunior on 2006-12-29
I have the same error ...
In my case it was out of disk problem..so I enter in prompt mode and delete a few files till there's enough space for ubuntu splash to work
Yeah..I know Iknow..That suppose to be the swap job (booting without using disk space at all)..but who knows!!
It worked for me.

---

### Post by mjunior on 2006-12-29
I find out this topic that also can help:
[http://www.ubuntuforums.org/showthread.php?t=80599&highlight=session+lasted](http://www.ubuntuforums.org/showthread.php?t=80599&highlight=session+lasted)

---

