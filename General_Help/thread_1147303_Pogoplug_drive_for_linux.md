---
title: "Pogoplug drive for linux"
date: 2009-05-03
forum: General Help
---

### Post by Ptah on 2009-05-03
Hello everyone, I hope someone can help me with this.  What this product does is create a networked drive that you can access via web or by local drive.  I can not figure out how to mount this drive using the command instructions they give.  Below is the command:

pogoplugfs --user [email]test@cloudenginges.com[/email] --password test --mountpoint /mnt/fuse

Here is the link to the product it is pretty cool! [http://www.pogoplug.com/](http://www.pogoplug.com/)

---

### Post by perryrt on 2009-05-12
Well, I just installed mine tonight, and keep in mind I'm so very NOT a *nix god....

But this is what I figured out already.

Once you download the file from the pogoplug site, extract it to your home directory. This puts a file called "pogoplugfs" in your home directory.

Open a terminal window, and try the following phrase:
```
perryrt@dell-desktop:~$ ./pogoplugfs --help
```

If it works, you should get a listing of possible options (and it means the command is working, obviously.)

Mine looked like this:

```
Usage:
  pogoplugfs [options]

Where options include
  --help           Displays this page
  --version        Displays full version and exits
  --ver            Displays numeric version and exits
  --builddate      Displays date and time of build and exits
  --compiler       Displays compiler used for build and exits
  --valtoken <v>   Specifies a validation token <v> used to authenticate
  --user <u>       Specifies the user to authenticate as
  --password <p>   Specifies the password to authenticate with
  --device <d>     Specifies the device ID to use for the mount point
  --service <s>    Specifies the service ID to use for the mount point
  --mountpoint <m> Specifies the full path on the local machine at
                   which to mount the virtual drive
  --fuseopts <f>   Specifies a comma delited set of fuse options
  --notrashes      Don't allow .Trashes in root

Linux builds require at least --mountpoint as well as either --valtoken
or --user and --password to be specified

Additionally, options can be read from a configruation file that is in
one of the following locations:
   <PWD>/pogoplugfs.conf
   ~/.pogoplugfs.conf
   /etc/pogoplugfs.conf
Configuration files are of the form:
   <key>=<value>
And keys supported include:
   svcuser         User to authenticate as if not specified on command line
   svcpassword     User password to authenticate with if not specified
   logseverity     Maximum log level that will be output to the log (integer>


```


More later when I figure it out.

---

### Post by perryrt on 2009-05-12
OK, additional info.

To mount the drive, first you need to create a mount point (i.e. where in the file system it "fits".)

I chose /media/pogoplug, since most of what will be on this drive is various media files. The original pogoplug example uses /mnt/fuse - I don't think it makes a difference, really. Anyway, to set that directory up, type "sudo mkdir /media/pogoplug" from the terminal. 

Then you can start the drive using:

```

./pogoplugfs --user test@cloudenginges.com --password test --mountpoint /media/pogoplug

```

....where **/media/pogoplug** is your mount point, **test@cloudengines.com** is your user name and **test** is your password.

The problem here is that this process enables the pogoplug unit/drive for root only, not for the other users.

I'll have to figure out that one later.

In the meantime, "sudo nautilus" from the terminal will get you a file manager that will allow you access to the drive at the mount point (/media/pogoplug or where-ever else you put it.) Just be careful not to go nuts with this window. That's a "root" filesystem window, which means you have permission to delete ANYTHING....including stuff that might hurt your system.

Good luck!

---

### Post by sjpn on 2009-08-19
i had to do 
```

sudo chmod +r /etc/fuse.conf
```

to get it to work with my user
I also created a simple script to toggle it

```
#!/bin/bash

#find the current state of pogoplug
state=`pgrep pogoplugfs`

#if off, turn it on, else turn it off
if [ "$state" = "" ]; then
~/Programs/pogoplugfs --user user@abc.com --password password --mountpoint /media/pogo
else
echo myUserPassword | sudo -S umount /media/pogo
fi
```

i'm not very good at shell scripts, but i configured keyboard shortcuts to this script and I can mount/unmount my pogoplug with a keystroke :)
note:it requires your user password and pogoplug password in clear text. a clear security violation.

---

### Post by abodsalas on 2011-01-10
Hi there.

What I did for it to work as it should.
1) Install al the FUSe and HFS files as mentioned in the [http://www.pogoplugged.com/article/13974/How-to-Install-Pogoplug-Drive-on-Ubuntu-10.04-Lucid-Lynx/](http://www.pogoplugged.com/article/13974/How-to-Install-Pogoplug-Drive-on-Ubuntu-10.04-Lucid-Lynx/) link.

2) I created a /pogoplug/ folder where I put the pogoplugfs file.
3) In Terminal 'cd /pogoplug'               ***-----> Very important to do this first
4) sudo usermod -a -G fuse $(id -u -n)
5) sudo mkdir /media/pogoplug
6) sudo chown root:fuse /media/pogoplug
7) sudo chmod 0775 /media/pogoplug

then execute the command:
./pogoplugfs --user YOUREMAIL --password YOURPASSWORD --mountpoint /media/pogoplug

Replacing YOUREMAIL and YOURPASSWORD with your pogoplug's email and password account.

**You should NOT add a 'sudo' before ./pogoplugfs** in order for it to work. It should work perfectly well without a sudo.


With this working perfectly I added the command in the System-Preferences-Startup Applications; so it would automatically connect to the pogoplug drive on startup. I used this configuration on cammand line:

/home/YOURUSERNAME/pogoplug/./pogoplugfs --user YOUREMAIL --password YOURPASSWORD --mountpoint /media/pogoplug

Replacing YOURUSERNAME, YOUREMAIL and YOURPASSWORD with the correct names.


Saludos,

Andrés

---

### Post by msaurora on 2011-07-23
Thanks to everyone who has posted on this topic. This has made my life a lot simpler.

Anyway ... I just did a pogoplug install on Ubuntu 11.04. I did not install anything new except the pogoplug utility. gvfs-fuse 1.8.0-0ubuntu2 is installed on my machine and was sufficient to get me up and running. After this I did the following, which is a slightly different than prior posts.

1) Download and unpack pogoplug utility to a directory
2) cd to download directory
3) sudo usermod -a -G fuse $(id -u -n)
4) sudo mkdir /media/pogoplug
5) sudo chown root:fuse /media/pogoplug
6) sudo chmod **0777** /media/pogoplug/
7) sudo chmod +r /etc/fuse.conf

I was then able to successfully run the pogoplufs application and access my data. I think step 6 could have used 0775 if I would have added myself to the fuse group, but this works.

Good Luck

---

