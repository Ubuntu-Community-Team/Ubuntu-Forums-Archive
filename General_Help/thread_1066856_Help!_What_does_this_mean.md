---
title: "Help! What does this mean??"
date: 2009-02-11
forum: General Help
---

### Post by 3pinner on 2009-02-11
Ubuntu Intrepid
I just downoaded latest updates (Feb 11 2009), logged out, then logged back in and got this message:

Users $HOME/.dmrc file is being ignored.
This prevents the default session and language from being saved.
File should be owned by user and have 644 permissions.
Users $HOME directory must be owned by user and not writable by others.

So what is this and how do I fix it??

Thanks!

---

### Post by soxs on 2009-02-11
$HOME/.dmrc has wrong permissions

just do as it says and do this from a shell:

```
sudo chown -vf $USER $HOME
sudo chmod -vf 755 $HOME
sudo chmod -vf 644 $HOME/.dmrc
```This should fix both errors..

Edit: If it still keeps complaining or some programs don't work replace -vf with -Rvf (for command one and 2)
EDIT: Fixed $user to $USER

---

### Post by 3pinner on 2009-02-11
> **soxs said:**
> $HOME/.dmrc has wrong permissions

just do as it says and do this from a shell:

```
sudo chown -vf $user $HOME
sudo chmod -vf755 $HOME
sudo chmod -vf 644 $HOME/.dmrc
```This should fix both errors..

Thank you soxs!
Any idea what might have caused this??

---

### Post by soxs on 2009-02-11
chmoding accidently your home dir, happens from time to time, or a random hicup of ubuntu... happend both to me before, no big deal...

---

### Post by 3pinner on 2009-02-11
Thank you, I'll give it a shot and post back in a minute.

---

### Post by 3pinner on 2009-02-11
OK so this is what I get when I type in the first line:

anyname@frodo-desktop:~$ sudo chown -vf $anyname $HOME
[sudo] password for anyname: 
chown: missing operand after `/home/anyname'
Try `chown --help' for more information.

---

### Post by 3pinner on 2009-02-11
> **3pinner said:**
> OK so this is what I get when I type in the first line:

anyname@frodo-desktop:~$ sudo chown -vf $anyname $HOME
[sudo] password for anyname: 
chown: missing operand after `/home/anyname'
Try `chown --help' for more information.

so what did I do wrong?

---

### Post by 3pinner on 2009-02-11
What operand should I be using?

---

### Post by 3pinner on 2009-02-11
Sorry, but I still need help with this!
Thanks!

---

### Post by soxs on 2009-02-11
sry, my fault $user must be $USER

---

### Post by 3pinner on 2009-02-11
hello,
I got through the first two commands, and when I tried the third, I got an error message.  The /.dmrc file could not be accessed. permissions denied.
At that point, I lost m desktop background, and I could not get the reply to thread page in my browser. Something really wrong here.
So I restarted the computer.
The log in appears, I type in my username and password, and then only have a cursor arrow.
then I get the two following error messages:

  Could not update ICEauthority filr /home/anyname/.ICEauthority

  There is a problem with the configuration server 9/usr/lib/libeconf2-4/gonf-sanity-check-2 exited with status 256) :confused: :confused:

---

### Post by bodhi.zazen on 2009-02-11
Really nice guide on this issue [here](http://ubuntuforums.org/showthread.php?t=976610)

---

### Post by 3pinner on 2009-02-11
thank you!
But I cannot log on to that account to follow the instructions  due to the last two error messages I posted.
1)  I have another account with administratior priviledges, can I do this from that account?
2)  If not, how do I correct the two other error messages in the previous post?
Thanks!

---

### Post by bodhi.zazen on 2009-02-11
What did you do to cause these problems ?

Were you running applications as root ? did you move your home directory ? did you enter a command ?

most of these errors stem from ownership / permissions errors in your home directory.

so you need to boot to say recovery mode and look at the permissions.

ls -la /home/anyname

---

### Post by 3pinner on 2009-02-11
hat did you do to cause these problems ?

Were you running applications as root ? No
 did you move your home directory ?  No
did you enter a command ? Yes,
I followed instructions from  a previous reply and in terminal:

suco chown -vf $USER $HOME
sudo chmod -vf 755 $HOME

These 2 commands worked fine

The last did not>
sudo chmod -vf 644 $HOME /.dmrc

I got an error message that .dmrc was not accessible - permissions denied 

When I logged off and logged back on, I got the other 2 error messages.

When I check the account permissions as you suggested, the first line (which I assume is my overall account permissions):

drw-r--r-- 87 anyname anyname   4096 2009-02-11 18:09 .

---

### Post by 3pinner on 2009-02-11
THANK YOU!
I followed the tutorial and everything is fine so far.

I have no idea how I could have caused this, it just started happening right after I installed the latest update. anyway, I learned something, and that's why I come here!

---

### Post by bodhi.zazen on 2009-02-11
Awesome, glad it is solved.

Thanks goes to the author of the tutorial , who I see is a member of the Beginners Team as well :twisted:

---

