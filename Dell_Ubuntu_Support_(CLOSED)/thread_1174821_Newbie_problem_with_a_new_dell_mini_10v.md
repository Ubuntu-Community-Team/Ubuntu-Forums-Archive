---
title: "Newbie problem with a new dell mini 10v"
date: 2009-05-31
forum: Dell Ubuntu Support (CLOSED)
---

### Post by bigmadmonkey on 2009-05-31
Hi Guys

Im hoping someone can help me or point me in the right direction
I have just got a new dell mini 10v
got it on the internet tryed doing the updates and also installing an html editor

But when i do the updates i get the following message

E: /var/cache/apt/archives/linux-image-2.6.24-22-lpia_2.6.24-22.45netbook9_lpia.deb: files list file for package `libxcb-shape0' is missing final newline

What does that me im a brand new ubuntu user, well is the 1st time i havnt used windows (sorry)

I really dont know what to do.

To make matters worse the dell website is telling my service tag is not even correct for a uk model, i know this netbook was made in china been waiting for 2 weeks.

[LEFT]Any suggestions would be great

Thanks
Stuart

[/LEFT]

---

### Post by Daveski on 2009-05-31
> **bigmadmonkey said:**
> 
But when i do the updates i get the following message

E: /var/cache/apt/archives/linux-image-2.6.24-22-lpia_2.6.24-22.45netbook9_lpia.deb: files list file for package `libxcb-shape0' is missing final newline

What does that me im a brand new ubuntu user, well is the 1st time i havnt used windows (sorry)


Could be a corrupt file. Check in /var/lib/dpkg/info/ for a file called libxcb-shape0.list and rename or move it.

You could try getting the installer (apt) to clean and fresh files with:

```
apt-get clean
apt-get update
```

---

### Post by ugm6hr on 2009-05-31
I would suggest trying to get apt-get to fix its own errors.

In Terminal:

```
sudo apt-get update
sudo apt-get install -f
```

Post the output from these commands, it might help...

---

### Post by metalmoggy on 2009-06-04
> **bigmadmonkey said:**
> Hi Guys

Im hoping someone can help me or point me in the right direction
I have just got a new dell mini 10v
got it on the internet tryed doing the updates and also installing an html editor

But when i do the updates i get the following message

