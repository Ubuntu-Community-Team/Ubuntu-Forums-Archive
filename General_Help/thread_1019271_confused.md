---
title: "confused"
date: 2008-12-23
forum: General Help
---

### Post by newbie321 on 2008-12-23
Is there a default root password? i cannot log in to root at all and dont remember setting a pass for it

---

### Post by paydaydaddy on 2008-12-23
I don't really know the answer to the question, but I do know that you can do pretty much anything you need to do by using sudo. Give the specifics of what you are trying to do and you will surely get some help to achieve your goal without logging in as root. That said, you will probably get the real answer to your question from one of the linux gurus lurking about. Good luck.:)

---

### Post by monstermudder78 on 2008-12-23
IOP1
:popcorn:

[http://ubuntuforums.org/showthread.php?t=842738]("http://ubuntuforums.org/showthread.php?t=842738")

---

### Post by CatKiller on 2008-12-23
You should probably read [this page]("https://help.ubuntu.com/community/RootSudo").

---

### Post by DirtDawg on 2008-12-23
No, there is no default password. You should have been prompted to create one. If you weren't, then there's some kind of problem (unless you're using the live cd. Then you shouldn't need one.).

If you have installed Ubuntu, but don't have the password, look up something like, "Ubuntu I forgot my password" in Google and you will likely get plenty of tips about getting a new one. 

Good luck.

Edit: Sorry, but I think I completely misunderstood your question.

---

### Post by jrusso2 on 2008-12-23
Ubuntu does not use a root password or account.  We use sudo and it uses your user account.  This gives you ten minutes of root level privledges.  I could tell you how to make a root account and set a password but this is not allowed on the forum.

But this information is easily available elsewhere but really its not needed.

---

### Post by DirtDawg on 2008-12-23
> **jrusso2 said:**
> Ubuntu does not use a root password or account.  We use sudo and it uses your user account.  This gives you ten minutes of root level privledges.  I could tell you how to make a root account and set a password but this is not allowed on the forum.

But this information is easily available elsewhere but really its not needed.

Why is it taboo to talk about creating root accounts?

---

### Post by Locutus_of_Borg on 2008-12-23
> **jrusso2 said:**
> Ubuntu does not use a root password or account.  We use sudo and it uses your user account.  This gives you ten minutes of root level privledges.  I could tell you how to make a root account and set a password but this is not allowed on the forum.

But this information is easily available elsewhere but really its not needed.

it's not allowed on this forum?  So if by chance you mess up something in your home folder...that .gvfs(?) file or whatever for example, you have no way short of using a livecd to fix it whereas with any other linux distribution you would simply login as root and fix the issue...well i guess there's single user mode...but seems just having a root account would be easier

to the OP, in some distributions, in the live session, the root password is the name of the distro, if thats what you mean, othertimes, you need to set one using passwd before you can use root...ubuntu should have nothing of the sort as the initial user is granted root access only by using su/sudo, if somehow you can no longer su, reboot into single user mode or use a livecd and edit /etc/sudoers to include your user name as in the example within that file that mentions the wheel group

---

### Post by dcstar on 2008-12-23
> **DirtDawg said:**
> Why is it taboo to talk about creating root accounts?

I don't think it is "Taboo", but just not recommended for most users as it opens up a potential security hole. I have seen the instructions for enabling the root account posted in these forums many (hundreds?) times, so it isn't difficult to find.

I enable the root account on my system, I am behind a NAT device so there is no direct Internet access to my machine for anyone to try and log in as root. My wireless router has MAC filtering and WPA2 enabled so I feel relatively secure there as well. As for any apps/scumware that may be able to use a root account to somehow compromise my machine, good luck to 'em as I don't readily add third-party repositories or install suss packages.

---

### Post by mshipman on 2008-12-23
If you *really* want to enable the root account, just run: sudo passwd root

---

