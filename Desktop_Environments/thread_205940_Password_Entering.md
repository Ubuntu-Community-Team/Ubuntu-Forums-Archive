---
title: "Password Entering"
date: 2006-06-29
forum: Desktop Environments
---

### Post by TomAnthony on 2006-06-29
I was wondering if there is a way to not have to enter a password every time I run an administration app? I do understand that this is less secure, but no one else uses my computer, and I don't do anything I don't fully understand anyway.

---

### Post by jgcamp99 on 2006-06-29
Re-enable root:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Make sure you allow gnome or KDE to allow root to log in graphically.

Step 1:

Enabling the root account
To enable the root account (i.e. set a password) use: 

sudo passwd root
Enter your existing password
Enter password for root
Confirm password for root 

Step 2:

Enabling graphical root login

In Gnome:
Open System --> Administration --> Login Screen Setup 

Click on the security tab 

Check Allow root login 

In KDE:
Open Konqueror and open the /etc/kde3/kdm/ folder 

Right click the kdmrc file and then Actions --> 'Edit as root' 

On line 246 should be AllowRootLogin=false change it to 'true' 

Save and exit. 

From the Linux Console:
Switch to a virtual terminal with Ctrl+Alt+F1 (or F2, F3, ..., F6). You can get back to your X session with Ctrl+Alt+F7. 

Log in as yourself. 

Become root with "sudo -i". 

Start a new X server on display :1 with "startx -- :1". 

You can run a different window manager (say, fvwm) with something like "startx fvwm -- :1". 

You must use display :1 because the default (display :0) is already being used by you. 

Be careful, you're the superuser. Don't forget to logout as soon as you're done, from both X and the console.

---

### Post by jgcamp99 on 2006-06-29
Oh, btw, if you mean have the root be the automatic login, I think you might have to try that with the autologin and instead of the ubuntu user account, indicate it as root. I think I read somewhere that autologin works with any user except root though, I may be right or wrong on this.

---

### Post by lamego on 2006-06-29
The security issue is not about yourself doing insecure commands or other people using your computer, linux is not less prune to virus/spyware unless you follow security rules like those. If your user gets by default full system privileges you will be vulnerable to any linux compatible malware that may appear and which you maybe tricked to run.

---

