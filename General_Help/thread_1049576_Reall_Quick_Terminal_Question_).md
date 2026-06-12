---
title: "Reall Quick Terminal Question :)"
date: 2009-01-24
forum: General Help
---

### Post by naeeme on 2009-01-24
So I have an Acer Aspire One and I downloaded madwifi-0.9.4.tar.gz in order for Ubuntu to recognize my driver, so that I can use WiFi.

Right now madwifi-0.9.4.tar.gz is on my desktop, and I need to navigate through Terminal in order to install it.

Here is what I have tried:

> naeeme@ubuntu:~$ ~/madwifi-0.9.4
bash: /home/naeeme/madwifi-0.9.4: No such file or directory
naeeme@ubuntu:~$ ~/madwifi-0.9.4.tar.gz
bash: /home/naeeme/madwifi-0.9.4.tar.gz: No such file or directory
naeeme@ubuntu:~$ cd ~/Desktop
naeeme@ubuntu:~/Desktop$ 


Where do I go from there? Terminal doesn't even recognize the existence of madwifi-0.9.4.tar.gz on my Desktop, it seems!

I also tried installing Nautilus to make things easier, but it doesn't seem to work.

> naeeme@ubuntu:~$ sudo apt-get install nautilus-open-terminal
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package nautilus-open-terminal


Someone help me out, please!
I'm tired of Windows and really want to get into Ubuntu.

Thank you :p

Oh, by the way, I used Wubi to install Ubuntu because my AAO does not have a CD drive. Maybe that's the problem?

---

### Post by Adramelech on 2009-01-24
nautilus open terminal is a nautilus plugin, you can see it in the file menu with the name 'open in terminal', it opens the folder you are currently in.

If you have the madwifi file under your desktop the easy way to decompress it is to double click it.

---

### Post by oldos2er on 2009-01-24
You were on the right track with 'cd ~/Desktop' since that's the directory the file's in. Now enter

```
tar zxvf madwifi-0.9.4.tar.gz
```

then 'cd' into the madwifi directory. 

Re: nautilus-open-terminal, check System, Administration, Software Sources and make sure all repositories are enabled.

---

### Post by mb_webguy on 2009-01-24
Ok... there are a couple of issues here.  First, you should have needed to install Nautilus, since it is Ubuntu's default file browser.

Second, you *could* extract the archive from the command line as oldos2er said, but you can also extract a tarball (those .tar.*xx* files) using Archive Manager (File Roller).  Once you've done that, then you need to open the terminal and navigate to the folder where you extracted the archive.  If you saved an archive called "myarchive.tar.gz" to the Desktop, and extracted it to a directory called "myarchive", also on the Desktop, then in the terminal you would do the following:
```

naeeme@ubuntu:~$ cd Desktop
naeeme@ubuntu:~/Desktop$ cd myarchive
naeeme@ubuntu:~/Desktop/myarchive$

```
Now, if this is source code, to install it you would do the following:
```

naeeme@ubuntu:~/Desktop/myarchive$ ./configure
naeeme@ubuntu:~/Desktop/myarchive$ make
naeeme@ubuntu:~/Desktop/myarchive$ sudo make install

```
(Note that there will be a lot of output after each of the above commands.)

However, it's much better to compile and install software using checkinstall.  Read [this page]("https://help.ubuntu.com/community/CompilingEasyHowTo") for more information.  And of course, the best ways to install software are using Add/Remove Applications or Synaptic to install from the repositories, or using a .deb file.

---

