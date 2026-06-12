---
title: "Boot Up Error Message"
date: 2008-11-27
forum: Desktop Environments
---

### Post by bear54 on 2008-11-27
:confused:**Boot Up Error Message**
When booting up after typing in user name and password I get the following error message...

**"User's $HOME/.dmrc is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users."**

I began getting this error message after trying to change permissions on an external hard drive. How can I fix this? Any help will be greatly appreciated.
Eric:cool:

---

### Post by PmDematagoda on 2008-11-27
Regardless of this error, are you able to start the GNOME session properly? If so, post the output of:-
```
ls -la ~
```
otherwise, boot Ubuntu in Recovery Mode, drop to a terminal, run:-
```
startx
```
and open a terminal from there and post the output of that command on your home directory, where it would look like:-
```
ls -la /home/username/
```

---

### Post by binbash on 2008-11-27
[http://ubuntuforums.org/showthread.php?t=974072&highlight=dmrc](http://ubuntuforums.org/showthread.php?t=974072&highlight=dmrc)

---

### Post by bear54 on 2008-11-27
Thank You all for the info I will give it a try and see if I can solve this error message. This problem is only annoying my computer boots and runs fine.
Thanks Eric

---

### Post by bear54 on 2008-11-27
I have a major problem I did the following...

[B]chmod 755 $HOME
chmod 644 $HOME/.dmrc[/B]

as root now I can't boot up as user. I can login as root but I have no access to my folders or my back-up internal hard drive. At this point I would like to access my folders and back-up drive so that I can do a back-up. I do back-ups about once a week but it's been almost a week so will lose a lot of data if can't do a new back-up and have access to my back-up drive. I tried booting up in restore and tried to repair corrupt folders but did not work. I am logged in as root in in text mod now and tried to login as user but get message that there are no files.
  Any help would be greatly appreciated.
    Eric

---

### Post by PmDematagoda on 2008-11-28
Can you post the output of:-
```
ls -la /home/username/
```
where username is the username you use.

---

### Post by bear54 on 2008-11-28
This is what I got when I typed in the command...

[B]ls -la /home/eric

ls: cannot access /home/eric: No such file or directory[/B]

Eric

---

### Post by PmDematagoda on 2008-11-28
Can you post the output of:-
```
ls -la /home/username/
```
where username is the username you use.

---

### Post by PmDematagoda on 2008-11-28
Can you post the output of:-
```
ls -la /home/username/
```
where username is the username you use.

---

### Post by bear54 on 2008-11-28
This is what I got...

[B]ubuntu@ubuntu:/media$ ls -la /home/username/
ls: cannot access /home/username/: No such file or directory
ubuntu@ubuntu:/media$ 
[/B]

I also tried my home directory /home/eric with the same result.

Eric

---

### Post by bear54 on 2008-11-28
I am useing a live Ubuntu 8.04 CD to try to access my internal drives. One drive has Windows XP and Ubuntu 8.04 the other drive is used as a back-up and is formatted as ext3. Since I tried to repair the error message I was getting at start up I have no access to any drives and machine will not boot Ubuntu. I just wanted clarify my situation.
  Eric

---

### Post by PmDematagoda on 2008-11-28
What error do you receive when trying to boot Ubuntu?

---

### Post by bear54 on 2008-11-29
When the problem first occurred I got this error message...

**"Your session only lasted less than 10 seconds. If you have not logged yourself out, this could mean that there is some installation problem or that you may be out of disk space. Try logging in with one of the failsafe sessions to see if you can fix the problem."**

I know that I have plenty of disk space so don't think that could be the problem. I just tried booting the computer up but could not attempt to log on as the video is now messed up. The picture is clear but too big for the screen. I may be able to log in in text mode but have not attempted that.

I am thinking that I could remove the main drive and make it external and connect it to a different computer and recover the data that way than reinstall in the computer and reinstall Ubuntu.
  Thank You for your help it is greatly appreciated.
    Eric

---

### Post by PmDematagoda on 2008-11-29
Boot Ubuntu in Recovery Mode, drop to a shell and then execute:-
```
chown *username* -R /home/*username*
```
where *username* is the username you use, not just username.

---

### Post by lelmo85 on 2008-11-29
If you can boot in text mode and get to terminal, try old standby sudo dmesg | less and sudo dmesg | tail. Might tell you something. (might not).



"Fools rush in where angels fear to tread"

---

### Post by bear54 on 2008-11-29
Thank You! Thank You! Success. I did as suggested and booted up in safe mode then text mode than typed in "**chown username -R /home/username**" worked. I was able to burn data to a DVD. There are problems but I haven't rebooted system yet to see final result. Data has been saved, my biggest concern.
  I will update after I reboot system to see if I can boot-up normally.
    Thank You!!!!
      Eric:)

---

### Post by bear54 on 2008-11-29
I have shut down computer and booted up again. I was not able to login I get the same error message as before. I have to shutdown by pushing power button on computer. When I boot up again I use **recovery mode** than **root shell** than I type **startx**  to get a graphical interface. I can see all my programs and home directory but I am logged in as root. User eric seems to be gone but when I type users in a shell my name comes up but I seem to have no privileges. Maybe there is a file I can edit in safe mode to fix this. Oh one other thing my internal back-up hard drive is not accessible.
  Eric :)

---

### Post by PmDematagoda on 2008-11-29
> **bear54 said:**
> I have shut down computer and booted up again. I was not able to login I get the same error message as before. I have to shutdown by pushing power button on computer. When I boot up again I use **recovery mode** than **root shell** than I type **startx**  to get a graphical interface. I can see all my programs and home directory but I am logged in as root. User eric seems to be gone but when I type users in a shell my name comes up but I seem to have no privileges. Maybe there is a file I can edit in safe mode to fix this. Oh one other thing my internal back-up hard drive is not accessible.
  Eric :)

Can you please post the output of the ls command I told you to post before? Perhaps we can try and figure out exactly what is wrong with the home directory.

---

### Post by bear54 on 2008-11-30
When I type in **"ls"** in a shell I get this...

**"Desktop Documents Music Pictures Public Templates Videos"**

I also tried the command **"ls -la ~"** the result is to long for me to type in here but a long list of directories was displayed with the word **root** at the beginning of each line.

When I try to view any system files I am denied access the message I get is that **I do not have permission** to view files. I thought this was odd as I am logged in as root. When I log out of root I am able to log eric in but he has no privileges.

Just an idea maybe I could make a new user who has all the normal privileges.
Eric

---

### Post by bear54 on 2008-12-03
After trying everything I could think of I went ahead and reinstalled Ubuntu 8.04. The most important mission was accomplished that was saving my data. I thank everyone for helping me do that. After the reinstall was complete I could access my back-up drives again. That made my day! One lesson that I learned from this is to back-up everyday or at least every time you add new data. You would think it would be obvious but it is easy to forget to do back-ups.
  Thanks Again
   Eric :D

**_Ubuntu_ is the BEST!!!!!**

---