E: /var/cache/apt/archives/linux-image-2.6.24-22-lpia_2.6.24-22.45netbook9_lpia.deb: files list file for package `libxcb-shape0' is missing final newline

What does that me im a brand new ubuntu user, well is the 1st time i havnt used windows (sorry)

I really dont know what to do.

To make matters worse the dell website is telling my service tag is not even correct for a uk model, i know this netbook was made in china been waiting for 2 weeks.

[LEFT]Any suggestions would be great

Thanks
Stuart

[/LEFT]


Identical problem here, with a Dell Mini 10v delivered this morning.  And there are 15 updates waiting to install, all being blocked by that one problematic line.  A simple fix for this pair of complete newbies would be very much appreciated!

---

### Post by metalmoggy on 2009-06-04
> **ugm6hr said:**
> I would suggest trying to get apt-get to fix its own errors.

In Terminal:

```
sudo apt-get update
sudo apt-get install -f
```Post the output from these commands, it might help...

Okay, done that - here's what I got back:

Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy Release.gpg
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/main Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/universe Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/multiverse Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/restricted Translation-en_US
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates Release.gpg
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/main Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/universe Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/multiverse Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/restricted Translation-en_US
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security Release.gpg
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/main Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/universe Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/multiverse Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/restricted Translation-en_US
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base Release.gpg
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/main Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/universe Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/multiverse Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/restricted Translation-en_US
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini Release.gpg
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/universe Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/multiverse Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/restricted Translation-en_US
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy Release
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates Release
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security Release
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base Release
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini Release
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/main Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/universe Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/multiverse Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/restricted Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/main Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/universe Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/multiverse Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/restricted Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/main Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/universe Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/multiverse Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/restricted Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/main Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/universe Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/multiverse Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/restricted Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/main Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/universe Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/multiverse Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/restricted Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/main Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/universe Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/multiverse Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/restricted Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/main Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/universe Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/multiverse Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/restricted Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/main Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/universe Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/multiverse Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/restricted Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/universe Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/multiverse Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/restricted Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/universe Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/multiverse Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/restricted Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/main Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/universe Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/multiverse Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/restricted Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/main Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/universe Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/multiverse Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/restricted Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/universe Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/multiverse Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/restricted Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/universe Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/multiverse Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/restricted Sources
Reading package lists... Done

Does that make any sense?

---

### Post by metalmoggy on 2009-06-04
> **Daveski said:**
> Could be a corrupt file. Check in /var/lib/dpkg/info/ for a file called libxcb-shape0.list and rename or move it.

You could try getting the installer (apt) to clean and fresh files with:

```
apt-get clean
apt-get update
```

Okay, tried that too, with this result:

apt-get clean
E: Could not open lock file /var/cache/apt/archives/lock - open (13 Permission denied)
E: Unable to lock the download directory

Hmph!

---

### Post by Talon2 on 2009-06-04
> **metalmoggy said:**
> Okay, tried that too, with this result:

apt-get clean
E: Could not open lock file /var/cache/apt/archives/lock - open (13 Permission denied)
E: Unable to lock the download directory

Hmph!

Try these commands instead:

sudo apt-get clean
sudo apt-get update

The sudo command allows you to operate as "root" or "super user."  sudo will cause the system to ask for your password.

For what it is worth:  I have a Mini 9.  I am currently very happy with it but I was not happy with it when it first arrived.  In my opinion Ubuntu 8.04 was just not ready for netbooks.  The new 9.04 Netbook Remix works great here on my Mini 9.  The only issue I can think of for the Mini 10 is that the Mini 10 has a different video chipset.  I think I saw where one of the devs at Canonical has recompiled and support is working for the Mini 10 and Mini 12 but you might want to ask questions about that before installing 9.04 Netbook Remix.

Good luck.

---

### Post by metalmoggy on 2009-06-04
> **Talon2 said:**
> Try these commands instead:

sudo apt-get clean
sudo apt-get update

The sudo command allows you to operate as "root" or "super user."  sudo will cause the system to ask for your password.

For what it is worth:  I have a Mini 9.  I am currently very happy with it but I was not happy with it when it first arrived.  In my opinion Ubuntu 8.04 was just not ready for netbooks.  The new 9.04 Netbook Remix works great here on my Mini 9.  The only issue I can think of for the Mini 10 is that the Mini 10 has a different video chipset.  I think I saw where one of the devs at Canonical has recompiled and support is working for the Mini 10 and Mini 12 but you might want to ask questions about that before installing 9.04 Netbook Remix.

Good luck.

Cheers for that, I'll give it a go.  However, a rather more serious problem has cropped up:  on three occasions now the system has completely frozen; the cursor, and even the clock got stuck, and the only way out was to hit and hold the power switch.  *Not impressed.*

Edit:  Okay, tried that, and got exactly the same enormous block of text as before (see above).  *Sigh.*

---

### Post by ugm6hr on 2009-06-04
Please report on:
```
sudo apt-get install -f
```

---

### Post by RustyRus on 2009-06-04
has anyone figured out a solution to this? I just got the 10v and have theexact same issue. I have tried downloading the updates throguh the terminal and also reinstalling the package from the package manager.


Any ideas. This is kinda blows

---

### Post by Daveski on 2009-06-05
As soon as mine is delivered I'll have a good look at the problem.

---

### Post by Brandon Williams on 2009-06-05
I don't have one of these myself, but I'll try to move you in the right direction nevertheless.

First, run 'od -a /var/lib/dpkg/info/libxcb-shape0.list' at a command prompt. This will output the content of the file as a character dump with multiple 16-character rows of data, rather than using the typical line-by-line format. On my system, the output looks like this:
```
0000000   /   .  nl   /   u   s   r  nl   /   u   s   r   /   s   h   a
0000020   r   e  nl   /   u   s   r   /   s   h   a   r   e   /   d   o
0000040   c  nl   /   u   s   r   /   s   h   a   r   e   /   d   o   c
0000060   /   l   i   b   x   c   b   -   s   h   a   p   e   0  nl   /
0000100   u   s   r   /   s   h   a   r   e   /   d   o   c   /   l   i
0000120   b   x   c   b   -   s   h   a   p   e   0   /   c   o   p   y
0000140   r   i   g   h   t  nl   /   u   s   r   /   l   i   b  nl   /
0000160   u   s   r   /   l   i   b   /   l   i   b   x   c   b   -   s
0000200   h   a   p   e   .   s   o   .   0   .   0   .   0  nl   /   u
0000220   s   r   /   s   h   a   r   e   /   d   o   c   /   l   i   b
0000240   x   c   b   -   s   h   a   p   e   0   /   R   E   A   D   M
0000260   E  nl   /   u   s   r   /   s   h   a   r   e   /   d   o   c
0000300   /   l   i   b   x   c   b   -   s   h   a   p   e   0   /   N
0000320   E   W   S   .   g   z  nl   /   u   s   r   /   s   h   a   r
0000340   e   /   d   o   c   /   l   i   b   x   c   b   -   s   h   a
0000360   p   e   0   /   c   h   a   n   g   e   l   o   g   .   D   e
0000400   b   i   a   n   .   g   z  nl   /   u   s   r   /   l   i   b
0000420   /   l   i   b   x   c   b   -   s   h   a   p   e   .   s   o
0000440   .   0  nl
0000443
```
The only row we're interested in is the second-to-last one (numbered 0000440 in my example), and the only character we're interested in is the very last character on that row ('nl' in my example). We want that character to be 'nl'. If it is, then the error you're getting from apt-get is misleading and I don't know what to suggest next. However, if the last character isn't 'nl', we may be able to fix it as follows.

Open the file with 'sudo nano /var/lib/dpkg/info/libxcb-shape0.list' and **don't change anything in the file**. Just press Ctrl+O to write the file back to disk and press Ctrl+X to exit nano. Now run the od command on this file again and check to make sure that nano inserted 'nl' as the last character. This may or may not solve the problem for you, but it's worth a try.

One additional point of note is that if you open the file in nano and you can't read it (the characters just show up as apparent giberish) then there's a bigger problem that probably won't be solved by the above, whether or not a newline is inserted.

---

### Post by mortenkjeldgaard on 2009-06-05
I suggest you try using Ubuntu 9.04 (jaunty) instead of hardy. The kernel is newer and lots of things have happened to Xorg. AFAIK, it should run just fine on the mini-10v, which uses a different graphics chip than the Mini-10. The latter used to have problems but those have now been solved, see [http://mok0.wordpress.com/2009/05/25/ubuntu-on-the-dell-mini-10-2/]("http://mok0.wordpress.com/2009/05/25/ubuntu-on-the-dell-mini-10-2/"). Use something like this for your /etc/apt/sources.list file:


For lpia architecture:
> 
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) jaunty main restricted universe
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) jaunty-security main restricted universe


For i386 architecture:

> 
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main restricted universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted universe


---

### Post by bunt3 on 2009-06-06
Hey everyone,

I have the same problem with my Dell Mini10v:

E: /var/cache/apt/archives/linux-image-2.6.24-22-lpia_2.6.24-22.45netbook9_lpia.deb: files list file for package `libxcb-shape0' is missing final newline

