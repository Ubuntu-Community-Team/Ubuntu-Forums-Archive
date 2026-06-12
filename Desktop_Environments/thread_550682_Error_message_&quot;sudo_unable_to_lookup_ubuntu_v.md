---
title: "Error message: &quot;sudo: unable to lookup ubuntu via gethostbyname()&quot;"
date: 2007-09-14
forum: Desktop Environments
---

### Post by dnccnd on 2007-09-14
Hallo!

I have just made a major update of my system after 6 months without using it. As it happened before, a new version of ubuntu is now available in Grub when I boot, and therefore I have to change the Grub manu.lst file to make Windows my default system.

Unfortunaly the "sudo" command to open manu.lst doesn't work and I get the same message that I have seen in other threads:

sudo: unable to lookup ubuntu via gethostbyname()

As suggested in the other threads, I tried to boot with the recovery mode, this is the first time I do that. The system loads some files but then it stops and I get a line with "root@ubuntu:~$".

Is it normal? Shouldn't the recovery mode lead me to the same kind of interface of the normal boot"? What should I do? Can I solve the "sudo" problem from there?

Thanks for any help you might provide!

---

### Post by mcduck on 2007-09-14
Could you post the exact command you tried to open the menu.lst file?

Also, the recovery mode _is_ just a command-line interface with root access. There is no desktop, as you should never, ever, in any case, run a desktop as root.

---

### Post by dnccnd on 2007-09-14
This is the message that get in terminal:

mauro@ubuntu:~$ sudo gedit /boot/grub/menu.lst
sudo: unable to lookup ubuntu via gethostbyname()
mauro@ubuntu:~$

I get the same message in the recovery mode.

