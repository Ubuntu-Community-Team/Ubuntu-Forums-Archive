---
title: "just want a simple file server"
date: 2012-05-01
forum: Desktop Environments
---

### Post by sartan on 2012-05-01
hi ubuntu forum, im so new to linux/ubuntu,so new i still have the shiny plastic wrap on, i want to set up a simple file server on ubuntu 12 desktop x64. my goal = one big shared public folder for my windows pc`s to back upto, Lan only.

my ubuntu desktop spec
[LIST]
[*]dual core
[*]6gb ram
[*]4 x 1tb hdd`s, including ubuntu install
[*]1 x ethernet connection dhcp handled by router
[/LIST]

my problem is me im clueless please help.
any help/suggestions will be gratefully received. many thx in advance

---

### Post by mangan on 2012-05-01
Hi, and welcome to the world! I very recently set up a file server (and I'm extremely proud to say it was my first command-line endeavor...ever!). It wasn't difficult at all, and you don't HAVE to do it all by command line if you don't want.

Depending on your comfort level with networking in general, it's a walk in the park.

The first thing you'll want to is set up your server with a static IP address. This can prevent headaches later on...imagine trying to send your friend an email, but his address keeps changing. A Static IP will mean your other machines will always be able to "find" your server. [Follow the steps in this link to do so]("http://www.liberiangeek.net/2012/04/setup-a-permanent-static-ip-address-in-ubuntu-12-04-precise-pangolin/")

Then, make sure to install Samba. Windows in general uses a protocol called SMB to communicate, and Ubuntu speaks the language very well.

[This link here appears to be a fantastic guide with screenshots of configuration on both the Ubuntu side as well as the Windows side of things.]("http://rbgeek.wordpress.com/2012/04/25/how-to-install-samba-server-on-ubuntu-12-04/") Warning: There's some command line here, but feel free to post with any questions.

And that's pretty much it for file server. If you have any other questions, post them here. I'm still pretty new to this but between myself and all the others here on the forums, you'll have plenty of guidance.

Edit: Just saw your username! I'm currently re-reading the Death's Gate Cycle, what are the odds?

---

### Post by Morbius1 on 2012-05-01
Since you are using the desktop version of Ubuntu, a slightly easier method on the Ubuntu end is to open up Nautilus, right click a folder in your home directory and select "sharing options" then click on all the options. The whole process has the look and feel of creating a "Simple Share" in WinXP.

If you don't have samba installed it will install the appropriate version for you. Then run the following command and see if the samba client on your machine can see the samba server on your machine:
```
smbtree
```

You can then move on to share other folders once you get the basics ironed out.

---

### Post by lukeiamyourfather on 2012-05-01
Another good option besides Ubuntu would be FreeNAS. It allows administration through a web interface and advanced features can be setup fairly easily compared to configuring them manually with a distribution like Ubuntu.

[http://www.freenas.org/](http://www.freenas.org/)

The advantage of using Ubuntu is it could fulfill other purposes besides serving files. If you go the Ubuntu route and want to know more about setting up a server be sure to check out the Ubuntu Server Guide.

[https://help.ubuntu.com/12.04/serverguide/index.html](https://help.ubuntu.com/12.04/serverguide/index.html)

---

### Post by sartan on 2012-05-01
thank you, mangan and morbius1, i have now shared the public folder via samba which gives me 900gb ish how do i go about adding the other 3 x hdds to the same share eg. make public folder 3.9tb in size and able to handle my backup images which will be over 1.2tb each ? is this a raid thing or something else .
your help has been great and i hope i can contribute to the forum in the future. thx again

---

### Post by sartan on 2012-05-01
thank you, mangan and morbius1, i have now shared the public folder via samba which gives me 900gb ish how do i go about adding the other 3 x hdds to the same share eg. make public folder 3.9tb in size and able to handle my backup images which will be over 1.2tb each ? is this a raid thing or something else .
your help has been great and i hope i can contribute to the forum in the future. thx again

---

### Post by sartan on 2012-05-01
i have tried freenas but it will not work with my hardware as it would of been an idea solution to my basic needs and with in built drive pooling, if only it had worked. but i like ubuntu alot from the short time i have been using it 2 days so far, im hoping i can get it running headless as i will only need it 2 days a week for backing up
thx

---

### Post by markbl on 2012-05-01
I often see people sending newbies off to instructions to "apt-get install samba", then configure "/etc/samba/cmb.conf", etc.

None of that is needed for simple file sharing. You don't even need to use a terminal. Just create or select a folder somewhere then right click on it and select the "Sharing Options". Anything needed from then (including samba) will be automatically installed.

---

### Post by mangan on 2012-05-01
> **markbl said:**
> I often see people sending newbies off to instructions to "apt-get install samba", then configure "/etc/samba/cmb.conf", etc.

None of that is needed for simple file sharing. You don't even need to use a terminal. Just create or select a folder somewhere then right click on it and select the "Sharing Options". Anything needed from then (including samba) will be automatically installed.

That's a good call. I answered from my experience, which was entirely command prompt. Looks like Morbius1 chimed in with the simpler answer as you said.

Sartan, to answer your latest question, I recently heard about a great way to do this called LVM. I haven't used it myself but you might do a little searching about it, maybe somebody else can chime in with more info.

---

### Post by sartan on 2012-05-02
Thank you all for posting help, using right click to share and install samba for folder or drive is spot on, and lvm does seem to be the answer for drive pooling,I have found a tutorial on how to install lvm during Ubuntu install as it is not an install option for the desktop only server I will post the tutorial and the result later today,I did experiment with lvm for server but there was to much command line and as I don't understand Ubuntu yet I could not get it to work. Thx again for all your input.

---

### Post by sartan on 2012-05-08
hi all, found an easy way of seting up a basic file server, download ubuntu desktop 12 from the alternate download link as this has LVM as part of the installer then when you get to the desktop use disk utility to add any reading drives to the lvm that was created a install then create the folder to share and or right click the folder to share and install samba for Windows network sharing. job done the not going I have to try and sort out is vnc desktop share to Windows

---

