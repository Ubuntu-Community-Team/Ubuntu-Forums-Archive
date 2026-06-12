---
title: "Permission Denied! Tar Extraction, File System"
date: 2012-12-09
forum: Desktop Environments
---

### Post by jbart0312 on 2012-12-09
Hey,

I was attempting to install Python 3.2.3 today, older versions called IDLE can be found as packages (I know). 

I downloaded the Tar ball. Now, How to extract and install properly on my file system is confusing to me. 

Archive manager likes it when I press extract but doesn't like it when I try to create a folder in /ect so I can put this where I want it.

I think that extracting this tar ball to the desktop is a bad idea.

Anyone out there want to throw some ideas my way to help me understand the darkness in my head. Thx.

---

### Post by TheFu on 2012-12-09
A tar file can be created with either relative paths or absolute paths. There is a place for both, but not when you download files from the internet. Then you only want relative paths to be used.  It is best to de-tar files into a temp area first, look through them for the permissions and only once you are satisfied, relocate the files to a more permanent location.

Historically, files that are loaded outside a package manager should be placed into /usr/local/ to keep it clearer in the administrators mind how they are installed and maintained.  /usr/local/etc/ would be my gut feeling for your tar files.

A normal user account cannot, and should not, be able to write to these directories. Elevated permissions are required. That means you probably need to use **sudo**.  **Archive manager** doesn't run with elevated permissions by default. I've never used it, I'm a CLI sorta-guy.  Chances are that you want to recursively copy the files from your temporary folder under your HOME into /usr/local/etc using root (sudo). Sometime like
**$ sudo cp -r ~/tmp-folder/top-tar-dir /usr/local**
is probably what you want.  Be certain to verify that your number account doesn't own anything after the copy. That could open security issues that you don't want or break the software.

---

### Post by NightsShadeQueen on 2012-12-09
I think you need root permissions to manipulate files in /etc

That said, I don't think you need to untar there. According to the README, you can untar anywhere and then just run a few of the scripts it includes with sudo and it should just work.

---

### Post by jbart0312 on 2012-12-09
> **NightsShadeQueen said:**
> I think you need root permissions to manipulate files in /etc

That said, I don't think you need to untar there. According to the README, you can untar anywhere and then just run a few of the scripts it includes with sudo and it should just work.

[PHP]On Unix, Linux, BSD, OSX, and Cygwin:

    ./configure
    make
    make test
    sudo make install

This will install Python as python3.[/PHP]What your saying is kind of what I gleamed from README.

After I extract the tar to a temp dir I should run these scripts from Terminal after performing; CD /home/.../temp/python/

Then Lubuntu will perform the scripts on whatever files are located only in that directory. I guess that is where my confusion might be.

Sorry, there are alot of things to learn in computers. That's why I posted to the forum. Googling the answer to this specific question was bringing me a lot of muddy admin proprietary explinations. I don't want to socialize my computer. I want to build it from the bottom up so that I can capitalize it. I guess that some will understand the last thing I just said while others just never will.

So, when some guys talk about admin privileges they are really talking about the different layers of abstraction within the Operating system itself?? SUDO changes the GUI or LXDE from, a user entering commands to them, to, a user entering commands to the kernal and file system itself??

---

### Post by TheFu on 2012-12-09
> **jbart0312 said:**
> So, when some guys talk about admin privileges they are really talking about the different layers of abstraction within the Operating system itself?? SUDO changes the GUI or LXDE from, a user entering commands to them, to, a user entering commands to the kernal and file system itself??

UNIX and Linux are multi-user operating systems. The idea that 2 or 500 or 50,000,000 users can share the same OS install has been part of the system architecture and design since the beginning. This is different from Microsoft and Apple computer designs over the years.  Multi-user was tacked onto Microsoft, but never really fully integrated until Windows Vista - I think many parts of the OS are still single user designed.

On UNIX systems, admin privileges almost always means using the "root" account.  sudo is a way to escalate from your normal user privilege level to "root" for a specific program.

File and process permissions are central to understanding UNIX and Linux security. If you are going to code web sites or web services, it is really, really, really important that you understand these ideas. An understanding beyond what can be explained in this forum is necessary if you don't want to have every web-app hacked.  

The concepts are not difficult, but there are many subtle ideas involved.  Many of these ideas and methods are why Linux and UNIX systems are considered much more secure than other OSes across the board.

---

### Post by jbart0312 on 2012-12-09
> **TheFu said:**
> 

The concepts are not difficult, but there are many subtle ideas involved.  Many of these ideas and methods are why Linux and UNIX systems are considered much more secure than other OS's across the board.


So, because of the way UNIX is designed to be multi-user then anyone can access the root directory quickly and start destroying stuff?

I remember reading somewhere that the multi-user capability of UNIX is what makes it so great as a preferred OS for WWW. servers.

So, there are very strong security measures right at the heart of UNIX, like what they call orthgonality and that is what helps the OS stay tidy without losing it's integrity?

It is very subtle, like you said, but very, very interesting and cool to learn. Thx MrFu

I will have the solution and post it SOLVED hopefully within the hour.

---

### Post by jbart0312 on 2012-12-09
:idea: So here is the **solution!**

[SIZE=3]How to properly download and extract a tar file in the directory of your choosing.[/SIZE]

Download tarball...

Open your terminal to access CLI:

Use **sudo mkdir** command to create a directory of your choice on your filesystem.

Use** cd** command to navigate to the directory containing your newly aquired compressed file: 

Use **sudo mv** command and relocate the tarball into the directory you have created for it.

It might look this way:

```

soandso@soandso-desktop: /home/soandso/downloads$ sudo mv python.tgz  /usr/python   
```Now hit enter.


Navigate to the new directory that now contains your tarball.

Use **sudo tar -zxvf**  [tarballsname.ext]

Your file will be extracted within the directory you put it.

What happens after that.? Lol! You might be coming back to Ubuntu Forums shortly! Ha! See ya. 

Thx to TheFu and NightsShadeQueen respectively.

---

### Post by TheFu on 2012-12-10
> **jbart0312 said:**
> So, because of the way UNIX is designed to be multi-user then anyone can access the root directory quickly and start destroying stuff?

No just any user, but only users that have been specifically provided with an escalation to root capability.  On a single user Linux system, then all users have access to sudo. After all, she/he installed the OS and requires root.  On a multiuser Linux system, only 1 or 2 people should have access with sudo to maintain the box, not everyone with an account.

UNIX/Linux OSes have the idea that only the minimal required permissions should be available to any account that is mandatory to do their jobs.  An average user account cannot harm anything on a properly configured UNIX/Linux system - the **Permission Denied** error that you originally saw demonstrates that aspect.  If you didn't have access to sudo (or the /etc/sudoers file didn't include your userid/group inside it), then you wouldn't have been able to write anything below /etc or /usr at all.

There are methods to get around some of this, mainly by using a liveCD and booting off it, but that same attack works with any OS. If physical access to the machine is available, it is extremely hard to fully secure the OS regardless of which OS it is.  The best way that I know to slow down any crackers is to encrypt the OS.  But I digress.

I'm glad that you found a solution that works.  Perhaps I should have just said.
**$ cd / ; sudo tar zxvf some-file.tar.gz **
since that was probably all you really wanted to know instead of writing about security and subtle security methods?  OTOH, that command may have been dangerous to your system.

---

