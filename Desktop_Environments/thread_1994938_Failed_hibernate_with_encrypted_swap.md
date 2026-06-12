---
title: "Failed hibernate with encrypted swap"
date: 2012-06-03
forum: Desktop Environments
---

### Post by inneedofsomehelp on 2012-06-03
Hi all,

I have an encrypted home partition, and therefore also swap. I tried to install 'hibernate' the other day, forgetting that this would not work with encrypted swap. The machine went into hibernation and now when I try to restart the machine, it just sits at the loading screen (showing the 5 scrolling dots) endlessly...

I am very new to linux, so am pretty clueless but have followed several posts on here and elsewhere from google to try to fix this. If I edit the boot command to add 'noresume', then I can get back in - but the next time I restart, I have the same problem. I have tried unmounting the swap and re-making it, but the problem persists. I guess there must be a flag somewhere telling the system that it has a saved state - but I can't seem to reset this.

Can anyone give me any clues??

Thanks!

---

### Post by hictio on 2012-06-03
On what hardware are you running?
I have been using an encrypted $HOME before and all thru Lucid Lynx on laptops (mostly Thinkpads) and I never had any issue going in and back from either suspend or hibernate.

---

### Post by inneedofsomehelp on 2012-06-04
I am on a Lenovo z370 laptop. I have read several places that hibernate with an encrypted swap would require fixing the encryption key. So I get why it didn't work. But now that I have cleared swap, etc I don't know why it still thinks there is a hibernation image to restore. Surely on a successful shutdown, it should clear that?

---

### Post by Toz on 2012-06-04
Try booting once with the **noresume** kernel parameter to disable the resume cycle and restore the swap space.

---

### Post by inneedofsomehelp on 2012-06-04
Yes, that is what I have done. It is the only way I can boot again.

However, everything I have tried to do to restore the swap has not fixed the root problem, because at the next boot, it requires noresume again.

This is why I am confused - is there a flag somewhere in /boot/ that isn't being cleared?

---

### Post by cortman on 2012-06-04
Hi, this is a known problem. I just got done transferring [Paddy Landau]("http://ubuntuforums.org/member.php?u=572807")'s excellent tutorial on it to the wiki- page [here.]("https://help.ubuntu.com/community/EnableHibernateWithEncryptedSwap")

---

### Post by inneedofsomehelp on 2012-06-04
Thanks. Yes, I think I saw the original post on enabling this. However, I was hesitant to implement it until the previous problem was fixed. But if you think this is safe to go ahead, then I will give it a shot..
Is there any downside to doing this? I guess it will always ask for a password at bootup - or is this only if resuming from hibernation?

---

### Post by inneedofsomehelp on 2012-06-04
Right... so this is strange...

I followed the steps in the link. I did not hibernate, but just restarted. It restarted fine. So I thought this must have cleared whatever the previous problem was.

So then I undid all steps (plus those detailed [here]("http://www.logilab.org/29155")) so that I could get back to the original state (normal, encrypted swap with no hibernate functionality and no password to enter on boot).

Now, when I restart, the same problem is back.

Any ideas??