I read posts by people with similar problems, like this one:
[http://ubuntuforums.org/showthread.php?t=39395](http://ubuntuforums.org/showthread.php?t=39395)

But I am not able to work without a desktop! :-(
Should I follow the same instructions from the receovery mode?

By the way, why shouldn't onw run a desktop as root?

Thanks a lot!

---

### Post by mcduck on 2007-09-14
> **dnccnd said:**
> This is the message that get in terminal:

mauro@ubuntu:~$ sudo gedit /boot/grub/menu.lst
sudo: unable to lookup ubuntu via gethostbyname()
mauro@ubuntu:~$

I get the same message in the recovery mode.

I read posts by people with similar problems, like this one:
[http://ubuntuforums.org/showthread.php?t=39395](http://ubuntuforums.org/showthread.php?t=39395)

But I am not able to work without a desktop! :-(
Should I follow the same instructions from the receovery mode?

By the way, why shouldn't onw run a desktop as root?

Thanks a lot!
I'm not sure about the problem when running in a terminal while logged into desktop. Try using gksudo instead of sudo, you should always use gksudo with graphical apps anyway.

If you try to fix it in recovery mode you can's use gedit (as it's a GUI application. And you don't need to use sduo in recovery mode since you are already root. just run 'nano /boot/grub/menu.lst' to edit the file with a simple text-based editor.

The reason why you should not run desktop as root is that the main reason that makes Linux secure is it's strict user permission control. You only give programs and users the permissions they need to do their task, nothing more. But if you log into desktop as root every single program you run, including the desktop itself, would run as root and have full power to do anything in your system. This is pretty much as insecure as running Windows as Administrator all the time. Security problem in any program, no matter what the program is, could compromise security of your whole system.

If you need to access system files with a graphical tool, just run 'gksudo nautilus' to open the file manager as root. And be sure to close it again as soon as you don't need it any more.

---

### Post by dnccnd on 2007-09-14
OK, here I need a whole procedure because I don't even know how to reboot or turn off the pc without a desktop! I followed the instructions contained in the link I provided in my previous reply, but I get something strange with only a line saying that some kind of text should be included on this page. There is nothing like 127.0.0.1 and so on. There some commands on the bottom of the page such as ^R and ^S but I really don't know how to use these commands! I think I have a big problem with the sudo thing here!

Now, to change the menu.lst file, when I am in the recovery mode I type nano /boot/grub/menu.lst aa you suggested, then I should get a text that I can edit. How do I save the file, exit the file and reboot?

Thanks again!

---

### Post by dnccnd on 2007-09-14
Now it is getting even worse!
I cannot access my ubuntu partition from Windows anymore!!! :-(

What happened?

---

### Post by mcduck on 2007-09-14
> **dnccnd said:**
> OK, here I need a whole procedure because I don't even know how to reboot or turn off the pc without a desktop! I followed the instructions contained in the link I provided in my previous reply, but I get something strange with only a line saying that some kind of text should be included on this page. There is nothing like 127.0.0.1 and so on. There some commands on the bottom of the page such as ^R and ^S but I really don't know how to use these commands! I think I have a big problem with the sudo thing here!

Now, to change the menu.lst file, when I am in the recovery mode I type nano /boot/grub/menu.lst aa you suggested, then I should get a text that I can edit. How do I save the file, exit the file and reboot?

Thanks again!
The commands marked like ^R mean that you should press Ctrl-R.

To save & exit in nano press Ctrl-X, it will ask if you wish to save the changes, press y, and then it'll ask where to save, press Enter to save to the original file.

If the file you opened didn't have the text it should have, first check that you didn't mistype the name of the file. Then, if the file was indeed right one you should add all the text that should be in the file. It might be a good idea to create a backup of the file before doing that, though. Yopu can do that with "mv yourfile yourfile.backup" (replace 'yourfile' with the actual file name, and also add 'sduo to the beginnng of the command unless you are in the recovery mode).

---

### Post by dnccnd on 2007-09-14
Great! It worked! Thanks a lot!!!
I had to write the content of the file from skratch but now I can use sudo.

The problem though is that I have been haivng problems with my LAN connection, I haven't been able to go online for a while. I worked a bit around with the networking settings but the internet connection simply doesn't work.

Now, after this last change, when I try to open the network options I get this message:

The configuration could not be loaded.
There was an error running the backend script.

Can you help me also on this one?

---

### Post by mcduck on 2007-09-14
> **dnccnd said:**
> Great! It worked! Thanks a lot!!!
I had to write the content of the file from skratch but now I can use sudo.

The problem though is that I have been haivng problems with my LAN connection, I haven't been able to go online for a while. I worked a bit around with the networking settings but the internet connection simply doesn't work.

Now, after this last change, when I try to open the network options I get this message:

The configuration could not be loaded.
There was an error running the backend script.

Can you help me also on this one?

Networking isn't really my strongest point, I just set the information I needed in Network Manager and it worked.. But since the error message you got doesn't really tell much about what the error is you could start by looking at /var/log/syslog, there might be a bit more information what the actual error is. Also, could you post here what you have in the /etc/hosts file now? I suppose if the file was empty it might have caused your networking problems, and the first thing to do would be to check that it now has all needed information..

edit: for reference, my /etc/hosts contains following information:
```
127.0.0.1 localhost Hyperion
127.0.1.1 Hyperion

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

---

### Post by dnccnd on 2007-09-14
Ok, now the network setting window opens, but the connection is still not working.
I looked at the syslog file, but it is a huge file and I don't understand anything in it!

My hosts file is similar to yours, the difference is only at the beginning, there is just one line with the 127.0.0.1 and it's like this:
127.0.0.1 localhost.localdomain localhost ubuntu

I changed it like in yours and like another example I found, in either cases sudo works but the internet connection doesn't.

I have found this post by the same guy as before:
[http://ubuntuforums.org/showthread.php?t=386309&highlight=johnbl](http://ubuntuforums.org/showthread.php?t=386309&highlight=johnbl)

He mentions that &#8220;Both /etc/hostname and /etc/hosts need to use the same name&#8221; for sudo and the network to work. In my "hostname" there is only the text "ubuntu", should I change it with the same text of the "hosts" file? What is in your hostname file?

I think that I have either a problem with my internet connection (but the same connection works in Windows) or I have to post a new thread only on my networking problem.

Thanks for your help!

---

### Post by mcduck on 2007-09-19
Sorry, my laptop had a hard drive failure last Friday, I don't have access to any Ubuntu machine until I get it back so I can't check what the hostname file should have. But if I remember right it should contain just the name of the computer, nothing else.

---

### Post by dcstar on 2007-09-20
> **dnccnd said:**
> 
......
He mentions that &#8220;Both /etc/hostname and /etc/hosts need to use the same name&#8221; for sudo and the network to work. In my "hostname" there is only the text "ubuntu", should I change it with the same text of the "hosts" file? What is in your hostname file?
!

My /etc/hostname contents:

** dc-desktop**

My /etc/hosts (part) contents:

127.0.0.1 localhost **dc-desktop** dc-desktop.tigerslair.tk
127.0.1.1 dc-desktop.tigerslair.tk

So yes, they should match (edit your "hostname" file!).

These commands should work when you get it set up correctly:

hostname
hostname -a

---

