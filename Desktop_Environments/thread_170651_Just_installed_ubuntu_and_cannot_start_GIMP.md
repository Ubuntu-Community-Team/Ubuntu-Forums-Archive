---
title: "Just installed ubuntu and cannot start GIMP"
date: 2006-05-05
forum: Desktop Environments
---

### Post by Henrythewound on 2006-05-05
Hey there, first post, I could not find what I considered to be a better place to ask this question, so just let  me know if there is one.

I just installed ubuntu 5.10 and finally got my modem up and running. I'm all updated and want to start exploring what can be done in Linux. One major component I was looking forward to usig was the GIMP. When I try to start it from the drop down Applications menu, I get the following error:

Cannot launch entry
Details: Failed to execute child process "gimp-remote-2.2" (no such file or directory)

I am dealing with a fresh install and could not find any answers on GIMP's site or google. Any ideas?

Thanks a lot
-Wound

---

### Post by kaamos on 2006-05-05
Hello and welcome to the forums!

If you open a terminal (Applications->Accessories->Terminal) and type "gimp" there, what is the output?

---

### Post by Sef on 2006-05-05
It's seems gaim did not get properly installed.

Try this, open the terminal and type

sudo apt-get update

sudo apt-get upgrade

---

### Post by Henrythewound on 2006-05-05
I have done the update and upgrade, the system says I am up to date. I tried starting Gimp from the terminal as well (I do it this way on a Sun station at work) and it did not work either. I don't remember the exact message, but I will look again tonight. What about this "gimp-remote-2.2" that it claims is missing? I have not touched the files for GIMP since my initial install, and the symantec (sp?) manager says I have the latest version. I'll post the error later.

-Wound

---

### Post by Henrythewound on 2006-05-10
OK, sorry for the long delay, life happened. I updated everything that needed updating, ubuntu says the system is up to date. If I try to launch GIMP from the terminal I get 

bash: gimp: command not found

strange, its listed in the Applications menu. When I try to reinstall GIMP from the Synaptic Package Manager it asks for the install cd. When I put the CD in, I get the following errors

W: Failed to fetch cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release amd64 (20051012)]/pool/main/g/gimp/gimp_2.2.8-2ubuntu6_amd64.deb
  MD5Sum mismatch

So I'm guessing something is wrong with my initial install from CD, maybe the iso I burned to disc was corrupted in the GIMP portion, I have not run into any other strange errors.

Is there a way to download the most recent version of gimp and install it manually? I have not done this in linux, but I'm sure there are tutorials out there.

Thanks, 
Wound

---

### Post by louis_nichols on 2006-05-10
Try this:

```
sudo apt-get -y remove gimp && sudo apt-get install gimp
```

EDIT: then try starting it again

---

### Post by Henrythewound on 2006-05-10
I will try this tonight and report back. Thanks a lot.

Wound

---

### Post by Henrythewound on 2006-05-11
The command I entered then asked for the install CD, which I inserted. It failed to read the files from the disc. I'll try re-downloading the iso and burning a new copy tomorrow when I have access to fast internet, not the 56k I suffer with at home.

Thx,
Wound

---

### Post by Henrythewound on 2006-05-11
I think there is definitely a problem w/ my files on the CD, I get the following error when running sudo apt-get install gimp

Failed to fetch cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release amd64 (20051012)]/pool/main/g/gimp/gimp_2.2.8-2ubuntu6_amd64.deb  MD5Sum mismatch

It insists on reading from the CD, I wish there was a way to simply dl the newest version of gimp and install it

anyways, thought I'd post the error I get

---

### Post by louis_nichols on 2006-05-11
oh! I see. well, what you want to do is definitely possible. There is a simple way and... well, another simple way, but better in the long run. :) I'll explain this latter one

What you need to do first is indtruct your package manager to stop looking for packages on the CD. It's better if you download them from the web directly. It may take a while, on a slow connection, but you can just take care of business in the meantime. It's not worth downloading the whole ISO all over. So, issue this command in console:

```
sudo gedit /etc/apt/sources.list
```

In this file, probably at the begining, you'll find a line that begins with *deb cdrom:* and so on. You need to put a # in front of this line. This comments it out, so the next time you install something, the system will only search on the web. Now that you're there, uncomment all other lines that begin with deb and deb-src, so you'll have access to all package repositories. After this save the file and exit.

Next, issue in terminal the comand:
```
sudo apt-get update
```
This will refresh the info about available packages and versions from the repos. After this, you will just need to install gimp with:

```
sudo apt-get install gimp
```

If you haven't yet un-installed it (this will become obvious, cuz the previous command will return a message telling you this.), first run the command

```
sudo apt-get remove gimp
```

---

### Post by Sef on 2006-05-11
```
sudo apt-get install gimp
```

When installing software, it is better to use aptitude.  Easier to remove programs. if need be.

sudo aptitude install gimp

---

### Post by Sef on 2006-05-11
```
sudo apt-get remove gimp
```

For removing it, I would do this:

sudo apt-get --purge gimp

This will get rid of the configuration files as well.


```
sudo apt-get install gimp
```

When installing software, it is better to use aptitude.  Easier to remove programs. if need be.

sudo aptitude install gimp

---

### Post by louis_nichols on 2006-05-11
[QUOTE=Sef]

sudo apt-get --purge gimp

This will get rid of the configuration files as well.[/QUOTE]

I agree. it might be better, in the OP's case.

---

### Post by Henrythewound on 2006-05-11
Great advice, I thought about telling apt-get to not look at the install CD, but didn't know how to go about doing it. I will run these programs tonight and reply w/ the results. Thanks again everyone.

Joe aka Wound

---

### Post by Henrythewound on 2006-05-11
Sef and Louis, it worked beautifully, thank you very much:D . In the process I learned a bit about how things in ubuntu linux are configured, many thanks! I will now get going on gimping some of my pics. 

PS it only took 15 minutes to download gimp on my 56k

Joe aka Wound

---

