---
title: "Installing Gnome from CLI"
date: 2009-03-27
forum: Desktop Environments
---

### Post by Thwelve on 2009-03-27
I have Ubuntu 8.10 on my laptop, dual booting with WinXP.

Because I do not use a printer with my laptop, I decided to remove cups. I went into the package manager and removed *all* packages related to cups. I was warned of other packages (OpenOffice, Firefox,.. a very long list covering almost everything!) that had a dependency on cups. I assumed that only the dependency would be removed but on rebooting I find myself stuck at the command prompt.

How can I now restore the Gnome desktop?

A couple of points:
1. I'm no expert (as you can figure out), so a simple solution will be appreciated.
2. I'd like to install all packages from my LiveCD (I'm not sure if I can connect to the internet, I believe I also managed to remove the network manager etc)
3. I am ok with a minimal number of packages (Gnome+Firefox+connectivity to the internet) to be installed right now as I would like to upgrade to 9.04 when its out.
4. I do not want to experiment too much on my own as I don't want to lose Windows and have to do a complete re-install of both Win and Ubuntu.

I did some digging around the the following should get me started:
```
$ sudo apt-cdrom add
```
followed by
```
$ sudo apt-get install ubuntu-desktop
```

Will this work? What else will I have to do to get my drivers (display, wireless etc) up and running?

Thanks!!

---

### Post by nebileix on 2009-03-27
yeah, that should work.

---

### Post by stderr on 2009-03-27
Yeah, looks fine. ubuntu-desktop is a meta-package which will install all the main packages related to the Ubuntu GUI. Hopefully it should sort out the graphics drivers, if they've also been removed; if not, the Restricted Driver thingy should moan at you soon after you get back into the GUI anyway. As for the network, I think any NetworkManager settings should have been preserved, since you presumably used 'sudo apt-get remove ...' as opposed to the --purge flag.

Should be fine.

---

### Post by Thwelve on 2009-04-04
I somehow guessed it couldn't be that simple!
Anyway, tried installing ubuntu-desktop, but it does not work!

I get a very long list, I assume of packages that will be installed. I'm told that 1 package will be upgraded (transmission-common), 255 will be newly installed, 0 removed and 6 not upgraded.
I am asked if I want to continue, I choose yes, and I get a long list of failures:
Failed to fetch [http://in.archive.ubuntu.com/..../somepackagename](http://in.archive.ubuntu.com/..../somepackagename) Could not resolve 'in.archive.ubuntu.com'

I am guessing what is happening is that ubuntu is attempting to download the packages off the internet based repositories.

I cannot connect to the internet, so I want to use the packages off my live CD. Any ideas anyone?

---

### Post by oldos2er on 2009-04-04
```
sudo nano /etc/apt/sources.list
```

 Run the above command, add a comment mark (#) at the beginning of each line EXCEPT the deb cdrom line. Use Ctrl-X to exit the file (it will prompt you to save your changes, hit Y), then run

```
sudo apt-get update && sudo apt-get install ubuntu-desktop

```

---

### Post by Thwelve on 2009-04-04
This is what I get now:
> Package ubuntu-desktop is not available, but is referred to by another package. This may mean that the package is missing, has been obsoleted, or is only available from another source
E: Package ubuntu-desktop has no installation candidate

---

### Post by hictio on 2009-04-04
Another option, useful if you are a bit of on an HDD space constraint is issuing:

```

sudo aptitude install ubuntu-desktop --without-recommends

```

That will get you a Gnome Desktop without extras (Firefox, GIMP, Evolution, Open Office, etc), so you can add only the ones you need later on.

---

### Post by Thwelve on 2009-04-06
Thanks! I'll try that later tonight, though HDD space is not really a constraint.

I did find this though:
[http://www.linuxforums.org/forum/ubuntu-help/138532-solved-install-packages-cdrom-thru-terminal.html](http://www.linuxforums.org/forum/ubuntu-help/138532-solved-install-packages-cdrom-thru-terminal.html)

I appears that someone else has encountered a similar problem and found a solution by downloading and installing individual packages. I can try this but can someone tell me which packages will I need (bare minimum, to get my desktop and networking up) and where can I get these packages from.

Thanks!!

---

### Post by Thwelve on 2009-04-08
tried ```
sudo aptitude install ubuntu-desktop --without-recommends
```
it took out another 58 packages and installed nothing.

Not really sure what to do next.

---

### Post by hictio on 2009-04-08
> **Thwelve said:**
> tried ```
sudo aptitude install ubuntu-desktop --without-recommends
```
it took out another 58 packages and installed nothing.

Not really sure what to do next.

I'm sorry, what do you mean it installed nothing?
You mean you have no graphical environment running?
Did you started it, I mean, your Gnome?

---

### Post by Thwelve on 2009-04-09
That right, Gnome was not installed. When I tried using the --without-recommends option, I was told that no new packages would be installed and 58 (i think) would be removed. I don't have the list of packages but I do remember glibc, python etc were removed.

So I am still stuck at the command line and just cannot start gnome :(.

---

### Post by hictio on 2009-04-09
> **Thwelve said:**
> That right, Gnome was not installed. When I tried using the --without-recommends option, I was told that no new packages would be installed and 58 (i think) would be removed. I don't have the list of packages but I do remember glibc, python etc were removed.

So I am still stuck at the command line and just cannot start gnome :(.

That's weird... Do you still have the lines commented on the 'sources.list' file? Perhaps it is because of that? I have issued that a couple of time, but always downloading from the Ubuntu repositories, not my CDROM.

---

### Post by Thwelve on 2009-04-11
It works!

I managed to do a ubuntu-desktop install from the network and now I have Gnome and I have my GUI desktop back!

Not sure what the problem was, but when I was trying this earlier, I got an error and I assumed I was not on the network. Yesterday I just tried pinging my modem/router and got a reply but still could not install the ubuntu-desktop. I tried ```
sudo apt-get update
``` which started downloading some packages from the network. I next tried ```
sudo apt-get install ubuntu-desktop
``` which worked! All packages downloaded and installed!

Still not sure what the problem was, but I am surprised there is no easy way to install the packages from the CD.

Anyway, thanks to all who tried to help!

---

