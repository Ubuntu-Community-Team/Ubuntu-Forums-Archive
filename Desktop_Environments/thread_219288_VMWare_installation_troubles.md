---
title: "VMWare installation troubles"
date: 2006-07-19
forum: Desktop Environments
---

### Post by Cataliste on 2006-07-19
Hello.

I am currently having a problem installing VMWare. >_>

I have properly chmod a+x the install script.  And I have PERL on my computer.

Now, when I try to install it via the Konsole I execute the file as "sudo".

It lets me chose the directories and what-not, but as soon as it tries to move any files, in this case "services.sh" it says it does not have proper permisions to the directory.  I am using all the default directories.

Has anyone else had this problem?  Solutions?

Thanks

~Cata~

---

### Post by Kurt` on 2006-07-19
Which guide are you following?

[http://www.ubuntuforums.org/showthread.php?t=183209](http://www.ubuntuforums.org/showthread.php?t=183209)

---

### Post by Cataliste on 2006-07-20
```

spinnerz@TEHSCION:~$ sudo '/home/spinnerz/burn/vmware-distrib/vmware-install.pl'
Creating a new installer database using the tar3 format.

Installing the content of the package.

In which directory do you want to install the binary files?
[/usr/bin]

What is the directory that contains the init directories (rc0.d/ to rc6.d/)?
[/etc]

What is the directory that contains the init scripts?
[/etc/init.d]

The file /etc/init.d/vmware that this program was about to install already
exists. Overwrite? [yes] yes

Unable to copy the source file ./installer/services.sh to the destination file
/etc/init.d/vmware.

Execution aborted.

```

^^^^That is my Konsole output.  Also, I have downloaded the kernel headers for my Kubuntu.

I also followed that guide to the T, and I still have the same error.  :(

---

### Post by Kurt` on 2006-07-20
Can you try

# sudo rm /etc/init.d/vmware

and run it again?

That's odd that a script run as root can't copy a file...

---

### Post by Cataliste on 2006-07-20
```

spinnerz@TEHSCION:~$ sudo '/home/spinnerz/burn/vmware-distrib/vmware-install.pl'
Creating a new installer database using the tar3 format.

Installing the content of the package.

In which directory do you want to install the binary files?
[/usr/bin]

What is the directory that contains the init directories (rc0.d/ to rc6.d/)?
[/etc]

What is the directory that contains the init scripts?
[/etc/init.d]

Unable to copy the source file ./installer/services.sh to the destination file
/etc/init.d/vmware.

Execution aborted.

```

Same error.  :S

I do not know what to do...

---

### Post by xxdd on 2006-08-07
i had the same problem, i did cd into the exact directory the install script was in and then executed it,

hope this helps

dave

---

### Post by shea on 2006-08-09
I am having the exact same problems that you are. I have installed Ubuntu Desktop x64 6.06. It is a clean installation and then i followed these steps. 
1. Install the nvidia-glx package and configure xorg.conf
2. run the auto package updater and install any patches/security fixes. Reboot
3. Install gcc and apache2 packages. reboot
4. download and install the newest version of VMware Server. Untar. 
5. In a terminal i run the following commands

shea@ultra20:~$ sudo -s
Password:
root@ultra20:~# /home/shea/Desktop/vmware-server-distrib/vmware-install.pl
Creating a new installer database using the tar3 format.

Installing the content of the package.

In which directory do you want to install the binary files?
[/usr/bin]

What is the directory that contains the init directories (rc0.d/ to rc6.d/)?
[/etc]

What is the directory that contains the init scripts?
[/etc/init.d]

Unable to copy the source file ./installer/services.sh to the destination file
/etc/init.d/vmware.

Execution aborted.

root@ultra20:~# cd /home/shea/Desktop/vmware-server-distrib/
root@ultra20:~/Desktop/vmware-server-distrib# ./vmware-install.pl
A previous installation of VMware software has been detected.

Failure

Execution aborted.



Any help would be much appreciated. 
Shea Lutton

---

### Post by shea on 2006-08-09
Ah Ha! I found this guide here: [http://howtoforge.com/ubuntu_vmware_server](http://howtoforge.com/ubuntu_vmware_server) and I was able to get it working. The article is good but there is one thing that has changed since it was written. There is one comment at the very bottom that included instructions to install one more package. By following the article and reading the comments I was able to get it working. 

Shame on VMware for not including more documentation. 
Shea

---

