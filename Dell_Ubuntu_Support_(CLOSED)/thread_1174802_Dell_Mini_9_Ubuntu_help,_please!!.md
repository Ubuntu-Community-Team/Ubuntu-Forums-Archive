---
title: "Dell Mini 9 Ubuntu help, please!!"
date: 2009-05-31
forum: Dell Ubuntu Support (CLOSED)
---

### Post by karmaloop on 2009-05-31
Ubuntu Noob here!

Can any of you guys help me?  I upgraded my ubuntu on my Dell mini 9 the other day and it changed EVERYTHING.  It takes two minutes to upload my desktop and even then, not everything shows up (i.e. my desktop icons), everytime I log on, I have to enter in the password in order to connect to my wireless, my back button on my Mozilla webrowser doesnt work, also, my Youtube videos wont play.  How can I fix this?  I hope I dont have to reformat, AGAIN :(

---

### Post by Dex73 on 2009-05-31
As far as the videos go it sounds like you need the Linux plugins. They should come as a pop up when you click the video. See if that works.

For the password is a keyring request?

---

### Post by karmaloop on 2009-05-31
> **Dex73 said:**
> As far as the videos go it sounds like you need the Linux plugins. They should come as a pop up when you click the video. See if that works.

For the password is a keyring request?



nothing pops up when i try to play the videos :(  it'll play the first 5 seconds of the vid and then suddenly stop.  

sorry, whats a keyring?

thanks for answering my post!

---

### Post by Dex73 on 2009-05-31
What web browser do you use? And how are your preferences dealing with pop ups set?

The Keyring is a program that handles your passwords. If it's a keyring thing there should be a pop-up window (not a firefox pop-up) that is asking for the Keyring password.

---

### Post by Cowchip7 on 2009-05-31
> **karmaloop said:**
> Ubuntu Noob here!

Can any of you guys help me?  I upgraded my ubuntu on my Dell mini 9 the other day and it changed EVERYTHING.  It takes two minutes to upload my desktop and even then, not everything shows up (i.e. my desktop icons), everytime I log on, I have to enter in the password in order to connect to my wireless, my back button on my Mozilla webrowser doesnt work, also, my Youtube videos wont play.  How can I fix this?  I hope I dont have to reformat, AGAIN :(

What version of Ubuntu are you using?

---

### Post by ugm6hr on 2009-05-31
Do you have a 4GB HD?  If yes, I suspect your HD is full.

---

### Post by VipX1 on 2009-05-31
I changed my password:Login in the Passwords and Encryption Keys GUI. Now my Keyring to access the WIFI is different to the Login Password and I can't get into the Root in the Terminal using su - because it says my password is incorrect?? What is going on with Ubuntu and Passwords?

---

### Post by Dex73 on 2009-05-31
> **VipX1 said:**
> I changed my password:Login in the Passwords and Encryption Keys GUI. Now my Keyring to access the WIFI is different to the Login Password and I can't get into the Root in the Terminal using su - because it says my password is incorrect?? What is going on with Ubuntu and Passwords?

Ubuntu is very particular about passwords. I had the same password problem, there's a thread on how to fix the keyring (mine's set to no password so it can access WiFi automatically).

Try here   [http://ubuntuforums.org/showthread.php?t=1109736&highlight=change+keyring+password](http://ubuntuforums.org/showthread.php?t=1109736&highlight=change+keyring+password)

---

### Post by ranch hand on 2009-05-31
Have you checked to see if you have the restricted extras?  It really would be good to know what you are running and what you upgraded from.

Here is an article that everyone new to linux should read;

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

Here is a real good guide to setting up your Ubuntu box.  Replace "Jaunty" to whatever your version is if different;

[http://ubuntuguide.org/wiki/Ubuntu:Jaunty](http://ubuntuguide.org/wiki/Ubuntu:Jaunty)

---

### Post by Talon2 on 2009-06-01
You did not tell us what you upgraded from or what you upgraded to.  That information would be a good place to start.

I use 9.04 Netbook Remix on my Mini 9.  It works very well.  The original Ubuntu 8.04 that my Mini 9 came pre-loaded with had issues.

---

### Post by karmaloop on 2009-06-01
> **Dex73 said:**
> What web browser do you use? And how are your preferences dealing with pop ups set?

The Keyring is a program that handles your passwords. If it's a keyring thing there should be a pop-up window (not a firefox pop-up) that is asking for the Keyring password.

I use Mozilla as my web browser and my popups are turned off.

To connect to the internet, there is a window that pops up asking for a password, is that the keyring?

> **Cowchip7 said:**
> What version of Ubuntu are you using?

> **ugm6hr said:**
> Do you have a 4GB HD?  If yes, I suspect your HD is full.

Yes, I'm using a 4GB HD.  Ever since I upgraded my Linux, it said I ran out of disk space, so I deleted a bunch of files and nothing happens.  Could the hd being full be the reason why my laptop starts up so slow?


> **Talon2 said:**
> You did not tell us what you upgraded from or what you upgraded to.  That information would be a good place to start.

I use 9.04 Netbook Remix on my Mini 9.  It works very well.  The original Ubuntu 8.04 that my Mini 9 came pre-loaded with had issues.

How do I find out what version I uploaded onto my computer?  Where do I get the Remix? 




Thanks everyone!!

---

### Post by Cowchip7 on 2009-06-01
Open the terminal and type the following command: cat /etc/issue

The output should tell you what version of ubuntu you're running. Post the output here.

BTW, the terminal can be found in Applications > Accessories > Terminal.

---

### Post by Dex73 on 2009-06-01
Yes that's that sounds like the keyring. The link I posted should solve the problem. Just don't put in a new password and it should start up automatically.

[http://ubuntuforums.org/showthread.p...yring+password](http://ubuntuforums.org/showthread.p...yring+password)

---

### Post by karmaloop on 2009-06-02
> **Cowchip7 said:**
> Open the terminal and type the following command: cat /etc/issue

The output should tell you what version of ubuntu you're running. Post the output here.

BTW, the terminal can be found in Applications > Accessories > Terminal.



Is there something I should type in before that command?

---

### Post by Cowchip7 on 2009-06-02
> **karmaloop said:**
> Is there something I should type in before that command?

Nope. that is all you need.

cat /etc/issue

(Note the space between "cat" and "/etc/issue"

---