Thanks for all suggestions so far. I really thought I had fixed it when I managed to restart! :(

---

### Post by cortman on 2012-06-04
Why don't you post in the original tutorial thread with details on what went wrong? The author will be sure to follow up on your problem there. Good luck!

---

### Post by inneedofsomehelp on 2012-06-04
To be honest, since there were no other replies, I assumed it was locked in some way.. so I could reply there.

However, this is unrelated to his post so I don't want to clutter his post with something not caused by his original tutorial. What is best practice here? Post anyway?

---

### Post by cortman on 2012-06-04
The nature of the new wikified tutorial threads is that the original thread (containing the tutorial) becomes the support venue thread for that wiki. It's considered standard practise for people to post questions/problems with a tutorial thread in that thread. Most of the time the author is subscribed to it so he can handle support requests as they come in. Go ahead and post.

---

### Post by inneedofsomehelp on 2012-06-04
Ok. Thanks. I will give it a go!

---

### Post by Paddy Landau on 2012-06-04
Right. First off, please do **not** install [hibernate]("apt:hibernate") — in fact, please uninstall it so that you do not accidentally use it!

The correct way to hibernate in Ubuntu from the terminal is with this command:```
sudo pm-hibernate
```Now, let's find out what's happening on your system.

[LIST=1]
[*]Boot into Recovery Mode. (If you don't know how: Press Shift when you start your computer and keep it held down until you see the purple Grub menu. Use your arrow key to proceed to the "recovery menu" option, normally the second, and press Enter.)
[*]Drop to Root Shell Prompt.
[*]Enter the following two commands:```
mount --options remount,rw /
mount --all
```
[*]Now enter the following five commands and post the results of each here (please enclose your results between [noparse]```
[/noparse] and [noparse]
```[/noparse], or highlight the results and press the # button in the toolbar). Note that the first and third commands use the lowecase letter "l", not the digit "1", after the minus-sign.
```
ls -lA /home
parted --list
fdisk -l
cat /etc/fstab
swapon --summary
```
[/LIST]

---

### Post by inneedofsomehelp on 2012-06-05
I did have hibernate installed. I have removed it. That is probably what I used to hibernate last time.

Holding shift during boot up doesn't seem to do anything, but the first time I tried it, it booted ok.. and now it looks like the problem has disappeared. I haven't a clue what is going on now, since I had restarted several times previously when it hung.

I cannot reproduce it any more, so I guess there is no point in grabbing the outputs now since it will all look fine..?

So sorry to have spent everyone's time on this. I spent about 6 hours yesterday and about about 4 hours on Sunday going round in circles trying to fix this and testing it. And now, I wake up and it has gone away.. bizarre. I did boot off a USB stick in the mean time, but I can't imagine that would have changed anything...

Thank you so much for your time everyone. If it comes back as quickly as it disappeared, I will be back! :)

---

### Post by Paddy Landau on 2012-06-05
I'm glad it's been resolved. Please [mark the thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

If it does return, follow the [post=11998296]instructions in my post[/post] and we'll see what we can do.

---

### Post by notjingo on 2012-12-04
Sorry to reopen this thread if it's closed, but I am also having the exact same problem.

I followed the guide to enable encrypted swap hibernation ([[COLOR=#1155cc][FONT=Arial]_https://help.ubuntu.com/community/EnableHibernateWithEncryptedSwap_[/FONT][/COLOR]]("https://help.ubuntu.com/community/EnableHibernateWithEncryptedSwap")[COLOR=#980000][FONT=Arial][/FONT][/COLOR]) and everything went well except my system still will not resume from hibernation. It powers off fine but when started up again it just does a full reboot. I am asked for my crypt-swap passphrase during every Ubuntu boot.

Can you give us instructions on how to revert the changes made in the tutorial? Since hibernation is still not working I'd like to undo this. 

Alternatively if you can offer any thoughts on why hibernate is still not working with this method that would be great too. I have had hibernate work on this machine in ubuntu 11 and now I am running 12.10.

Thanks for your help!

---

### Post by Paddy Landau on 2012-12-04
> **notjingo said:**
> I followed the guide to enable encrypted swap hibernation…
If you want it to work, you could try going through the steps again, carefully, in case you missed out something. However, I have not tested it on 12.10, although it should work.

> **notjingo said:**
> Can you give us instructions on how to revert the changes made in the tutorial?
I presume that you have an encrypted home folder. (If not, you should have set it up as instructed in the [Preparation stage]("https://help.ubuntu.com/community/EnableHibernateWithEncryptedSwap#Preparation").)

To undo, I need to know whether or not you have an encrypted home folder. To tell whether or not you do, open a terminal and enter the following command, changing [FONT=Lucida Console][COLOR=Navy]notjingo[/COLOR][/FONT] to your actual username:
```
mount | grep -Fc [COLOR=Navy]notjingo[/COLOR]/.Private
```If you see the number [FONT=Lucida Console]1[/FONT], you have an encrypted folder. But if you see the number [FONT=Lucida Console]0[/FONT], you do not have an encrypted folder. (If you see anything else, please let me know.)

Let me know, and we'll progress from there.

---

### Post by notjingo on 2012-12-04
I followed the tutorial exactly and everything seemed to work except or the actual resume of hibernate, as I detailed in my last post. What info or logs should I inspect to find out why it's not resuming?

Also, my home folder IS encrypted.

---

### Post by Paddy Landau on 2012-12-05
> **notjingo said:**
> I followed the tutorial exactly and everything seemed to work except or the actual resume of hibernate, as I detailed in my last post. What info or logs should I inspect to find out why it's not resuming?
Unfortunately, I do not know the answer to your question, sorry.

I am wondering if you have accidentally turned off swap, or if you have more than one swap partition.

Open a terminal and enter the following commands. Please post the results here (between [FONT=Lucida Console][noparse]```
[/noparse][/FONT] and [FONT=Lucida Console][noparse]
```[/noparse][/FONT] tags).
```
sudo parted --list
swapon --summary
sudo cryptsetup status cryptswap1
```

---

### Post by notjingo on 2012-12-05
From Parted, this is my swap partition:
```
 3      80.0GB  88.6GB  8590MB  primary

```

swapon --summary is now empty, and cryptsetup reports that
```
/dev/mapper/cryptswap1 is inactive.
```

Yes it looks like the swap was deactivated after I encrypted it. How can I reactivate it?

---

### Post by Paddy Landau on 2012-12-06
Thank you for your response. I take it that your [FONT=Lucida Console]parted[/FONT] output did *not* show something like the following:
```
Model: Linux device-mapper (crypt) (dm)
Disk /dev/mapper/cryptswap1: 4409MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0.00B  4409MB  4409MB  linux-swap(v1)
```In that case, it seems as though you do not have an encrypted swap partition at all, and the partition that you do have is not in use.

This explains your computer's failure to hibernate.

[SIZE=3]**Questions**[/SIZE]

Did you install an earlier version of Ubuntu and subsequently upgrade (tell me the versions involved), or was this a fresh installation of 12.10? Did you encrypt your home folder when you originally installed, or did you subsequently encrypt it?

I don't understand how you could have completed the steps in the [Preparation stage]("https://help.ubuntu.com/community/EnableHibernateWithEncryptedSwap#Preparation") of your [hibernation encryption]("https://help.ubuntu.com/community/EnableHibernateWithEncryptedSwap"), when you do not have an encrypted partition! You must have missed out at least some steps, and you could not have repeated it as requested in [post=12387383]my previous post[/post].

[SIZE=3]**What to do now?**[/SIZE]

The first thing to do is to encrypt your partition. Repeat all the steps 1&#8211;13 in the section [How to Set Up Hibernation]("https://help.ubuntu.com/community/EnableHibernateWithEncryptedSwap#How_to_Set_Up_Hibernation"). **Notes:**

[LIST]
[*]Step 2 may return an error. Ignore the error.
[*]Regarding [FONT=Lucida Console]/dev/sdXN[/FONT], in your case [FONT=Lucida Console]N[/FONT] will be 3. I don't know [FONT=Lucida Console]X[/FONT] because you did not post the full output of [FONT=Lucida Console]sudo parted --list[/FONT].
[*]You should have already completed steps 8&#8211;11 and 13 in your previous attempts. Double-check them.
[*]Let me know if you get an error on any step, excluding step 2.
[/LIST]
[SIZE=3]**Test**[/SIZE]

Now repeat the [first-time use test]("https://help.ubuntu.com/community/EnableHibernateWithEncryptedSwap#New_Swap_First_Time_Use") and then [test your hibernation]("https://help.ubuntu.com/community/EnableHibernateWithEncryptedSwap#How_to_Hibernate").

If either of them fails:

[LIST=1]
[*]Post the contents of your file [FONT=Lucida Console]/etc/fstab[/FONT].
[*]Post the **full** results of:```
sudo parted --list
swapon --status
sudo cryptsetup status cryptswap1
```
[/LIST]

---

### Post by notjingo on 2012-12-06
I had the swap partition successfully working (non encrypted) before I went through your tutorial. I was able to encrypt it and in fact I DO have the encrypted swap partition though it stopped working (in terms of swap) after I followed your tutorial. 

Here is the entry from blkid:
```
/dev/sda3: UUID="26f14559-00a2-4993-ab59-e57b6e315579" TYPE="crypto_LUKS" 

```

In terms of the Ubuntu install, it was a fresh 12.10, with an encrypted HOME folder. 

Anyway, I tried to go through your tutorial again, and after entering

```
 sudo mkswap /dev/mapper/cryptswap1
```

I get the error:

```
/dev/mapper/cryptswap1: Device or resource busy
```

I'm assuming this is because the cryptswap1 already exists...

At this point here is the result of "sudo cryptsetup status cryptswap1"

```

/dev/mapper/cryptswap1 is active and is in use.
  type:    LUKS1
  cipher:  aes-cbc-essiv:sha256
  keysize: 256 bits
  device:  /dev/sda3
  offset:  4096 sectors
  size:    16773120 sectors
  mode:    read/write

```

I checked all the other steps in the tutorial and everything looks fine, I have all the right entries in the files. BTW Ubuntu registers my system as having 7.7gigs of RAM, so I have made the swap partition 8 gigs.

I am about to test and see if hibernate works. Will post the results in a couple minutes.

---

### Post by notjingo on 2012-12-06
I just used ```
pm-hibernate
``` to hibernate and I got the same result...

The computer shuts off fine, but then instead of resuming from hibernate, it just reboots completely. During Ubuntu startup, it asks me for the cryptswap password, which I enter, and then it says
```
cryptsetup: cryptswap1 set up successful
```
like in the screenshot from the tutorial, but alas it didn't resume. 

Before I used the hibernate command I made sure to register the changes with 
```
 sudo update-initramfs -u -k all
```

Any ideas? If there's no way to fix this, I can live without hibernate, but I would like to get it to stop asking for the password every time I boot. 

Will using the "/etc/luks-keys/" option in the crypttab entry get rid of the password prompt while keeping the swap encrypted?

---

### Post by Paddy Landau on 2012-12-06
Thanks for your responses. I think we are a little closer, especially as your swap partition has mysteriously started working now!


[LIST]
[*]Now that your swap partition is working, try hibernating again. Does it work?
[/LIST]
 
If not, I wonder if 12.10 uses a different mechanism from 12.04. I have not tested this on 12.10, so perhaps I need to do so. But I won't have time until the weekend.

** If you want to undo your hibernation**, follow these steps. Warning: I have not tested this process, but I would be surprised if it failed to work.

[LIST=1]
[*]```
sudo swapoff --all
sudo cryptsetup luksClose /dev/mapper/cryptswap1
```
[*]Open your Disks utility (from the Dash). Find your hard drive (on the left) and click your swap partition, [FONT=Lucida Console]/dev/sda3[/FONT], on the right.
[*]Click Format Volume. Type: Swap Space. Name: (anything you want). Encrypt underlying device. Format.
[*]Undo steps 8–11 and 13 in [How to Set Up Hibernation]("https://help.ubuntu.com/community/EnableHibernateWithEncryptedSwap#How_to_Set_Up_Hibernation"), then repeat step 12.
[*]Reboot.
[/LIST]
 
You should no longer have hibernation available in your menu.

Now, enter the command:
```
sudo swapon --all
```Reboot again.

Check whether or not you have a swap:
```
swapon --status
```If you still do not have swap, post the contents of your file [FONT=Lucida Console]/etc/fstab[/FONT] here.

---