I hope someone can help us...):P

---

### Post by jaguar080 on 2009-06-06
> **ugm6hr said:**
> Please report on:
```
sudo apt-get install -f
```

i have the same problem and ran apt-get install -f after the clean and update. this is the result:

```
pablo@pablo:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gnome-cards-data libggzmod4 guile-1.6-libs libggz2 libqthreads-12 gnome-games-data libggzcore9
  libguile-ltdl-1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by amosa on 2009-06-06
I have the same problem with my Mini 10V which means that I cannot install anything - major pain in the ***. 

By the way, after running 

od -a /var/lib/dpkg/info/libxcb-shape0.list

I get a load of nulls...

~$ od -a /var/lib/dpkg/info/libxcb-shape0.list
0000000 nul nul nul nul nul nul nul nul nul nul nul nul nul nul nul nul
*
0000440 nul nul nul
0000443

Something does not look right.

---

### Post by Daveski on 2009-06-06
Oh dear - does this mean that Dell have a corruption in their master image that they are putting on these machines before shipping them?

---

### Post by RustyRus on 2009-06-06
All,

I have the mini 10v and was experiencing the same issues as you all were. I downladed the newest net remix from ubuntu and put it on. Much happier with this version. It installed with no issues and all drivers and applications worked without any issues.

This laptop is mostly for my wife and she likes the new desktop type. you can switch between the new and classic easily and quickly. this is  a must install IMO.

Thanks to those with insight and help on the above issues.

---

### Post by dmchapple on 2009-06-06
Just received a Mini 10 today, and it has exactly the same problem. Normally I would remove the Dell stuff and replace it with Jaunty, but my wife likes the Dell netbook interface! :)

---

### Post by dmchapple on 2009-06-06
ok, I'm no expert but this seemed to fix it for me:

cd /var/lib/dpkg/info
sudo rm libxcb-shape0.list
sudo apt-get --reinstall install libxcb-shape0

Hope that helps someone!

---

### Post by RustyRus on 2009-06-06
dmchapple the newest version has a much better netbook desktop. It is alot more fucntional. The install would take about 20 minutes and i promise you she will like it better.

---

### Post by pendennis on 2009-06-07
> **dmchapple said:**
> ok, I'm no expert but this seemed to fix it for me:

cd /var/lib/dpkg/info
sudo rm libxcb-shape0.list
sudo apt-get --reinstall install libxcb-shape0

Hope that helps someone!

Thank-you, that seemed to do the trick for me.

---

### Post by dmchapple on 2009-06-07
Thanks RustyRus.  I'm using the latest ubuntu netbook remix on my Dell Mini 9 under Ubuntu 9.04.  It's just that the new Mini 10 is for my wife, and she prefers the Dell netbook interface - until I can convince her otherwise! ;)

Hopefully it's just that one corrupt file on the Dell install, and removing it and reinstalling seems to do the trick.

---

### Post by amosa on 2009-06-07
Sorted - nice one!

---

### Post by metalmoggy on 2009-06-10
Huge thanks to **dmchapple** for the solution, which worked after an initially worrying line in the Terminal window about a non-existent directory, and to others for their contributions.  It was a relief to see that this was a common problem.  The system freeze I also reported appears to have - for now - been fixed, too.

However, after installing a codec package Dell neglected to include with the 10v's media player, the update list was itself updated, and there now appear to be *190 additional updates* available to install.  Yikes!

---

### Post by Whitston on 2009-06-12
> **RustyRus said:**
> All,

I have the mini 10v and was experiencing the same issues as you all were. I downladed the newest net remix from ubuntu and put it on. Much happier with this version. It installed with no issues and all drivers and applications worked without any issues.

This laptop is mostly for my wife and she likes the new desktop type. you can switch between the new and classic easily and quickly. this is  a must install IMO.

Thanks to those with insight and help on the above issues.

I have the same problem as the others on this thread, but am a bit reluctant to write command lines (v inexperienced).  Thought I might give your solution a go.  It would help me a lot if you could let me have the address of the web site you downloaded from and the description of the download.  Lastly, I have no idea what a "net remix" is???  Could you give a brief explanation please.

Thanks

---

### Post by ugm6hr on 2009-06-12
> **Whitston said:**
> I have the same problem as the others on this thread, but am a bit reluctant to write command lines (v inexperienced).  Thought I might give your solution a go.  It would help me a lot if you could let me have the address of the web site you downloaded from and the description of the download.  Lastly, I have no idea what a "net remix" is???  Could you give a brief explanation please.

Thanks

It is much easier to copy and paste command line entries from here (experience not required!) than installing a new operating system.

Nevertheless, installing Ubuntu Netbook Remix is fairly easy.

Details at [http://ubuntu.com/](http://ubuntu.com/)

---

### Post by Daveski on 2009-06-12
Have you looked here:

[http://www.canonical.com/projects/ubuntu/unr](http://www.canonical.com/projects/ubuntu/unr)

---

### Post by Whitston on 2009-06-13
Thanks for the reply.  I went to ubuntu.com and read that I need 4GB to download the remix. I don't have that so that option is out for me.  I was also a bit confused as to whether the remix was based on 8.04, or whether I would be changing to 9.04.
Thanks also for the links to beginner pages.  I had found the pocket guide by Keir Thomas which I hope will get me started.
Had not thought about cut and paste for the code (that solves the problem of whether the character after shape is an O or a 0).
One last question.  I assume those code lines work on their own, and I do not have to have a cd drive with the Ubuntu disc in it.  (the fact that the code starts with cd is what go me worried.)
Not many people as basic as me :)

Jim

---

### Post by Whitston on 2009-06-13
Thanks for the link Daveski.   Very useful in explaining what the Netbook remix is, especially the video.  Looks like a very user friendly desktop.  Unfortunately I don't have the spare GBs to download it, so will persevere with the code (eventually)

Jim

---

### Post by ugm6hr on 2009-06-13
Netbook Remix is based on 9.04 (hence called 9.04NBR).

The file is about 700MB (not 4GB).

You need a 1GB+ USB flash drive to install it.

The command **cd** means *change directory*; no CD drive required.

---

### Post by metalmoggy on 2009-06-13
Quite the potential nightmare if you go ahead with 'em, since they may not all successfully install, and can prevent Firefox from launching.  Additionally, upon reboot, you may get *this* disconcerting message appearing at the bottom right of your screen:

"The configuration defaults for Gnome Power Manager have not been installed correctly.  Please contact your computer administrator."

The solution to completing the update installations, which fixes this problem, along with the Java-related ones affecting the Firefox web browser, is found if you launch the Update Manager via the Ubuntu icon at the top of the screen.  Open a Terminal window (via the "Accessories" sub-menu), and sudo bash to obtain root administrator access.  Then type the following line (including spaces) to kickstart the rest of the interrupted installations:

**dpkg --configure -a**

Once you restart, the 10v will check its allocated disk space (in total, the 190 updates amount to >250 Mb), reboot, and everything should work again as normal.  Just one final additional note - the start-up sound may not always occur.  No idea why...

---

### Post by Whitston on 2009-06-14
> **ugm6hr said:**
> Netbook Remix is based on 9.04 (hence called 9.04NBR).

The file is about 700MB (not 4GB).

You need a 1GB+ USB flash drive to install it.

The command **cd** means *change directory*; no CD drive required.

I would like to thank **DMCHAPPLE**  **DAVESKI** and **UGM6HR** for their help in solving the problem.  Decided to go with the DMCHAPPLE code and after some problems managed to get it to work.  Completed the elusive downloads and all seems fine (fingers crossed).

Thanks again to all.

Jim

---

### Post by And-car on 2009-06-14
Me too, thanks!

---

### Post by Whitston on 2009-06-16
Hi, on my Dell mini the F1 key used alone constructs a new window (about 4:3) and passes that signal to the VGA where it can be displayed on a digital tv.   I have looked for a way to achieve the same function through the menus, but with no luck.
My concern is that in a future upgrade I might lose the Dell F1 function and not know how to achieve it some other way.
Can anyone tell me please how this can be achieved either by menus or through terminal.

Thanks

Jim

---

### Post by Fangman on 2009-06-23
The install package is 4gb, you can download it to a USB drive and then plug it in to install from.

---

### Post by bobsteamer on 2009-06-23
Yesterday I received my wife's machine with all the problems quoted above.  There is no way I will try to correct it (I am a Window's man but wanted a fast machine for my wife).  I have asked Dell to take it back and will look at the latest Linux EEEPC which I know is utterly reliable as I bought my daughter one of the first ones that came out and was very impressed on how fast it was.  Having bought DELL for over 25 years(Business & Private) I am bitterly disappointed.

---

### Post by Daveski on 2009-06-24
> **bobsteamer said:**
> I have asked Dell to take it back and will look at the latest Linux EEEPC which I know is utterly reliable as I bought my daughter one of the first ones that came out and was very impressed on how fast it was.  Having bought DELL for over 25 years(Business & Private) I am bitterly disappointed.

Oh dear, that is a shame.
The eee PCs are essentially the same spec as the Dell, so speed will be virtually identical. I have heard that the 4Gb system volume can become completely full when running the eee updates, and the fix for this is also a command line (terminal) command.

---

### Post by bobsteamer on 2009-06-24
My wife wants the DELL!
 
In Terminal I typed in:    cd /var/lib/dpkg/info and get a reply of "No such file or directory"
 
Do I have to Logon as "Root" before I try this?
 
I am a real Linux Newbee!

---

### Post by Daveski on 2009-06-24
> **bobsteamer said:**
> My wife wants the DELL!
 
In Terminal I typed in:    cd /var/lib/dpkg/info and get a reply of "No such file or directory"
 
Do I have to Logon as "Root" before I try this?
 
I am a real Linux Newbee!

I have just opened a terminal and typed *cd /var/lib/dpkg/info/* and hit return and I am in that location (not as root).

A tip is to use the TAB key to auto-complete paths, so type **cd /va** and then press TAB and the **r/** will be added. Please note that Linux is case sensitive (all these are lowercase) and that you must have a space after the cd command. Oh, yes, and the slashes are the other way to the Windows ones.

---

### Post by bobsteamer on 2009-06-24
Missed the space after the **cd -** everything OK now
 
Many thanks **Daveski** for your help.
 
My wife can keep her DELL now (it really is a beautiful bit of kit).

---

### Post by cgregan on 2009-06-24
> **metalmoggy said:**
> Cheers for that, I'll give it a go.  However, a rather more serious problem has cropped up:  on three occasions now the system has completely frozen; the cursor, and even the clock got stuck, and the only way out was to hit and hold the power switch.  *Not impressed.*

Edit:  Okay, tried that, and got exactly the same enormous block of text as before (see above).  *Sigh.*


Can you please post the results of the following command from terminal?

cat /boot/grub/menu.lst

---

### Post by Doctorcito on 2009-06-26
In case it is of help to others, I have the same problem. I phoned Dell's Presto "support" who apparently were not aware of this problem, but they put me through to some software support folk who were in fact helpful and said that they were working on a fix that would be emailed to customers in a few days.

---

### Post by bobsteamer on 2009-06-26
> I phoned Dell's Presto "support" who apparently were not aware of this problem, but they put me through to some software support folk who were in fact helpful and said that they were working on a fix that would be emailed to customers in a few days.
 
Which country? "Dell's Presto "support" doesn't sound familiar!

---

### Post by Doctorcito on 2009-06-26
> **bobsteamer said:**
> Which country? "Dell's Presto "support" doesn't sound familiar!
 
 
UK - or should I say Europe? But the call centre was in New Delhi.
 
_[COLOR=#800080][http://www1.euro.dell.com/content/topics/topic.aspx/emea/topics/presto/home?c=uk&l=en&s=dhs](http://www1.euro.dell.com/content/topics/topic.aspx/emea/topics/presto/home?c=uk&l=en&s=dhs)[/COLOR]_

---

### Post by Doctorcito on 2009-07-09
> **Doctorcito said:**
> In case it is of help to others, I have the same problem. I phoned Dell's Presto "support" who apparently were not aware of this problem, but they put me through to some software support folk who were in fact helpful and said that they were working on a fix that would be emailed to customers in a few days.
 
Well I suppose I was being a bit naive. NO email from Dell "support" apart from one asking about my impressions of the call handler. So I followed the advice above and fixed the problem.
 
I wonder how many others are stuck on the same problem?
 
Why is DELL so unresponsive?
 
Incidentally according to their online "help", my 10v's Service Tag does not exist.

---

### Post by wrinkley1 on 2009-07-09
Dell were of course lying when they said they were unaware of the problem. I reported it weeks ago to Dell UK (and I'm sure many other people will also have reported it).I also got an initially apparently helpful response and then heard nothing further from them.I reported it via the hardware faults route as Dell will not give software support. I pointed out that although it was a software problem it was of their making and they ought to sort it out. I got a reply saying it would be forwarded for response but that was the last I heard.This was my first experience of Linux - meaningless error messages within days of receiving the machine. If I hadn't found this thread it would also have been the last time I bought a Linux machine, I'm sure it will be for many newbies. My impression of Linux has improved since but it will be the last time I buy a Dell machine.

---

### Post by exile_pete on 2009-07-27
> **dmchapple said:**
> ok, I'm no expert but this seemed to fix it for me:

cd /var/lib/dpkg/info
sudo rm libxcb-shape0.list
sudo apt-get --reinstall install libxcb-shape0

Hope that helps someone!

This resolved the problem for me as well, cheers dmchapple  :P

---

### Post by nicolehill973 on 2009-09-08
Thank you everyone, I have been fumbling around with my netbook in hand and tears all over it for 5 days. No sound, no DVD, no music. totem what is that suppose to do, because it's not doing anything right now. Watching my money and mind just float away like a beautiful dream that the bad breath of your dog wakes you up from.  This should help make my life a bit easier, fun on the road, ease with my school work. I was really thinking of returning it to Dell and getting Windows put on the thing. But like most things in life we can get through anything, it we keep going and don't forget to breath. I now think I see the light at the end of this tunnel.  I'm at work right now, but once I get home I'll hooking that red machine online and getting that thing fixed.  
SO FIRED UP!!

---

### Post by Montala on 2009-09-09
Hi,
 
Just in case anyone reads the first few posts in this thread, and is having second thoughts about buying a Ubuntu powered Mini 10v from Dell, it does look as if they have now solved the problems which were being reported.
 
I redeived a new 10v from them a week ago now, and have managed to update it with no problems at all... I even succeeded in updating Pidgin to the latest version, following the instructions on their website!
 
Just for information, I am in the UK, and I also received a Ubuntu 8.04 LTS machine specific recovery DVD ROM... which of course is not much use without an external optical drive! :)

---

### Post by Jobanjo422 on 2009-09-17
Thx to all who contributed to solution of this problem.  It had been driving me crazy!

---

### Post by sheriduh on 2009-10-19
I received a Dell mini just last week, and had the same error.  I found a solution ([https://answers.launchpad.net/ubuntu/+source/update-manager/+question/78863](https://answers.launchpad.net/ubuntu/+source/update-manager/+question/78863)) that was quite involved, and am concerned that I messed something up.  After working through all the lines that the solution suggested, with two errors, my system told me I needed 195 updates.  I am frustrated that Dell is still sending out computers with this known error.

Now I am having some quirky problems with programs.  I don't know if they are bugs, or if I messed something up with the solution.  Can anyone help?

---

### Post by domineo on 2010-04-30
Hi, 

I have the same problem and I found the solution here (it's works for me :) ) :

[http://darrenchapple.wordpress.com/2009/06/07/dell-mini-10-corrupt-libxcb-shape0-file/](http://darrenchapple.wordpress.com/2009/06/07/dell-mini-10-corrupt-libxcb-shape0-file/)

[COLOR=Sienna]If you’ve recently bought a Dell Mini 10, you may have a problem with a corrupt file in Dell’s default build.  This will prevent you from running your automatic updates, installing new packages, etc.

If you get a message like this:

/var/cache/apt/archives/linux-image-2.6.24-22lpia_2.6.24-22.45netbook9_lpia.deb:
 files list file for package `libxcb-shape0' is missing final newline

then you’ll want to fix it by removing the offending file, and reinstalling the package.  This should work:

cd /var/lib/dpkg/info
sudo rm libxcb-shape0.list
sudo apt-get --reinstall install libxcb-shape0[/COLOR]

---

