---
title: "Ubuntu/Gnome Bug/Error? Help Please!"
date: 2008-05-13
forum: Desktop Environments
---

### Post by cchester on 2008-05-13
Hey guys,

I just applied the newest updates and restarted like it said and I get the following errors.

$HOME/.dmrc - File should be owned by user and have 644 permissions.

/home/chris/.ICEauthority - File should be owned by user.

It said to report and restart in safe mode but even when I do that I get these two errors. I haven't tried booting into the console yet though. How do I fix this or is the only way to reinstall. I sure hope not.

If so and I have to then I want to repartition my drive different instead of letting Ubuntu do it. So with a 500 GB drive how much should I make for the root system and home much for the home directory? I will be using Vmware and so forth and don't want to run of room when installing programs from synaptic and stuff like that.

I am using Ubuntu 8.04.

Thanks for any help on this. I want my Ubuntu back because right now I have to do this in Windows XP.

---

### Post by Stefan Stryjecki on 2008-05-13
Hey man. I had the same error but it appeared at login. I was able to click "ok" and log in normally.

When are you getting this message?

If I recall right, I had to change ownership on my home directory recursively to get rid of this message. (making myself the owner).

---

### Post by cchester on 2008-05-13
> **Stefan Stryjecki said:**
> Hey man. I had the same error but it appeared at login. I was able to click "ok" and log in normally.

When are you getting this message?

If I recall right, I had to change ownership on my home directory recursively to get rid of this message. (making myself the owner).

Yeah I get it at the login screen sort of. The thing is once I put in my username and pass then the error come up. I click on it and then it is trying to load the desktop and then then second error comes up. Can't get no where else to correct it. I tried loading another older kernel and same thing. So how did you fix this. If I can try and get it to boot to a command prompt?

Thanks for any help.

---

### Post by cchester on 2008-05-14
Ok guys now I think something is getting really messed up now.

I restarted and picked recovery and it got me to a root prompt.

I typed the following:

chmod 644 /home/chris/.dmrc
then
chown chris /home/chris/.dmrc
then
chmod -R /home/chris
then
chown -R /home/chris
then
chmod 644 /home/chris/.ICEauthority
chown chris /home/chris/.ICEauthority

Now I get the following: Your home directory is listed as /home/chris but it doesn't appear to exist. Do you want to login with /(root) dir as home. It might not work.(something like that)

Is there a way I can boot to the command line recovery and add a root account so I can log in to the GUI and fix this or use my Mint 4.0 install on my other hard drive to fix this?

Please help.

Thanks

---

### Post by Stefan Stryjecki on 2008-05-14
Hi. Have you really written "chown -R /home/chris" without specifying the owner?

Try this: start Ubuntu. When you get the error, press Alt+Ctrl+F1. This will bring you to a console. Log in. Then type "ls /home". If you have "chris" in the output then it's not that bad. ;)

After that type:

chown -R chris /home/chris
chmod -R u+rw /home/chris

Then reboot and let us know what happens.

---

### Post by cchester on 2008-05-14
> **Stefan Stryjecki said:**
> Hi. Have you really written "chown -R /home/chris" without specifying the owner?

Try this: start Ubuntu. When you get the error, press Alt+Ctrl+F1. This will bring you to a console. Log in. Then type "ls /home". If you have "chris" in the output then it's not that bad. ;)

After that type:

chown -R chris /home/chris
chmod -R u+rw /home/chris

Then reboot and let us know what happens.

Ok I did everything you said :

I get to the login screen.
Press Alt+Ctrl+F1
It shows chris-ubuntu-desktop-login
So I login
I get after login chris@chris-ubuntu-desktop
then I typed ls/home and it reported chris
so I then typed
chown -R chris /home/chris I get the following
chown cannot read directory /home/chris/internal/uid-0:permission denied

same error for /home/chris/internal but operation not permitted
same error for /home/chris/catalog
same error for /home/chris/pending
same error for /home/chris

chown -R u+rw /home/chris same error as last from above not permitted

This is driving me nuts. Is there anything else I can do?

Thanks for any more help.

---

### Post by Stefan Stryjecki on 2008-05-14
Some of the files in your home directory seem to be owned by root (the superuser - root has user id 0). Try the same thing with superuser privileges, i.e.:

sudo chown -R chris /home/chris
sudo chmod -R u+rw /home/chris

You will have to type your password when prompted.

---

### Post by cchester on 2008-05-14
> **Stefan Stryjecki said:**
> Some of the files in your home directory seem to be owned by root (the superuser - root has user id 0). Try the same thing with superuser privileges, i.e.:

sudo chown -R chris /home/chris
sudo chmod -R u+rw /home/chris

You will have to type your password when prompted.

Same thing yet again. It doesn't seem like it will release. So what else can I try or am I out of options?

What about making a root account so I can use the gui and try and release the permissions?

