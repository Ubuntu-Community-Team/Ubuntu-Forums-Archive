---
title: "Locked Out! Can't reset root passwd."
date: 2008-06-12
forum: Desktop Environments
---

### Post by fuzzy68 on 2008-06-12
:confused:I think I just totally lost my mind...been at this machine ALL day trying every possible suggestion on the web with no luck.

Duel boot system:
Win XP
Ubuntu 7.10

I used to have Dapper Drake.  I installed 7.10 over it recently.

I forgot all my usernames passwords from Drake. Pretty lame, I know.

So I tried going into recovery mode and found what looked like my username:

cat /etc/passwd | grep

Tried resetting that one...no luck.

Tried resetting root so many times either in recovery or using live cd that now it totally spits out every attempt.  I even tries some suggestion about altering Grub entries:

adding:

", single"

and:

", init=/bin/bash"

Does anyone have any further suggestions?  Should I just install the newest version over this one?

Thanks in advance.

---

### Post by kdcoetzee on 2008-06-12
Ubuntu stores its password in /etc/shadow (have to be root to see it I think)

So if you use a liveCD, mount your filesystem , and then go edit the shadow file.

Here is a explanation of the shadow file [http://www.cyberciti.biz/faq/understanding-etcshadow-file/]("http://www.cyberciti.biz/faq/understanding-etcshadow-file/")

I think if you leave the password part out of root. you would have a blank password.
the "!" represents the password for root.

```
root:!:14039:0:99999:7:::
```

to

```
root::14039:0:99999:7:::
```

I have never edited shadow file. Just saw someone do it one.

---

### Post by aysiu on 2008-06-12
Juggernaut_KDC has a good suggestion.

In the future, don't set a root password. Then you won't be locked out.

---

### Post by imneo on 2008-06-12
this is not a problem to fix ;)
reboot your system, when grub is loading press "Esc"
then select your usual boot kernel (probobly the first line)
do not press enter, press "E" for edit 
at the end of the line enter the word "single" 
then press enter then press "B" to boot at single user mode

when asked press "Ctrl D" 
you are now able to change your root password
do:

passwd root

now enter your new password.
reboot your system.
Done.

if you still have a problem post at this help Forum:
[http://www.scripts-net.com](http://www.scripts-net.com)

---

### Post by fuzzy68 on 2008-06-13
2 completely different suggestions- Cool

First one, KDC and Aysiu,

I don't know how to edit the shadow file.  I know what it is.  I understand what you mean in general.  Can you please clarify.  I have mounted my drive using liveCD before.

To All,

Apologies for my obvious lack of proficiency with Linux.

When I use liveCD the very first screen that appears is the black with Ubuntu logo and several choices "Install or Start", "Diagnostics" (i think), etc.. There is also the option to hit F6 which makes a kind of terminal strip appear near bottom of screen.

I think that, by accident, I was able to get to a command prompt from here??? Or was it within the CD desktop Terminal window???

Can you clarify?

Second one, Imneo,

I did exactly what you suggest twice and am still at the same place.  Thank you though, and I might try it again for the heck of it.

Aysiu,

I wasn't aware that I did set a root password at any point...probably did it accidentally?  In the future, I'll be sure not to.

---

### Post by fuzzy68 on 2008-06-13
The most recent time I tried your suggestion the boot went straight to the "enter root password pr hit control D" prompt.

---

### Post by fuzzy68 on 2008-06-13
Also,

Mounted drive again just to see if I could and,,,,I again tried to reset the root password by :

passwd

i do get the prompt to do that and as soon as I hit one key I'm propted to re:enter the password...that's reight, one digit only.  When I repeat this process I recieve a message that says:

"Authentication token lock busy"

"Password unchanged"

HHHmmmm.

---

### Post by kdcoetzee on 2008-06-13
> **fuzzy68 said:**
> 2 completely different suggestions- Cool

First one, KDC and Aysiu,

I don't know how to edit the shadow file.  I know what it is.  I understand what you mean in general.  Can you please clarify.  I have mounted my drive using liveCD before.

When I use liveCD the very first screen that appears is the black with Ubuntu logo and several choices "Install or Start", "Diagnostics" (i think), etc.. There is also the option to hit F6 which makes a kind of terminal strip appear near bottom of screen.


That is a thing of linux , there is a million ways to get the same result.


i am not very good with explaning things I will try my best..
Ok , so when the liveCD is booted up. go to applications > accessories > Terminal(or alt-F2 is like windows run dialog; then just time terminal)

Then you have to go the the /etc on your mounted drive.I think the mounted drive will be in the /media  folder. "cd /media"

When you are in the /etc folder on your mounted drive 

```
sudo gedit shadow
```

then you can remove the "!" were root is written.

then your root will be with out a password.

---

### Post by fuzzy68 on 2008-06-13
Thank you oh barer of knowledge. I will apply your advice later this eve.  Cheers.

---

### Post by fuzzy68 on 2008-06-14
So I'm pretty sure the whole mounting thing is not going well.

I boot using the cd, desktop comes up, open a terminal, type:

sudo mount /dev/sda3 /mnt

then I really don't know if that does the trick or not.

next, I type:

sudo gedit shadow

The shadow file opens but shows only a blank window.  The title bar at the top of the window shows "/home/ubuntu" as what looks like the address of the shadow file.

Is this just the cd's shadow file?

I guess I'm pretty spun around on this.

---

### Post by aysiu on 2008-06-14
Let's take it one step at a time.

With the live CD booted, can you post the output of these commands? ```
sudo fdisk -l
df -h
```

---

### Post by kdcoetzee on 2008-06-15
you must be in the /etc folder of your mounted drive.
you are trying to open a blank shadow file.


with this command you will see all your partitions on your harddrive
so just make shore you mount the correct partition(thanks aysiu)

```
sudo fdisk -l
```

ok go to the /mnt folder. "ls" to see what is in the folder if you see your mounted drive then this command might help.

```
sudo gedit {mounteddrive_here}/etc/shadow
```

---

### Post by aysiu on 2008-06-15
Or```
gksudo gedit
``` instead of *sudo gedit*

In the case of Gedit, it may not matter that much, but it is a good habit for users to get into to use *gksudo* and *kdesu* for graphical applications, as sometimes it does matter.

Read more [here](http://www.psychocats.net/ubuntu/graphicalsudo).

---

### Post by fuzzy68 on 2008-06-15
Thanks for your suggestions...I just blew up my PC...just kidding.  I did install 8.04 over the top and all is now good.

---

