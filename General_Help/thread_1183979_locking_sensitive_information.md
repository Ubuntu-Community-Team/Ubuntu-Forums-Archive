---
title: "locking sensitive information?"
date: 2009-06-10
forum: General Help
---

### Post by platinumlolita on 2009-06-10
I've just got my dell mini 9 in the mail! YAY!
It came pre-installed with hardy.
I was wondering if I can get something like a nautilus plugin or something, that can lock external usb drives with a password. I'd also like to lock folders.
Is there anything like that??

Thanks in advance~

---

### Post by platinumlolita on 2009-06-10
Btw I'm not scared of the terminal, but I like to avoid it when I can...
I will NOT partition my internal storage.

---

### Post by doas777 on 2009-06-10
I use truecrypt for creating encrypted volumes. would that work? the thumbdrive thing would require special encryption hardware/software on the thumb itself, or the user could just put it in another computer to bypass the password.

I'm told that there are some folder encryption features within ubuntu itself, but those always makes me wary.

---

### Post by platinumlolita on 2009-06-10
> **doas777 said:**
> I use truecrypt for creating encrypted volumes. would that work? the thumbdrive thing would require special encryption hardware/software on the thumb itself, or the user could just put it in another computer to bypass the password.

I'm told that there are some folder encryption features within ubuntu itself, but those always makes me wary.

well, short of gluing the volume to the slot or melting it in, that's not my solution...

aaaand you're told? can you link me to a thread or something? those would be perfect!

tyvmmmmm

---

### Post by Agent ME on 2009-06-10
By locking sensitive information, are you trying to protect the data from other users of your computer, or people who might steal your laptop or hard drive for that data?

In the first case, simply right-clicking the folder, Properties, Permissions, and set the Folder and File Access for Group and Others to None.

However, if someone were to put the hard drive into a different computer or ran a different OS from a cd, Linux's file permissions would mean nothing to the other system, and they could read whatever files. If this is a worry, then you want to look into encryption.
This is easy to do on Ubuntu. Start a terminal, enter
```
ecryptfs-setup-private
```
press enter, and follow the directions. Log out and log back in, and you'll see you now have a folder in your user's home folder called "Private". Any files put in here are automatically encrypted, and can only be accessed while you're logged in after entering your password.

---

### Post by platinumlolita on 2009-06-16
> **Agent ME said:**
> By locking sensitive information, are you trying to protect the data from other users of your computer, or people who might steal your laptop or hard drive for that data?

In the first case, simply right-clicking the folder, Properties, Permissions, and set the Folder and File Access for Group and Others to None.

However, if someone were to put the hard drive into a different computer or ran a different OS from a cd, Linux's file permissions would mean nothing to the other system, and they could read whatever files. If this is a worry, then you want to look into encryption.
This is easy to do on Ubuntu. Start a terminal, enter
```
ecryptfs-setup-private
```
press enter, and follow the directions. Log out and log back in, and you'll see you now have a folder in your user's home folder called "Private". Any files put in here are automatically encrypted, and can only be accessed while you're logged in after entering your password.

Well, it's an SSD inside. And the boot menu is not very good at booting other volumes. I already have it locked with my pass. I just want to lock additional folders containing rather *cough *questionable* things.
The terminal suggestion sounds good. Is there a way I can change the password for the Private folder so it's different from the login password?

---

### Post by platinumlolita on 2009-06-18
wanna make this clear to you all~~~

I have R rated fanfics on my mini 9 and dont want cousins reading them. Is that better? How would I lock them in a folder? Maybe I'll just resort to hiding the flash drive...

---

### Post by regal_dunce on 2009-06-18
Here's what I'd do:  you can make a folder in your home direcory that belongs to root, and change the permissions so that only root can read it.  This way, if you don't tell your cousins your administrative password, they can't read the folder:

```

sudo mkdir private
sudo chmod 700 private

```

Then you'll have to use "sudo" to copy anything in or out of that folder, and no one will be able to display it's contents without the root password.  If your cousins open a nautilus window, there will be a little lock on that folder and if they click it, they won't be able to get into it.

Sometimes the simplest things are the best.

---

### Post by bodhi.zazen on 2009-06-18
> **regal_dunce said:**
> Here's what I'd do:  you can make a folder in your home direcory that belongs to root, and change the permissions so that only root can read it.  This way, if you don't tell your cousins your administrative password, they can't read the folder:

```

sudo mkdir private
sudo chmod 700 private

```Then you'll have to use "sudo" to copy anything in or out of that folder, and no one will be able to display it's contents without the root password.  If your cousins open a nautilus window, there will be a little lock on that folder and if they click it, they won't be able to get into it.

Sometimes the simplest things are the best.

My guess is that will not work as I am going to guess the external drive is either FAT or NTFS =)

And what is to prevent people from circumventing those protections, especially on a removable device ?

I advise you use encryption, either Truecrypt or ecryptfs

[http://bodhizazen.net/Tutorials/Ecryptfs](http://bodhizazen.net/Tutorials/Ecryptfs)

---

### Post by regal_dunce on 2009-06-18
> 
My guess is that will not work as I am going to guess the external drive is either FAT or NTFS =)

And what is to prevent people from circumventing those protections, especially on a removable device ?


Quite right, I should have said that this will only work on the HD.  

However, it sounds to me like platinumlolita is much more concerned about visibility of certain files to people he allows to use his computer, rather than true encryption of his data.  That said, given that you've shown where to find a file-encryption tutorial, I'll concede that it's a much better approach.

---

### Post by platinumlolita on 2009-06-20
> **regal_dunce said:**
> Quite right, I should have said that this will only work on the HD.  

However, it sounds to me like platinumlolita is much more concerned about visibility of certain files to people he allows to use his computer, rather than true encryption of his data.  That said, given that you've shown where to find a file-encryption tutorial, I'll concede that it's a much better approach.

Everybody has been a lovely help! I'll give these a go.
My filesystem needs no protecting, I should have said so in the title of the thread... I'm just worried about one folder, that's it! If changing permissions to root on one folder will do the trick, that should work just fine.

Umm but if I want to get into the folder, do I go into sudo in terminal then open it? Or do I change permissions back using my admin password?

---

### Post by bodhi.zazen on 2009-06-20
changing permissions back will work and is probably best, just do not forget to change them back again ;) . accessing as root will work as well.

---

### Post by platinumlolita on 2009-07-01
how about truecrypt? it mounts filesystems if I give it a password. That's much faster, but is it safe??

---

