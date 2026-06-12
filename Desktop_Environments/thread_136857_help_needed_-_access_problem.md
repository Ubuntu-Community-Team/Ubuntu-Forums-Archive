---
title: "help needed - access problem"
date: 2006-02-26
forum: Desktop Environments
---

### Post by -insert username here- on 2006-02-26
hi, i'm new to ubuntu, i just started using it with vmware.  i've used red hat before.  i want to put something in /usr/lib/ but when i try to copy it, i get this error:

You do not have permissions to write to this folder.

how do i make it so i have permission?

---

### Post by Sutekh on 2006-02-26
I don't know how Red Hat works, so excuse me if I cover stuff you already know.

The only part of the filesystem that you (a common user) has access to is your home directory; /home/<username>/.  Everything else is owned by root. 

By default Ubuntu does not allow root access, but instead encourages the use of **sudo**.  Sudo allows commands to be 'run as root', temporarily giving you the power of the root user.

For a more complete explanation

[Ubuntu Wiki - Root/Sudo]("https://wiki.ubuntu.com/RootSudo")


For you to copy the files to /usr/lib/ you would need the following command
```
sudo cp /<path of file> /usr/lib/
```
Replacing <path of file> with the absolute path of the file you want to copy.

You will then be prompted for a password, which is the password you would have chosen as the first user on the system (assuming using vmware is the same as a real installation)

---

### Post by -insert username here- on 2006-02-26
thanks.  and yeah, vmware runs it like a real installation.

---

### Post by Sutekh on 2006-02-26
That's pretty cool.  Do you use vmware player?  (I'm just checking it out)

---

### Post by -insert username here- on 2006-02-26
i just run the virtual machine in the vmware console, but i know some people use the vmware player.

---

### Post by Sutekh on 2006-02-26
Oh I see.  Then its just a matter of downloading the virtual environment of the OS you want to use?

---

### Post by -insert username here- on 2006-02-26
ok, it's not working.  can someone tell me what stupid mistake i made this time?

```
sudo cp /home/daniel/desktop/firefox/* /usr/lib/mozilla-firefox/
```

---

### Post by Sutekh on 2006-02-26
Whats the error?  Invalid filename?  A users desktop should be capitalised
```
sudo cp /home/daniel/**D**esktop/firefox/* /usr/lib/mozilla-firefox/
```

---

### Post by -insert username here- on 2006-02-26
[QUOTE=Sutekh]Oh I see.  Then its just a matter of downloading the virtual environment of the OS you want to use?[/QUOTE]
you download the iso of the installation disc(s), make a new virtual machine, load the iso in the virtual cd drive, then boot it up and install as if it was a normal computer.

---

### Post by -insert username here- on 2006-02-26
okay, the capitalization worked.  but firefox still won't.  how am i supposed to install software?

---

### Post by Sutekh on 2006-02-26
You're trying to install software?  Firefox?

```
sudo apt-get install firefox
```

Installing software in Ubuntu is best handled by apt-get at the command line and Synaptic (in the System -> Administration menu) for a GUI

[Installing Software in Ubuntu ]("http://www.psychocats.net/linux/installingsoftware.php")

[Software Installation - Windows or Linux]("http://www.psychocats.net/essays/winuxinstall.php")

---

### Post by -insert username here- on 2006-02-26
yeah, the version of FF that came with ubuntu was out of date so i was trying to upgrade it.

---

### Post by Sutekh on 2006-02-26
To FF 1.5?

There are some threads on this let me do some digging

[Ubuntu Wiki - FirefoxNewVersion]("https://wiki.ubuntu.com/FirefoxNewVersion") - If you want to do it all manually

[Ubuntu Forums - Automatix]("http://ubuntuforums.org/showthread.php?t=66563") - automated installer for selected apps

---

### Post by -insert username here- on 2006-02-26
ill try the automatix thing, if that doesn't work, im going to switch back to red hat

---

