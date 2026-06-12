---
title: "Login Issues with 9.04"
date: 2009-05-05
forum: General Help
---

### Post by dgerwin11 on 2009-05-05
At the risk of being reprimanded for starting a new thread for an old problem, I still am getting
"no exec ine in the session file xfce4.
running the GNOME fail safe session instead."

I have tried to follow the suggestions offered, but get no where.

After getting into $HOME/.dmrc, I can make the changes but nothing happens.  After making the changes, I hit enter on the keyboard, but nothing happens.

Other people seem to follow the same advice and get the desired results.  My conclusion is that I am goofing up a step somewhere, but for the life of me I can't figure it out.  On the other thread I have stated this, but get no responses.

Can anyone help me, please?

---

### Post by tommcd on 2009-05-05
> **dgerwin11 said:**
> 
After getting into $HOME/.dmrc, I can make the changes but nothing happens.  After making the changes, I hit enter on the keyboard, but nothing happens.

What changes to you make to .dmrc? A quick google search reveals that you need to change xfce4 to xfce like this:
[http://mondotech.blogspot.com/2009/04/no-exec-line-in-session-file-xfce4.html](http://mondotech.blogspot.com/2009/04/no-exec-line-in-session-file-xfce4.html)
How did you edit the file, and what changes did you make to the file? Post the output of:
```
less ~/.dmrc
```
If editing .dmrc does not not fix it, there are 2 other possible fixes listed in this bug report:
[https://bugs.launchpad.net/ubuntu/+source/xfce4-utils/+bug/354204](https://bugs.launchpad.net/ubuntu/+source/xfce4-utils/+bug/354204)

---

### Post by dgerwin11 on 2009-05-05
I made the change from Session=xfce4 to Session=xfce.  At that point I hit "enter" on my keyboard bu nothing happens
[Desktop]
Session=xfce4

---

### Post by dgerwin11 on 2009-05-05
I tried the link you mentioned, but got (and I paraphrase here) bash no command found
The solutions on launchpad work for eveyone but me.

---

### Post by tommcd on 2009-05-05
> **dgerwin11 said:**
> I made the change from Session=xfce4 to Session=xfce.  At that point I hit "enter" on my keyboard bu nothing happens
[Desktop]
Session=xfce4
Did you save the file so the changes persist? What text editor did you use and how did you save the file? Just hitting enter will not save a file in any text editor I know of. 
> 
[Desktop]
Session=xfce4

Is that the entire file, and do the changes persist after a reboot?

---

### Post by tommcd on 2009-05-05
> **dgerwin11 said:**
> I tried the link you mentioned, but got (and I paraphrase here) bash no command found
The solutions on launchpad work for eveyone but me.
What did you do *exactly*? Can you post the command you used and the output from it? Please describe exactly what you are doing so I can at least be sure you are editing the files and running commands properly. This could be why it is not working for you.

---

### Post by dgerwin11 on 2009-05-06
I have tried nano and vim.  How do you save a file with a text editor?  I tried rebooting with the terminal still open with "xfce" replacing "xfce4".  yes that is the entire file, and no the changes do not persist.  It keeps going back to "xfce4"

---

### Post by mondo1287 on 2009-05-07
In nano hit ctrl-x to exit, it will ask if you want to save the file.

---

### Post by dgerwin11 on 2009-05-07
Thanks for the attempt to help.  I entered "sudo nano $HOME/.dmrc" into terminal + password.  "[Desktop]
Session=xfce4" appeared.  I arrowed down and deleted second line and retyped "Session=xfce". ctrl x and then y to save.  I then rebooted and the machine came back up with the original "No exec line in session...."  I retried it without closing terminal and with closing terminal.  Alas no go.

I am thinking my best option is to email my files to my gmail account, and reinstall Xubuntu 8.10 from the disk I made 6 months ago.

---

