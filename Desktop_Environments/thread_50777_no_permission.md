---
title: "no permission??"
date: 2005-07-21
forum: Desktop Environments
---

### Post by Sander50 on 2005-07-21
I'm a newbie to linux, but I wanted to try. so i installed ubuntu (not very difficult), and now it works fine.

I installed Apache2 after that - just to test some php-script -. Now i wanted to delete the directory "apache_default" or something, but it says "i have no permission" to delete it. There are more dirs I can't just edit... I have only one user!
how can i fix that??

Sander(50)

---

### Post by dave9191 on 2005-07-21
You dont have permission because you are not the owner of those files or the admin of the computer. Under ubuntu the root account is not setup by deafult and you use sudo instead. You can do this in the command line by putting "sudo" before every command and enetering YOUR PASSWORD. Or you can launch a graphics file browser as root. Instructions to do that are on these forums as Im sure in other places. 

Dave

---

### Post by musicman2059 on 2005-07-21
Simple fix for that:

```

sudo chown /path/to/file yourusername

```

Or was it sudo chown yourusername /path/to/file?  Either way, one of those would work, or just check chown --help.

---

### Post by kafton on 2005-07-21
> sudo rm /path/to/file


sudo gives you root privileges.

---

### Post by dave9191 on 2005-07-21
sudo chown YOUR_USER_NAME:YOUR_USER_GROUP /path/to/file

Thats the correct format for the command.

sudo rm /path/to/file 

will remove the file in question.

---

### Post by Sander50 on 2005-07-21
It works. Thanks!

but can't i login as root or something? or is that a stupid question...

---

### Post by musicman2059 on 2005-07-21
The root account in Ubuntu is technically disabled, but there are workarounds:

1. Using the root terminal under the System Tools menu, or

2. Starting up in recovery mode.

Of course, prolonged use of the root account is **NOT** recommended as you can do some very significant damage to your system.

---

### Post by dave9191 on 2005-07-21
And by default logining in with root at the login screen is disabled. Tho you can change that and login as the root user to make changes to your system, it is **hightly not recommened** unless you know exacly what you are doing. Not running as root is a security measure not to mess up the computer and protect your system. 

Dave

---

### Post by Sander50 on 2005-07-22
ok, thanks all! 

now i've already another question :smile: 
i dont have an internet connection on my ubuntu computer. So, i downloaded (on another computer) gtoaster, and tried to install it (commando *./configure* or something). the computer starts with configuring, but then i get the following error:
```

[i]*** The gtk-config script installed by GTK could not be found,
*** If GTK was installed in PREFIX, make sure PREFIX/bin is in
*** full path to gtk-config.
configure : error : cannot find Gtk+[/i] 
```

I checked, GTK is installed on my computer... 

when trying to install another package (gdesklets) i get the another error:
```
*configure: error: XML ::Parser perl module is required for intltool.*
```
And I checked (again): Perl and XML are installed. 

What are these errors, and how can I install those programs?

Sander

---

### Post by dave9191 on 2005-07-22
The ./configure is the first part of compiling a program. In order to compile a program you need to have all the development libaries installed on your comptuer. These are not there by default. You have gtk, but you dont have gtk-dev. It would be a lot better if you could download the precompiled version or a package. Prefably a .deb file that can be installed with the "sudo dpkg -i package_name" command. 

Dave

---

### Post by Sander50 on 2005-07-29
thanks guys! i now know how to install some programs, they work fine.

But i have another question... I installed [NetworkManager](http://people.redhat.com/dcbw/NetworkManager/)  on my computer (it is installed succesfull), but how can I start the program now? There are no icons for it in *Applications* or somewhere else...

Sander(50)

---