Thanks for anymore help.

---

### Post by Stefan Stryjecki on 2008-05-14
This is really weird.

You can't create a root account because it's already there. When you run a command with "sudo" you're running it as root. Logging in as root in graphical mode won't help you.

Try one last thing (this is what my friend Google advised to do):

Boot into recovery mode and (after login) type:

chmod 700 ~/

(or "sudo chmod 700 ~/" if the previous doesn't work).

If this doesn't help you, then I give up.

EDIT:
You can also try it with the recursive option (chmod -R 700 ~/)

---

### Post by cchester on 2008-05-15
> **Stefan Stryjecki said:**
> This is really weird.

You can't create a root account because it's already there. When you run a command with "sudo" you're running it as root. Logging in as root in graphical mode won't help you.

Try one last thing (this is what my friend Google advised to do):

Boot into recovery mode and (after login) type:

chmod 700 ~/

(or "sudo chmod 700 ~/" if the previous doesn't work).

If this doesn't help you, then I give up.

EDIT:
You can also try it with the recursive option (chmod -R 700 ~/)

Well I booted into recovery mode and when I picked drop to root and I typed the above like you said and restarted.

Got the exact same .dmrc error and .ICEauthority errors when I rebooted.

I need to ask this of you because I spent a lot of time customizeing my desktop and so forth and don't want to run into this again and have to start from scratch so is there away next time once I get my desktop set the way I want it to save my desktop theme so that I can reinstall it again without having to hunt down everything again? I know that I can click save at the bottom and it saves it for the computer I am on but I want it to have all the files I use and be already configured so all I have to do is install and be done with it.

Also how would you partition a hard drive that is 500gb so that the root, swap, and home are all seperate from each other? I want to be able to have enough room in root available so I don't run out of room to install things from synaptic like the programs I use and updates that come out but at the same time keep things seperate that way if I ever do another reinstall I will be able to reinstall and not have to worry about loosing my home partition again that has everything in it.

Thanks for anymore help and the help you have given me through all of this. I had tried google before asking on the forum about the error I was having and the stuff I found didn't work from it either.

Thanks.:(

---

### Post by Stefan Stryjecki on 2008-05-15
Hi.

B4 you reinstall try:

sudo chmod 700 /home/chris

This is the same as chmod 700 ~/ IF you're logged in as chris. (~ is a shortcut to the home directory of the active user). But if you were logged in as root then it changed permissions for /root.

As to your another question. I think that 10-15GB is plenty for the root partition (i.e., "/"). I never had more than 7-8GB used on it. It is generally advised that you reserve for swap the same amount of memory as your RAM (or a little more - if you have little RAM it might be the double). E.g. I have 1GB RAM and 2GB swap. You can reserve the rest for your home partition.

However, if you have such a big disk, I would set some 100GB aside as a backup partition. You could write a simple bash script saving the crucial elements of your home directory to this backup partition, or do it manually once in a while.

Sorry I couldn't help you more.

---

### Post by cchester on 2008-05-15
> **Stefan Stryjecki said:**
> Hi.

B4 you reinstall try:

sudo chmod 700 /home/chris

This is the same as chmod 700 ~/ IF you're logged in as chris. (~ is a shortcut to the home directory of the active user). But if you were logged in as root then it changed permissions for /root.

As to your another question. I think that 10-15GB is plenty for the root partition (i.e., "/"). I never had more than 7-8GB used on it. It is generally advised that you reserve for swap the same amount of memory as your RAM (or a little more - if you have little RAM it might be the double). E.g. I have 1GB RAM and 2GB swap. You can reserve the rest for your home partition.

However, if you have such a big disk, I would set some 100GB aside as a backup partition. You could write a simple bash script saving the crucial elements of your home directory to this backup partition, or do it manually once in a while.

Sorry I couldn't help you more.

Thaks for the reply.

I had to do sudo chmod 700 ~/ because I was logged into the console under my username.

So I typed what you said and then typed ls -ld and it reported:

drwx------ 89 root root 12288 /home/chris

and I then rebooted to the same error.

Thanks for trying to help.

---

### Post by Stefan Stryjecki on 2008-05-15
Yeah. So it says that your home directory is owned by root. No wonder you can't log in.

Didn't you run "sudo chown -R chris:chris /home/chris"?
You should have.

---

### Post by cchester on 2008-05-15
> **Stefan Stryjecki said:**
> Yeah. So it says that your home directory is owned by root. No wonder you can't log in.

Didn't you run "sudo chown -R chris:chris /home/chris"?
You should have.

Thnaks I ran what you said:

sudo chown -R chris:chris /home/chris

then ran ls -ld to see what it said and got this reported:

drwxr-xr-x 89 chris chris 12288

The only this is I still get the .dmrc error and .ICEauthority error abd needing to be 644.

Still stuck at the loging screen.

---

