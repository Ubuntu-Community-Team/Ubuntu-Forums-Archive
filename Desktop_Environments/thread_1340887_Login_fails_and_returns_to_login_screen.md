---
title: "Login fails and returns to login screen"
date: 2009-11-29
forum: Desktop Environments
---

### Post by abhi.b on 2009-11-29
Hi,

When I boot my notebook and try to login, within a few seconds I am sent back to the login screen. I am using Ubuntu 9.10 on a Dell Vostro 1500, with Blubuntu.

The ~/.xsession.err (error file) contains a line "cannot find /home/my_user_name/.profile". So I logged in via command prompt, and set the permissions of .profile to "rwxr-xr-x" (I think the previous permissions were "rwxr--r--"). However, the problem still persists and I cannot login with the desktop screen.

It used to work before, and the problem started appearing after I did the following:
1. I was running Ubuntu 9.04, on which I never saw this issue.
2. Upgraded to 9.10 via Update Manager.
3. Changed theme from default to Blubuntu.
4. Made a few changes to panel - added a couple of launchers, workspace switcher etc.

Please let me know if anyone has suggestions to fix this.

Thanks,
-- Abhijit

---

### Post by BenAshton24 on 2009-11-29
is that the only error or are there more?

---

### Post by abhi.b on 2009-11-29
That is the only error.

---

### Post by abhi.b on 2009-11-29
I tried removing .profile from my home directory. 

After restarting and entering username/password, I get only a blank screen and it does not proceed further.

I checked the .xsession-errors: There is a line 'cant save user-dirs.dirs'.

Any suggestions? I have also removed blubuntu using apt-get remove blubuntu-look.

---

### Post by abhi.b on 2009-11-29
I could not figure out how to fix it. 

My workaround: I have installed KDE, and I can now login without any problems.

However, I was hoping to figure out the cause of the original problem, and fix it so that it does not occur again. Perhaps I will try installing Gnome again in the future.

Anyways, sometimes working with Linux means you have to spend a lot of time trying many different things :-) It is certainly worth the effort.

---

### Post by U2010 on 2010-02-21
Hi,

had the same problem last month. In my case, there have been two files  in my home directory with root:root ownership (.ICEauthority and  .nvidia-settings-rc). Just changed ownership and everything is back to  normal.

Hope this helps and greetings.

---

### Post by Buripak on 2011-01-13
Hi, I had the same problem after installation some actualizations for my Ubuntu. You are using nvidia kernel module I see, just reboot your Ubuntu and in GRUB select Recovery mode, then select "run terminal as root" and reinstall your nvidia kernel module for example:

[INDENT]# sh NVIDIA-Linux-x86-96.43.19-pkg1.run[/INDENT]

After reinstall log in and everything should be in order.

---

### Post by Talion86 on 2011-01-17
> **U2010 said:**
> i had the same problem last month. In my case,  there have been two files  in my home directory with root:root ownership  (.ICEauthority and  .nvidia-settings-rc). Just changed ownership and  everything is back to  normal.
I had the same problem, with the login screen repeating everytime I logged in. This solved my problem, thanks!

---

### Post by Jellow on 2012-03-05
> **U2010 said:**
> Hi,

had the same problem last month. In my case, there have been two files  in my home directory with root:root ownership (.ICEauthority and  .nvidia-settings-rc). Just changed ownership and everything is back to  normal.

Hope this helps and greetings.

How do you change ownership of files in your home directory if you can't login?

---

### Post by oldos2er on 2012-03-05
Please don't bump old threads. Stick with the one you created here: [http://ubuntuforums.org/showthread.php?t=1934755](http://ubuntuforums.org/showthread.php?t=1934755)

---

