---
title: "Synaptic package manager broken??"
date: 2006-01-11
forum: Desktop Environments
---

### Post by Muskoka on 2006-01-11
Cant use Synaptic anymore. System-Administration-Synaptic Package Manager, box comes up asking for password, enter password, then nothing. Went into the System Monitor to see if it was running and there's nothing there for Synaptic. Used apt-get to uninstall and reinstall, still nothing. Used apt-get to d/l kpackage and it works fine. Also the Add Programs icon from the Applications menu is gone. These are related because when Synaptic quit I went to Applications, Add Programs, clicked on the icon and it dissapeared and never came back. System has been running fine for about 1 month, today was the first real problem. Set-up is pretty basic. Haven't changed my user profile, or changed any passwords. Other than this problem, the system is fine. I can live without it but was curious if anyone had any ideas. Did try booting up into i386 kernel instead of 686 but same thing. Also tried 686 recovery at boot up,nothing different.

Did try something: Alt-F2 (Run Application) typed in Synaptic and it gives me an error saying i need to run it as Root ?? Tried as per the post below but didn't change anything.

Maybe this helps:
root@ubuntu:~# synaptic

(synaptic:8662): Gtk-WARNING **: cannot open display:

---

### Post by newuser111 on 2006-01-11
in a terminal type sudo synaptic

see if it works

---

### Post by Muskoka on 2006-01-11
Thanks for the quick response but no go.

glen@ubuntu:~$ sudo synaptic
Password:"my password"
glen@ubuntu:~$

Nothing happens, the hard drive dosen't even try to load anything, system just sits there.

---

### Post by newuser111 on 2006-01-11
try this

sudo apt-get --purge remove synaptic

then

sudo apt-get update

sudo apt-get install synaptic

sudo apt-get clean

sudo update-menus

---

### Post by newuser111 on 2006-01-11
also running synaptic wont work from root account, do it from your user account with sudo

otherwise type xhost + before typing "su"

---

### Post by Muskoka on 2006-01-11
Tried what you suggested but didn't get past first command:

This is the exact cut and paste.

glen@ubuntu:~$ sudo apt-get --purge remove synaptic
Password:"my password"
glen@ubuntu:~$

Nothing happens, nothing uninstalls. It is still there, because after rebooting I can get the password prompt again when launching Synaptic and it dosent load.

---

### Post by newuser111 on 2006-01-11
try running them from the root account "su" since you have it enabled

it actually looks like you have a problem with your sudo permissions, otherwise sudo apt-get would be able to uninstall synaptic, so try using the root account

---

### Post by Muskoka on 2006-01-11
Was able to uninstall and reinstall as root but still wont run.

---

### Post by Thirsteh on 2006-01-11
Type:
ls /usr/local/bin/synaptic

If it exists, delete it. Don't see why it should though.

---

### Post by Muskoka on 2006-01-11
Thanks again for the quick responses but nothings working out.

Tried and got:

glen@ubuntu:~$ ls /usr/local/bin/synaptic
ls: /usr/local/bin/synaptic: No such file or directory
glen@ubuntu:~$

/usr/local/bin is empty

Newuser111 your onto something because anything that needs my password wont work, Login Screen Setup,Networking,Users and Groups, all these things fail to load.

---

### Post by hashimoto on 2006-01-11
Sounds like your username is not in the sudoers file. Open terminal, do "su" and then run "visudo". Add your username to the end of the file (after root) and give it same permissions that root has: ALL (ALL) etc (or something like that, look at the root permissions). Save and exit. Your username should now have sudo rights.

---

### Post by newuser111 on 2006-01-11
i agree with hashimoto, the sudoers file has probably been wrongly edited

in the mean time you can run sudo commands from the "su" root account by typing 

**xhost +** before typing "su" this will let you start programs from the root account

---

### Post by Muskoka on 2006-01-11
Finally problem solved....

Went into "Applications", "System Tools", "Run as different user", and was able to run Synaptic as root from there. So I figured this was a way to see my "glen" user seeing as I wasen't able to use the menu command "System", "Administration", "Users and Groups". Newuser111 was correct and got me thinking that something must be wrong with my permission/permission level. Went to "Run as different user" in the "Applications","System Tools" menu, typed in users-admin and guess what, I got in. From there I was able to see that my "glen"  user didnt have any privileges, checked all the boxes and now I'am back in business, everything normal again. How it got like that is beyond me, I've never done anything in the Users Groups. If someone has seen this before please let me know what I did or how it might have happened so I don't do whatever I did again.

Thanks to all for the help.... Glen

---

