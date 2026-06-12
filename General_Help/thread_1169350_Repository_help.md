---
title: "Repository help"
date: 2009-05-25
forum: General Help
---

### Post by Sentience on 2009-05-25
Im having some trouble. I was trying to install medibuntu. I think I did something wrong and hit the wrong key after hitting aptitude, and maybe turned something off...I dont know. At one point I became root. 

Now its not letting me download updates or install new programs, and I still dont have medibuntu. 

Its saying failed to fetch, a web address...could not resove 'US.archive.ubuntu.com

How can I reset everything back to how it was then install medibuntu properly?

---

### Post by Kevbert on 2009-05-25
Can you still surf the web ? sounds like a network problem. If you can and are getting http 404 errors it may be that the US server is down or being updated. In that case go the System-Administration-Software Sources and change your server.

---

### Post by Sentience on 2009-05-25
Changing the server didnt seem to help. 

I am worried that I screwed something up by enabling the wrong source when trying to install medibuntu.

---

### Post by fballem on 2009-05-25
Please select System > Administration > Software Sources.

You should get a screen like Screenshot-Software Sources-1. You can change your server on this screen.

If you select the Third-Party Software tab you should get a screen like Screenshot-Software Sources-2. To remove a repository, click on it to select it, then click on the remove button. In the screenshot, there are two Medibuntu repositories, so if I wanted to remove them, I would select and remove each one.

If you select the Authentication tab you should get a screen like Screenshot-Software Sources-3. To remove a key, click on it to select it, then click on the remove button.

When you are done, select the Close button. You will get a message to update the software lists, which you should do. Once this is done, please reboot your machine.

Once you have rebooted and logged back in, please open a terminal and cut and paste the following code into the terminal:

```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update
```

This will add the correct entries for medibuntu back into your software sources.

Hope this helps,

---

### Post by Sentience on 2009-05-25
I think I discovered the problem. It wouldnt let me download anything from any server while I was using my bittorent client. Is that odd?

---

### Post by Sentience on 2009-05-25
Sorry about being a noob.


Is it a problem that under third party sources some of them say Hardy Haron and some of them say Jaunty Jacalope? 

I honestly dont know which one this computer is running right now. 


It says....

CDRom with Ubuntu 8.4 Hardy Heron
Unsuported updates
Archive....Jaunty partner
archive... jaunty partner (source code)

---

### Post by fballem on 2009-05-25
> **Sentience said:**
> Sorry about being a noob.


Is it a problem that under third party sources some of them say Hardy Haron and some of them say Jaunty Jacalope? 

I honestly dont know which one this computer is running right now. 


It says....

CDRom with Ubuntu 8.4 Hardy Heron
Unsuported updates
Archive....Jaunty partner
archive... jaunty partner (source code)

I've heard that upgrading from one release to another can cause problems. I have always done a clean install with each new version and that seems to work very well. The reason that I say this is that your issue may be related to the 'mixed repositories'. You may want to consider doing a fresh install - after backing up your data to an external drive.

---

### Post by Sentience on 2009-05-25
I seem to be having a problem installing a fresh copy of Ubuntu over my previously partitioned Ubuntu. It wants to create a whole new OS separately.

I really dont want to have to reinstall Windows as well as Ubuntu. I dont even know if I have the code for windows anymore.

I tried it with a Hardy Disk. I could try again with a Jaunty disk....What am I doing wrong?

---

### Post by Kevbert on 2009-05-26
You probably just want an upgrade. Have a look at [this]("http://www.ubuntu.com/getubuntu/upgrading"). To perform a CD upgrade, scroll down, you need the alternate CD.

---

