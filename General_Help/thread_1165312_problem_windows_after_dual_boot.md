---
title: "problem windows after dual boot"
date: 2009-05-20
forum: General Help
---

### Post by lolium on 2009-05-20
Hey
   I created an unformatted partition and then i used the live cd of the current ubuntu version and installed as told to by installation instructions but after reboot i try booting into windows or linux it just restarts the computer and i cant access any operating system now.

How do i make a dual boot and it allow to boot into windows or linux without any problme

cheers

Sam

---

### Post by AlexsAntidote on 2009-05-20
Could you boot from the Live CD and post a screenshot of your partitions (use the partition manager under system->administration)

This should help us troubleshoot your situation.

---

### Post by lolium on 2009-05-20
> **AlexsAntidote said:**
> Could you boot from the Live CD and post a screenshot of your partitions (use the partition manager under system->administration)

This should help us troubleshoot your situation.

I would happily do that for you on the live cd i cannot access the "x window" as i think it is know i come onto the bash i think were it says something on the lines of 


ubuntu@ubuntu:$

Is tehre a code to access the "x windows"

---

### Post by lolium on 2009-05-20
Also, i have put linux on the domain at my school for the it technicians and its proving difficult to me as how to allow user access totheir files on the windows files.

I was thinking change the my documents directroy on linux but need a password to access it, any suggestions on how to do so?

if somebody could help me on these 2 problems i would be forever greateful

cheers

Sam

---

### Post by AlexsAntidote on 2009-05-20
That is interesting. Are you using Ubuntu Server Edition by any chance? If so the server edition does not come with a GUI.

If when you boot from the Live CD you only come to the Bash prompt, try typing in the command: **startx**

If you get some type of an error message could you go ahead and post it here?

---

### Post by lolium on 2009-05-20
> **AlexsAntidote said:**
> That is interesting. Are you using Ubuntu Server Edition by any chance? If so the server edition does not come with a GUI.

If when you boot from the Live CD you only come to the Bash prompt, try typing in the command: **startx**

If you get some type of an error message could you go ahead and post it here?

I have the new desktop edition

right i will try that and then you want a print screen on the partitions?

I cant remember off the top of my head what happens wehn i try browse to the dierectory but i could post up tomoro what happens or evem p/m yoo if i can..

Sam

---

### Post by AlexsAntidote on 2009-05-20
> **lolium said:**
> I have the new desktop edition

right i will try that and then you want a print screen on the partitions?

I cant remember off the top of my head what happens wehn i try browse to the dierectory but i could post up tomoro what happens or evem p/m yoo if i can..

Sam

Hey Sam,

If you could get a screenshot of gparted (the partition manager) displaying the partitions for your hard drive, that should be sufficient. If you cannot boot into either Linux or Windows it may be possible you somehow messed up the partitions which would prevent you from mounting them (which would give you problems when you try to browse to the directory).

Posting here is fine, but you may also p/m me if you prefer.

---

### Post by AlexsAntidote on 2009-05-20
> **lolium said:**
> Also, i have put linux on the domain at my school for the it technicians and its proving difficult to me as how to allow user access totheir files on the windows files.

I was thinking change the my documents directroy on linux but need a password to access it, any suggestions on how to do so?

if somebody could help me on these 2 problems i would be forever greateful

cheers

Sam

That sounds like a different problem, you may be better off starting a separate thread for that one. I would also recommend adding a little more clarification as well.

Did you mean: you installed Linux (I'm guessing Ubuntu 9.04 but is it server or desktop edition) on one of your school's servers and want to allow other users to access files on that same machine remotely from other machines?

How are you trying to access the files? VNC? VPN? WebDAV? SSH?

---

### Post by lolium on 2009-05-20
> **AlexsAntidote said:**
> Hey Sam,

If you could get a screenshot of gparted (the partition manager) displaying the partitions for your hard drive, that should be sufficient. If you cannot boot into either Linux or Windows it may be possible you somehow messed up the partitions which would prevent you from mounting them (which would give you problems when you try to browse to the directory).

Posting here is fine, but you may also p/m me if you prefer.

I tried the startx command in bassh you asked me to do when running the live cd and that just brings up a black screen.

Before i couldnt boot into either after installing ubuntu, atm i have only windows xp now, and i cannot gain access to xwindow on live cd.

As for the directory one for the linux xp server, i got ubuntu on the domain but i need a password to brows so the user files on linux, is there a way to get around this and have a certain folder load as my documents for when a user logs into the domain?

Cheers

Sam

---

### Post by lolium on 2009-05-20
> **AlexsAntidote said:**
> That sounds like a different problem, you may be better off starting a separate thread for that one. I would also recommend adding a little more clarification as well.

Did you mean: you installed Linux (I'm guessing Ubuntu 9.04 but is it server or desktop edition) on one of your school's servers and want to allow other users to access files on that same machine remotely from other machines?

How are you trying to access the files? VNC? VPN? WebDAV? SSH?

I installed linux on a client (ubuntu) and then hooked it up to the domain users can log in but it auto creates them a folder in linux, i want it so when they log in there documents on linux will direct to were there shared folder will be e.g "i:/2011/006057.2011" that type of thing , i didnt do the rest but the head it technician told me you cant browse to the directory becaue of password but he said somthing bout can map the network drive.

Im not sure he didnt tell me how he tried accessing the files.

Sam

---

### Post by AlexsAntidote on 2009-05-20
> **lolium said:**
> I installed linux on a client (ubuntu) and then hooked it up to the domain users can log in but it auto creates them a folder in linux, i want it so when they log in there documents on linux will direct to were there shared folder will be e.g "i:/2011/006057.2011" that type of thing , i didnt do the rest but the head it technician told me you cant browse to the directory becaue of password but he said somthing bout can map the network drive.

Im not sure he didnt tell me how he tried accessing the files.

Sam

OK first of all, are you running Microsoft Windows (XP or other) and trying to remote connect to that and access files through Windows? Or are you running Linux and trying to connect to it and etc.? File permissions and user access are handled differently between Windows and Linux.

If you are running Linux on the server and your clients are logging in to the server remotely you can change their default home directory within the linux server to give them a different default location.

If you want to do that then let me know, I will try to help, but that is a little more advanced.

---

