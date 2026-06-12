---
title: "Can't Log In! (GDM Problems! links2 is a life saver!!!)"
date: 2006-08-25
forum: Desktop Environments
---

### Post by Raavea on 2006-08-25
Aaagh! 
I just tried to log in, and it told me that it couldn't write to some file in the home directory because it was out of disk space. 

I'm sure I haven't filled up the drive it's on, but I don't know any bash commands! How can I delete things from the command line? I know dir and cd *(lucky I used to be obsessed with exploring windows via DOS when I was little!)* but how do I delete a file? 

I tried del filename and delete filename but neither worked.

What do I do? *hyperventilates* 

Thankfully I installed links2 after it was recommended by a guy after the xorg errors. I updated that *(xorg)* too, to level 10.4 like it wanted yesterday, and xorg told me some kind of error too about the GDM before chucking me into the DOS-like command-line bit.

My brain hurts!

---

### Post by Raavea on 2006-08-25
Gack.. I'm gonna try using Goooogle with this links thing... Wish me luck! 0_0

I still don't see how I could have filled my drive up. And if I had.. Shouldn't there have been some warning when I did? Or before I shut down last night?

---

### Post by xtknight on 2006-08-25
Relax.  All is fine.  :)

The rm command will remove a file.
mv = move, cp = copy

You may need to prefix the commands with one called sudo to get you admin access.  This will ask for your user's password.

e.g.,
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

Can you type the following and see if you have any free space on / (or /home if it exists)?

df -h

---

### Post by Raavea on 2006-08-25
Well I just checked for rootkits *(call me paranoid, but my girlfriend left bittorrent downloading on her windows laptop all night, and we're networked..)* and it came up with an interesting error:
```
EXT3-FS error (device hdb1): ext3_get_inode_loc: unable to read inode block
```
Odd.. Sounds to me like hdb is dead.. Anyhow, I'll go try that df thing. Found a site on google telling me the command 'quota' would do that, but it didn't actually work.

---

### Post by Raavea on 2006-08-25
Okies, the command you gave me output what's below, there might be typos as I had to write it on a bit of paper and type it in..
```
Filesystem    Size    Used    Avail    Use%    Mount
/dev/hdb1     19G     3.5G    14G      20%     /
varrun        252M    76K     252M     1%      /var/run
varlock       252M    4.0K    252M     1%      /var/lock
udev          252M    116K    252M     1%      /dev
devshm        252M    0       252M     0%      /dev/shm
lrm            252M    19M     234M     8%      /lib/modules/2.16.15-26-386/volatile
/dev/hda1     7.7G    1.3G    6.1G     17%     /home/raavea/everything
```
To make things clearer, I have two hds, one with ubuntu on it (20G) and one for all my documents, music, and other crap (7G) called 'everything'. It looks like there's plenty of room, so what could the error be?

---

### Post by Raavea on 2006-08-25
.......o.o I guess I'll reboot and see if I can catch the error message long enough to write it down.


EDIT: Whoaly. *blinkblink*
 I rebooted and got a NEW error. And it wouldn't let me do anything but turn off or run fsck without the - stuff. So I did. I guessed at it all, but this time I didn't get GNOME! At least I got as far as logging in. It gave me an error;
 > I could not start your session and so I have started the failsafe xterm session. Windows now have focus only if you have your cursor above them. To get out of this mode type 'exit' in the window in the upper left hand corner.
 So I exited and tried logging back in, this time expressly selecting 'GNOME' as my session. Same error. Luckily typing 'firefox' into the window worked.

..Why is my hard-drive making *thinking* noises? It doesn't usually when I'm typing in a form field...

 Aaaaanyhow. **_What do I do_** now~? 
I'm gonna zip back and make all those posts a bit more legible.


EDIT2: I managed to log in to the failsafe GNOME session. Which is good, because I couldn't figure out how to close pop-ups in the xterm session. -_-

Now I really need to know how to fix this! *worried*

Maybe I should just re-install Ubuntu....? But I'd rather not..

---

### Post by Raavea on 2006-08-26
Umm.... Seriously. I went to bed, and I still can't log into GNOME. Only into failsafe. Wtf is going on? Will someone please help me?

 I do love doing the whole re-install thing, but I'd rather learn something by fixing this, this time.


EDIT: Sorry. That sounded a little rude. I was stressed. It's been another day, and I was actually worried about turning the computer off last night in case it died again.

 I'm about *this* close to giving up on learning anything, and simply re-installing.

 I'll never give up [COLOR="Orange"]Ubuntu[/COLOR] though~! ^____^

---

### Post by tseliot on 2006-08-27
Try adding a new account (i.e. username):

1) Boot in RECOVERY MODE from the GRUB Menu almost as soon as you turn on your computer (it will take you to the command line).


2) Type:
```
addusr new_username
```

**NOTE: replace "new_username" with your new username (which must be different from the one you already have**

```
passwd new_username_password
```

**NOTE: replace "new_username_password" with the password for your new username**

3) Add your new username to the sudoers list (otherwise you won't be ablet o use sudo)

Type:
```
visudo
```

and look for these lines:
```
# User privilege specification
root    ALL=(ALL) ALL
```

Add your new username so as to make it look like this:

```
# User privilege specification
root    ALL=(ALL) ALL
**new_username ALL=(ALL) ALL**
```

**NOTE: replace "new_username" with your new username**

After you did that type: 
```
:wq
```

and press ENTER in order to save


4) Restart your computer. Type:
```
reboot
```

5) Boot Ubuntu as usual and log in using your new username

---

### Post by Raavea on 2006-08-27
It didn't work - I couldn't log into normal GNOME with the new username either.

 What now? And thanks for your reply!

---

### Post by Raavea on 2006-08-28
I guess I'll re-install then. When I get a break from all this work.. -_-

I hope my set up of having all my docs on a seperate drive works, as failsafe doesn't screen-print so I doubt it will write to CD.

---

