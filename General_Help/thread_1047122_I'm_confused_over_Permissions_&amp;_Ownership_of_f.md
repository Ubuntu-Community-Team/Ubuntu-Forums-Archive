---
title: "I'm confused over Permissions &amp; Ownership of files on my memory stick!"
date: 2009-01-22
forum: General Help
---

### Post by SteveDee on 2009-01-22
This is the scenario:-
 - I create a file on 'buntu computer #1, which makes me the Owner and the Group is steve
 - I copy the file to my memory stick, and now I am still the Owner, but the Group is root
 - I try to change the Group on 'buntu computer #2 (using Nautilus > Properties > Permissions) but it says I do not have Permission to change the group.

How can this be, if I am the Owner of the file?

---

### Post by SteveDee on 2009-01-25
I'm probably talking to myself, but here goes anyway...

By experimentation I've worked out that when you plug a Fat32 memory stick into your 'buntu computer, the current user becomes the owner of files, and the Group is root.

If you log out, then log in as another user, you won't be able to access the files on the stick until you unmount, remove, then re-attach (mount). Now the owner is the new user.

This is the main source of confusion for my family when using 'buntu. 

Since Fat32 was not designed for Linux, this is just the default behaviour that allows a Fat stick to work with Linux. However, it would probably be more user friendly by allowing "everyone" to rwx all Fat files & directories.

Of course when you create an Ext3 file system on a memory stick, Permissions and Ownership remain constant. So you can set your self as the owner and Group = your group, and that's the way it will stay. However, you can't then carry files to a Windows machine via your stick.

---

### Post by callan79 on 2009-01-25
> **SteveDee said:**
> Of course when you create an Ext3 file system on a memory stick, Permissions and Ownership remain constant. So you can set your self as the owner and Group = your group, and that's the way it will stay. However, you can't then carry files to a Windows machine via your stick.


Hello,

I see the problem you're having, it's just sort of one of those things. I guess in 'most' situations, a USB stick would be owned by one person, i.e. single user. Any files to be shared between multiple users would be on the local hard disk or a network share.

Is there a particular reason why you want to access files on a USB stick, then log in as another user, and access those file again? Just curious ...

Either way, you might already know, but you can get a Windows ext3 driver from [http://www.fs-driver.org/](http://www.fs-driver.org/)

Hope this helps :)

Cheers
Callan

---

### Post by SteveDee on 2009-01-25
> **callan79 said:**
> 


Is there a particular reason why you want to access files on a USB stick, then log in as another user, and access those file again? Just curious ...


Callan

No, you're right...no one in their right mind would want to do this.

Its just that having deleted Windows from the family computer and replaced it with 'buntu, I get complaints when something non-windowsie happens. And a few times I've been abused because someone can't access the files on their USB stick.:(

Now that I know its because the computer was started using person#1 account, but with person#2 stick already plugged in....then person#2 comes along and logs on, (are you still with me?) I can put them right. ;)

Oh and thanks for the link. The reason our sticks are still Fat is due to work & school commitments, where windows still rules.

---

### Post by mb_webguy on 2009-01-25
I can see why this might cause a bit of frustration at first, but since the solution is simply to remove the USB drive and plug it back in, I wouldn't think it would be a major problem...

---

