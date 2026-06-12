---
title: "Playing music in ubuntu 10.4"
date: 2010-08-02
forum: Desktop Environments
---

### Post by rahul_cse25 on 2010-08-02
I am very new to ubuntu.I have ubuntu 10.4 in my laptop,can anyone tell me how to play music in ubuntu,preferably music and video. Do i have to install something else or how to get started.

---

### Post by lykeion on 2010-08-02
Hi and welcome to Ubuntu,

Have you tried to double-click the music/video file?
This should launch the file with the deafult associated program.
Pre-installed programs for playing music/video in Ubuntu are Totem Movie Player and Rhythmbox, 
see **_[https://help.ubuntu.com/community/SoundVideoDefault](https://help.ubuntu.com/community/SoundVideoDefault)_**

Some music/video file formats are restricted by copyrights and patents (like MP3, QuickTime, Windows Media, Flash). 
To be able to play those you need to install a package called ubuntu-restricted-extras, 
see **_[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)_**

---

### Post by siabost on 2010-08-02
To add to lykeion's post, you can get ubuntu-restricted-extras from the Ubuntu Software Store from the Applications menu - it's right at the bottom.
Search for ***ubuntu-restricted-extras***and click install.

To play commercial DVDs you will need to go to the Medibuntu website [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) follow the instructions to ***Add A Repository***(copy/paste the relevant commands shown into your terminal as instructed).
After that enter the following command in Terminal window ```
sudo apt-get install libdvdcss2
``` You'll be asked for your password which you will have to type blind (it won't give you any indication that you are typing anything) and hit return.

Alternatively, you can go to System/Administration/Synaptic Package Manager, click Reload button (top left), search for libdvdcss2, tick it for installation, click Apply, click Mark (if it asks you to) & click Apply again.

Bob's your uncle! ;)

---

