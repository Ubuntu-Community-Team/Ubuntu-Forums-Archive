---
title: "I hate ubuntu 8.10 bcz I can not use root"
date: 2009-01-15
forum: General Help
---

### Post by adameye on 2009-01-15
I think the old version of Ubuntu is good, but 8.10 is very strange, I can not use root to do anything, everytime when I use sudo su, I got "#  ",  after "#  " I can not display previous command, and I can not use Tab key to display the existing command or files, more important, some installed software can not be used under "#  ", anybody know what happened? thanks

---

### Post by zacktu on 2009-01-15
When you su, you start a new shell.  "#" is the default prompt for root's shell.  The reason you can't see the previous command is that you issued it in a different shell.  When you use ctrl-D to exit the new shell, you'll be back in the old shell.  The history command will show your previous command as the last one entered.

---

### Post by adameye on 2009-01-15
thanks for the reply
but I need the root account to install something!
"#  " is nothing and useless, but I have no idea to find other ways to use root

---

### Post by hyper_ch on 2009-01-15
[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

---

### Post by doug-M on 2009-01-15
So 3 issues
1 - can not display previous command
2 - can not use Tab key to display the existing command or files
3 - some installed software can not be used under "#"

1 - Not displaying the command history for root is normally a security best practice. Try searching for enable history if you really want it. Also the other poster described why you current session history doesn't carry over to it.

2 - Sounds like file completion is not enabled. Perhaps because when you are running your root shell you are using /bin/sh as the shell as opposed to the typical end user /bin/bash.
So you might try searching on the topic of enabling file completion, or type bash to get a bash shell and see if that works better for you.

3 - Well you should be careful what you do as root (at the # prompt). If it can't find them then it is likely the path. Try typing env and look at what PATH= is set to. Compare this to typing env in a normal non-root (non-#) shell.

---

### Post by matey3 on 2009-01-15
lol I use xdm as my GUI and I can log in as root.
you can disable the GUI auto start.

oh and for the command line (terminal) you can insert a line in the .profile of the root.
PS1='\u@\h:\w\$ > ' 
or whatever instead of $
 then you get the regular prompt.
what user do you log in to begin with?
if not root and if you like the prompt just type set to see the PS1 value, copy/paste it to root's profile

---

### Post by adameye on 2009-01-15
when I try bash,
"bash: setenv: command not found"


most ubuntu users are students and I really don;t think anybody has interest to hack my computer.
I really do not mind anybody steal the things in my computer

now anybody can tell me how to get root account with "#  "
diable GUI?

---

### Post by jerome1232 on 2009-01-15
--edit-- 

Oh I see now what you actually want is to login to your gui with the root account, read hyper-ch's link. My answer is desktop users don't need to login to the gui as root. 

I'll link it again [http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

I don't think you understand in the slightest what the implications of doing your everyday tasks on the root account imply.

You really want to browse the web with a web browser that has root privileges? Are you trying to get malware? You trust java/flash programs on randomguys website enough to give them full access to your system?

-- end edit--

Something must not be set right on your machine all of the above features work for me, using sudo su or sudo -i.

tab completion and command history both work as they should in 8.10. 

When you have a prompt that ends with "#" that is a root prompt.

I think you need to check out some of the things doug-M mentioned as what your seeing isn't normal behavior.

---

### Post by doug-M on 2009-01-15
> **adameye said:**
> I really do not mind anybody steal the things in my computer

But I mind if your computer is now a zombie serving up spam, or attacking other computers, or an open relay, or serving up malware, or...

As hyper_ch posted, try this:
New forum policy on log-in-as-root tutorials
[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

FYI I do lots of weird and wonderful things to my Ubuntu computer and I have never required a root shell. I have always been able to do everything easily with sudo doing various commands. Now before I had sudo, a long time ago back on Solaris, HP-UX, AIX, MVS etc. I generally didn't get any root access at all, although favors for the sysadmins often worked wonders. Other pre-sudo days on things like slackware I really tried to be very careful what I did and didn't do as root.

sudo is your friend

---

### Post by heindsight on 2009-01-15
> **doug-M said:**
> But I mind if your computer is now a zombie serving up spam, or attacking other computers, or an open relay, or serving up malware, or...


not only that, but if you accidentally do something wrong, while logged in as root, you can cause yourself some serious headaches trying to get things fixed again (and you'll probably lose some important data in the process too).

Not logging in as root is not just about security, it also protects you from accidentally doing serious damage to your OS.

---

### Post by adameye on 2009-01-15
thanks,I did edit .profile and insert the line you mentioned, but everything is same with before
> **matey3 said:**
> lol I use xdm as my GUI and I can log in as root.
you can disable the GUI auto start.

oh and for the command line (terminal) you can insert a line in the .profile of the root.
PS1='\u@\h:\w\$ > ' 
or whatever instead of $
 then you get the regular prompt.
what user do you log in to begin with?
if not root and if you like the prompt just type set to see the PS1 value, copy/paste it to root's profile

---

### Post by mssever on 2009-01-15
> **adameye said:**
> thanks,I did edit .profile and insert the line you mentioned, but everything is same with before
Do you know what it does? If not, why did you do it? You shouldn't follow advise from random posters (myself included) without first understanding it.

My advice is to forget about a root shell, since it's completely unnecessary.

Back in the old (pre-sudo) days, I had to frequently use su to admin my system. I had to devise all kinds of elaborate methods to make sure I didn't forget which terminal was root and which was regular. After all, mistakenly running a command as root can have major consequenses.

These days, I just use sudo. It's easier and safer and works 100% of the time. Keep in mind that I use the terminal A LOT, so I know what I'm talking about.

---

### Post by bmartin on 2009-01-15
> **adameye said:**
> I think the old version of Ubuntu is good, but 8.10 is very strange, I can not use root to do anything, everytime when I use sudo su, I got "#  ",  after "#  " I can not display previous command, and I can not use Tab key to display the existing command or files, more important, some installed software can not be used under "#  ", anybody know what happened? thanks
When I want to become root, I use **sudo -s**. Does that do the trick?

---

### Post by redseventyseven on 2009-01-16
> most ubuntu users are students and I really don;t think anybody has interest to hack my computer.
I really do not mind anybody steal the things in my computer

Most ubuntu users are students? Really? I'd like to see the evidence for that. Furthermore, how is that relevant? Are students less likely to want to hack into other people's computers?

Anyway, as you say, it's your computer, you choose how you run it, but I'm with just about everyone here in thinking what you're asking for is A Bad Idea, and it's not ethical to give bad advice. It's like if someone asked "Hi there, I have a loaded gun pointing straight at my balls and a piece of string tied to the trigger. How do I hook the string up over a pulley system so that I can fire the gun from where I'm standing?"

---

### Post by matey3 on 2009-01-16
> Most ubuntu users are students? Really?

I believe he means where he is at (in his place) there are more students.(ie college, dorm, etc.)

Heh, I some times think that way too, like I dont care about security just give me my files..

I usually have to beg my family members to please go on my computer... heh specially my wife, if she sees a black screen with a command prompt she'll think the computer's broke! :D

---

### Post by mssever on 2009-01-16
> **matey3 said:**
> Did you try **xdm** at all?

Also **have you created a password for the root** user?
It's a little tricky at the 1st time you install the OS.
I dont like the GUI starting at the boot up, I like the command prompt a lot better, I can log in as any user I want.(I prefer root)and bring up any X program I want (I prefer xdm)
First, it's against forum policy to provide instructions for how to defeat Ubuntu's security model (which includes the lack of a root password). If people want to enable the root password, that's their right, but they should find out how elsewhere. We should be explaining why Ubuntu's model is superior.

Second, there's simply no valid reason whatsoever to run X as root. Period. It's an all-around bad idea. Please don't give out bad advise. There's nothing you can do in a root X that you can't do in X running as a normal user, and running X as root is really dangerous.

Because of the above, switching to xdm won't accomplish anything useful that gdm or kdm can't already do. If you just like xdm better, fine. But gdm is correct in disallowing root logins.

---

### Post by overdrank on 2009-01-16
It has been posted once in the thread so I will post once more [forum policy on log-in-as-root tutorials]("http://ubuntuforums.org/showthread.php?t=716201")
Thread closed.

---

### Post by bodhi.zazen on 2009-01-16
> **adameye said:**
> I think the old version of Ubuntu is good, but 8.10 is very strange, I can not use root to do anything, everytime when I use sudo su, I got "#  ",  after "#  " I can not display previous command, and I can not use Tab key to display the existing command or files, more important, some installed software can not be used under "#  ", anybody know what happened? thanks


FYI, since I am not sure if the original question was answered, you access root on Ubuntu with sudo

See : [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) 

for a single command use sudo commmand

for a root shell use

```
sudo -i
```

==============

Also, the tutorial on how to enable logins to X for root was jailed as per forums policy

[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

---

