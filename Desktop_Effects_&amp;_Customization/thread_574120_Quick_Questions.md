---
title: "Quick Questions"
date: 2007-10-12
forum: Desktop Effects &amp; Customization
---

### Post by Greatsteak on 2007-10-12
Hi all, 

First off, I am a complete Linux noob. I picked it up on a whim a few days ago and I am hooked now.  But as usual I have run into problems that have lead to new questions.

First off: While trying to install Compiz and Kiba Dock the HOWTO's have instructed me to edit the /etc/apt/sources.list and add a few lines to it. Ok, not a problem. I opened the correct file with a text editor and made the changes, but it won't allow me to save them.

Second: They tell me to "import the GPG key." What does this mean and how do I do it? Is it something inputed into CLI ?

Third and off topic: I have noticed that nothing in Linux comes with a nice installation executable. Does anyone know a tutorial I could read to learn more about the install and make commands?

Thanks in advance!

---

### Post by FuturePilot on 2007-10-12
To save the changes you need to open the file with root privileges. So open a terminal and put this into it.
```
gksudo gedit /etc/apt/sources.list
``` 
Then you will be able to save the changes.
As for the gpg key, there should be a somewhat long command that you need to paste into the terminal to import the key. All this means is that you trust the repo that you are adding. There should be the command in the guide you followed.
As for installing software, here's a nice explanation of the whole thing
[http://www.psychocats.net/ubuntu/installingsoftware]("http://www.psychocats.net/ubuntu/installingsoftware")

---

### Post by Greatsteak on 2007-10-12
Future Pilot,

Thank you very much for your quick and thorough response! Now, I just have to wait until I get home to try.

---

### Post by Greatsteak on 2007-10-12
I did some more reading and that psychocats.net site is excatly what I ahve been looking for!! You are my hero!

---

### Post by FuturePilot on 2007-10-12
No, problem. :) I've found a lot of useful information on that site. It actually belongs to aysiu who is a moderator here.

---

