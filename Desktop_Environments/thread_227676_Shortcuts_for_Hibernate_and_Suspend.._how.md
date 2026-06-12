---
title: "Shortcuts for Hibernate and Suspend.. how?"
date: 2006-08-02
forum: Desktop Environments
---

### Post by patrickfromspain on 2006-08-02
HI there!

I have been thinking that one of the last thinks that don't work with my laptop is the Fn+F3 and Fn+F keys. Those one are to make Suspend to ram and suspend to disk. As the Fn keys don't work with F3 and F4, I'll do it with Control.

The question is: how do I make shortcuts for that? I do now where I have to go in the gconf-editor, and I also now I can make hibernate setting the keys as <Control>F4 and setting sudo hibernate. How can I make sudo hibernate work without password?

Now, sleep or suspend to ram. I haven't figured out how to run that. Anyone? I just know there's some file called sleep.sh but I have no idea how to run it.

Thanks!

---

### Post by fourchannel on 2006-08-02
this sounds like a job for **Dah! Dun! Duh!** xbindkeys

I use xbindkeys to make firefox actually use the extra buttons on my mouse. This is the forum showing how to do it. But all you need to gleam from it is how to install xbindkeys and then how to add the control-F keys to do what you need.

oh and don't forget to add /usr/bin/xbindkeys to your System>Preferences>Sessions>Start at logon launcher to have it, um, start on logon. 

[http://ubuntuforums.org/showthread.php?t=97936](http://ubuntuforums.org/showthread.php?t=97936)

EDIT:

Sorry I kinda missed the other part of your post, I need to get to bed lol.

To use a program without using sudo, you need to set the "sticky bit" on an executable to have it retain the permissions of root, and let any one launch it with root privileges.
```
kev@Rei:~]$ ls -Flah /usr/local/bulldogdry/monitor
-rwsr-sr-x  1 root root 997K 2006-01-30 03:07 /usr/local/bulldogdry/monitor*
``` 
This is the file listing of my UPS software. I need it to have root permissions so it can do its job. Yet when the power goes out I don't want to take extra time typing in a password.

```
man chmod
```read the chmod manual pages and look for the sticky bit.

hope that helps, sorry if I'm a little disorganized with my post here, I'm going to bed now.

---

### Post by patrickfromspain on 2006-08-02
Thanx for answering :) But I'm afraid that your post doesn't suit my needs (It will at home, where I have an 8 button mouse, though). I don't want to install other stuff to do that. I already know where make the keybind in gconf-editor, but I don't know how to set up sudo hibernate so it doesn't ask for the password and I don't know how to make the computer go to sleep (suspend2ram) using the command line. Once I know these 2 things, all will be fine.

Thanx!

---

### Post by patrickfromspain on 2006-08-02
EDIT: I have tried, to make my computer sleep, to put in the command line sudo ./sleep.sh or sudo /etc/acpi/sleep.sh.. but nothing happens. It asks for the password and that's it.

---

### Post by fourchannel on 2006-08-02
Ok I think I told you wrong again last night... But I'm well rested now! anyways...
Linux permissions has a cool option to keep the privileges of the original users when executing a file. Its called the SetUID and SetGID bits.

lets say I have this program that I need root access to run.

-rwxr-xr-x 1 root root 1019948 2006-01-30 03:07 monitor

unfortunately I would need to do ```
sudo ./monitor
``` to get it to run. However I could set the SetUID and SetGID bits and then I wouldn't need to do sudo.

```
kev@Rei:/usr/local/bulldogdry]$ sudo chmod 6755 ./monitor
kev@Rei:/usr/local/bulldogdry]$ ls -l ./monitor
-rwsr-sr-x  1 root root 1019948 2006-01-30 03:07 monitor
kev@Rei:/usr/local/bulldogdry]$./monitor
``` notice the **x** has been replaced with an **s** for the user and group octals.

This way if I wanted to run the program without typing sudo, I can and it 1.) keeps me from taking root priviliges beyond the scope of the program and 2.) keeps me from being able to modify the original program

---

### Post by patrickfromspain on 2006-08-02
We'll I'm afraid that it's not only a permissions things. For example, I can launch hibernate script without sudo, but I will fail because it needs super user permisions, to shut down HDD's or whatever. Changing permissions won't help, I'm afraid.

I need to edit the sudoers file, but I don't know how.

Also, I need to know how to sleep, because sudo /etc/acpi/sleep.sh does nothing. Cd to the folder and then sudo ./sleep.sh does nothing. But sleep works, as I can make the computer sleep from the shutdown menu.

Thanx!!

---

### Post by patrickfromspain on 2006-08-02
EDIT: repeated

---

### Post by patrickfromspain on 2006-08-02
Ok, finally I figured out after coming casually to a thread about acpi and suspend no working.

The commands I wanted to run were sudo hibernate and sudo /etc/acpi/sleep.sh force (I think the force thing must go there because of gnome power manager). To run them with superuser preferences but without a password, I have edited my visudo file: sudo visudo and there I have added:

patrick ALL= NOPASSWD: /usr/sbin/hibernate
patrick ALL= NOPASSWD: /etc/acpi/sleep.sh force

save and exit.

Next, in gconf-editor, under metacity, in the keybinds I have added <Control>F3 to run sudo /etc/acpi/sleep.sh force and <Control>F4 to run sudo hibernate.

Works best now!!

---

### Post by fourchannel on 2006-08-02
cool. I actually could use that info, cause I never got hibernate to work from the command line. Thanks man.

---

### Post by patrickfromspain on 2006-08-02
If you want to use that info you'll have to install a suspend2 kernel XD

If not, you 'll have to use sudo /etc/acpi/hibernate.sh

---

### Post by Chouca on 2007-01-05
Thanks Patrick,

```
sudo /etc/acpi/sleep.sh force
```

This worked fine with my Dell Latitude, an easy solution!


Martin

---

### Post by thor918 on 2007-01-19
and if you only have apm availeble learn from this page :
[http://gentoo-wiki.com/HOWTO_Getting_APM_Suspend_to_Work](http://gentoo-wiki.com/HOWTO_Getting_APM_Suspend_to_Work)

To suspend (the real goal of this howto) 
# apm -s

---

