---
title: "need help with .deb files"
date: 2009-02-25
forum: General Help
---

### Post by JR-XXL on 2009-02-25
I want to hello to everyone, this is my first post.
I apologize for sounding like a newbie. I am trying to make the switch over to linux on a file server. I installed server v 8.10 and since I am a newbie im not to sure of all the command to setup the file server. I saw a web base gui, so I downloaded the .deb package. "Here comes the question", where do i copy the file to on my linux server so that i can run.

sudo dpkg -i webmin_1.441_all.deb

thanks for the help....

---

### Post by JR-XXL on 2009-02-25
I forgot to mention that I dont have internet access on the server I am configuring, so I cant use the typical : apt-get install command.

---

### Post by Yashiro on 2009-02-25
You can put it anywhere. If you want the easy life put it in the home folder of the account you are on. If you're just using this machine as a file server with no web access, look into openfiler instead of ubuntu server.

---

### Post by taurus on 2009-02-25
You can save it anywhere you want in your $HOME.  Why not create a ~/temp and save all your downloads there.  Then, you need to change to whatever directory that you have saved that file before you run that command to install it.

---

### Post by smani on 2009-02-25
The command refers to the current directory, so say you downloaded the file to your Desktop, then you have to
```
cd ~/Desktop
```
and then you can execute the command.

---

### Post by lukjad on 2009-02-25
Copy it to your home folder at /home/[YourUsernameHere]

Edit: Sorry, I just realized that I hadn't refreshed this page before posting.

---

