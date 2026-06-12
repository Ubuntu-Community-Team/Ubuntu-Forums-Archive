---
title: "Auto logout in less than 10 seconds"
date: 2005-12-29
forum: Desktop Environments
---

### Post by randal on 2005-12-29
I logged in (graphically) to my Ubuntu as usual but I encountered a problem with logging in. I got "kicked out" even before I could see my desktop and then the system reported of me being logged in for less than 10 seconds. Further, the system told that if it was not me who logged out, there could be a problem with some software installation. But like always, I did not take time to get all the details--sorry.

Before continuing, let me tell you that I'm dual booting with XP.

So I resorted to logging in with failsafe but still got kicked out. I could only login successfully with textual interface. Using the terminal, I removed blender since it was the last software that I remembered I installed and tried to login again but the problem was still there. I found it troublesome to consult people and find a solution so I reformatted my disk.  

I decided to shift to Kubuntu--which, I think was a not so good idea :p--and during the installation,  I encountered an error with some YAHOOMSGR~1--I really don't know what the "file" was but if you saw it, there's no doubt, it's yahoo messenger. But what was confusing is that I only have yahoo messenger in my XP. There was, as far as I can remember, a problem with the size of it's log file. The installation reported that the log file is appeared to be of 180k in size but it actually has 500+k clusters(?). I proceeded with the installation just to get Grub back, and then removed the messenger. Installed Kubuntu again, that time without the problem.

I'm really confused. How do I know that it is the other OS that causes a problem?

---

### Post by ed_d on 2005-12-29
What you need to do is "sudo chown username:username .ICEauthority

SO, during the boot, open a terminal and execute that.

---

### Post by Lord Illidan on 2005-12-29
[quote=ed_d]What you need to do is "sudo chown username:username .ICEauthority

SO, during the boot, open a terminal and execute that.[/quote]

Mind you tell us what that means.. Don't just pass out code, give an explanation..

---

### Post by ed_d on 2005-12-29
Sorry

What happens, or has happened to me is that "root" has taken ownership ot that file. When this has happened, it has stopped access to the desktop. To me, it usually happened after I used K3B in gnome. So, I would go into a rescue console from the gdm login screen and change ownership (chown) back to my username, then exit and log back in. All was good at that point.

---

### Post by randal on 2005-12-29
Hmnn... was I wrong in thinking that some process done in the other OS affected my Ubuntu? I know there is some way to solve the problem if a process in Ubuntu caused it but what if that Yahoo log file actually caused the problem?

---

### Post by Rinzwind on 2005-12-29
[QUOTE=ed_d]Sorry

What happens, or has happened to me is that "root" has taken ownership ot that file. When this has happened, it has stopped access to the desktop. To me, it usually happened after I used K3B in gnome. So, I would go into a rescue console from the gdm login screen and change ownership (chown) back to my username, then exit and log back in. All was good at that point.[/QUOTE]

Jups.

I installed bluetooth as root. When I put my bluetooth in and do my things in gnome/kde and take the bluetooth out the next session I start will crash: .ICEauthorty was changed to root and not the user.

**rm .ICEauthority** in the homedir solves it too.

---

### Post by ed_d on 2005-12-29
Im always nervous on pointing out the rm features to the younglings, as can cause some serious side effects. I like the chown feature myself.

---

### Post by binks on 2005-12-30
dudes you just saved my ubuntu carrer was contemplateing xp but this worked cheers

---

### Post by randal on 2005-12-31
Can I get explanation on why things like that could happen... I'm lost in this thread...

---

