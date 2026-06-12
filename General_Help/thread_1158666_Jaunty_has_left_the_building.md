---
title: "Jaunty has left the building"
date: 2009-05-13
forum: General Help
---

### Post by waltk on 2009-05-13
I hosed my version 9.04, by running 

sudo apt-get remove python  

and I watched in horror as 90% of my applications vanished.  I tried to apt-get install python, but all networking functionality is gone as well so no dependencies can load from the network.

What is the best way to get out of the woods?   Everything seems OK booting to the 9.04 "Live-CD" instance so if the answer is to copy my files off, and reinstall life will go on.

---

### Post by petrus4 on 2009-05-13
> **waltk said:**
> I hosed my version 9.04, by running 

sudo apt-get remove python  

and I watched in horror as 90% of my applications vanished.  I tried to apt-get install python, but all networking functionality is gone as well so no dependencies can load from the network.

What is the best way to get out of the woods?   Everything seems OK booting to the 9.04 "Live-CD" instance so if the answer is to copy my files off, and reinstall life will go on.

I've had this happen as well, with both Debian and Xandros, although not Ubuntu.

It's because of idiotic package developers who assign dependencies to packages which **shouldn't** be marked as deps of each other.

Before I offer solutions though, I'll ask the question...how long have you been using Linux for?  Is Ubuntu your first distro?

---

### Post by CatKiller on 2009-05-14
If you've got your live cd, you can use it as a local repository of packages. When you put the cd in, the package manager should ask you if you want to add it as a source. Say yes, and you should then be able to re-install the ubuntu-desktop package from the cd.

---

### Post by ad_267 on 2009-05-14
> **petrus4 said:**
> It's because of idiotic package developers who assign dependencies to packages which **shouldn't** be marked as deps of each other.

I'm pretty sure that a lot of these packages really do need python to function. A huge number of applications used in the Ubuntu desktop are written in Python. And usually you get a gigantic list of packages which are going to be removed followed by a "Do you want to continue? Yes/No?". At which time you press N. ;)

I think your only real option is to use a live CD to recover your data, then reinstall like you've already said. A separate /home partition comes in handy in these situations.

---

### Post by Junkieman on 2009-05-14
What Catkiller said ;) Install the **ubuntu-desktop** package to restore the default Ubuntu applications, you might miss some of the third-party packages you had installed.

Always, Always... Always pay attention to the details when running any command as SU. I'm also guilty of doing this before :p

---

### Post by MrFSL on 2009-05-14
> all networking functionality is gone as well so no dependencies can load from the network
I'm sure **waltk**  appreciates all the help but he said his network is hosed.

Python is not a requirement/dependancy for network connectivity. It might, however, be required by the gnome network manager. I would advise plugging in directly (non-wireless) to your internet. This way you can use ifconfig to get connected. 

Once connected you can then I suggest:
```
sudo apt-get install ubuntu-desktop
```
as suggested by **Catkiller** and **Junkieman**

In the future know that you can see the result of running apt-get without actually having it execute. Check out:```
apt-get help
```

---

### Post by Salute on 2009-05-14
wow
I did something like this too, luckily on a new installation so I just re-installed

---

### Post by waltk on 2009-05-14
Wow - those are some quick responses.  Since what I did was totally ridiculous, uh, yes, I DO want to remove 900 programs, I assumed I would be flamed mercilessly;  I appreciate the restraint.  

There appears to be 2 solutions, use the Live CD as a local repository, and hook up to the internet using the lan, accessing the Ubuntu repository.  I have a couple follow up questions.  

With CatKiller's suggestion, I only have command line available, so how do I add the LiveCD as a repository?

For MrFSL, I will give that a shot.  I did hook up directly to my router with an ethernet cable, but the network was still unavailable, so I will try to get that back up with ifconfig.  I was unsure how to proceed on that.

Thanks again for the suggestions.

---

### Post by Saint Angeles on 2009-05-14
type:
```
sudo nano /etc/apt/sources.list
```

for your repository list. then add your CD-ROM by adding (or uncommenting):
```
deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
```

i think thats how you can do it... i'm not 100% sure though. then you could run:
```
sudo apt-get install ubuntu-desktop
```

---

### Post by ELD on 2009-05-14
You don't even need to edit anything like what [Saint Angeles]("http://ubuntuforums.org/member.php?u=409668") said, when you put your said in a box should pop up saying it has found it and asks what you want to do :)

---

### Post by perlluver on 2009-05-14
> **ELD said:**
> You don't even need to edit anything like what [Saint Angeles]("http://ubuntuforums.org/member.php?u=409668") said, when you put your said in a box should pop up saying it has found it and asks what you want to do :)

He has no GUI, just a command line, therefore I don't think it will pop up.

---

### Post by CatKiller on 2009-05-14
> **waltk said:**
> With CatKiller's suggestion, I only have command line available, so how do I add the LiveCD as a repository?

Ah. ```
sudo apt-cdrom add
``` is the command-line way, I believe, although I've never used it myself. Hopefully **man apt-cdrom** will tell you anything else that you need to do to make it work.

---

### Post by ELD on 2009-05-14
Ah my bad.

---

### Post by waltk on 2009-05-14
Thanks again, everyone. I will give these a shot, and post the results in case anyone else finds themselves in a similar state.  

As a side note, I have been on Ubuntu for about 2 months, and am more than glad that I jettisoned XP.  I had become so used to installing with apt-get, I forgot that any good tool, like say a chain saw, needs to be treated with respect.

---

### Post by waltk on 2009-05-15
Thanks again for the help everyone.  I just wanted to close the loop in case anyone else found themselves in a similar position.

The apt-cdrom add command did seem to take, but it did not ultimately provide better results than the previous  apt-get install attempt.

I decided to pursue the wired ethernet connection and that did work, but with some coaxing.  I have no doubt that this could have been slicker, but this is what I did:

>sudo  vi /etc/network/interfaces

Adding the following:
auto eth0
iface eth0 inet dhcp

(If you're not used to vi, it can be odd.  I to insert the lines.  Esc : wq to save and close out)

> sudo ifconfig eth0 up

>/etc/init.d/network restart

apt-get -f install
apt-get install ubuntu-desktop

After about 30 minutes all was right with the world.  As a side note, I had to run
sudo ifconfig eth0 down to start browsing again since there was an IP conflict.

---

### Post by CatKiller on 2009-05-16
> **waltk said:**
> (If you're not used to vi, it can be odd.  I to insert the lines.  Esc : wq to save and close out)

**nano** is probably a more new-user-friendly command-line text editor.

Glad you're up and running again.

---

