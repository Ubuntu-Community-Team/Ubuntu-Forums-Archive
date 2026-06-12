---
title: "Administrator rights issues"
date: 2006-03-30
forum: Desktop Environments
---

### Post by sliverman69 on 2006-03-30
I installed Kubuntu this last week and while trying to install the driver for my soft modem I found out that I can't log in to the root user account, use sudo commands, or gain administrative rights to change settings.  I was wondering if there was something that I could do to fix this problem so I can install my soft modem software, netzero, and java.  Otherwise, I am going to try a fresh install.  It also won't let me access the package manager.

---

### Post by 5-HT on 2006-03-30
You didn't happen to do an 'expert install' did you?
I know that the expert install does not add the user you created during the install to the 'sudoers' file.

This file is what determines who can/can't use sudo, as well as what they can/can't use it for.

Even if you didn't perform the expert install, most likely your sudoers file is whats causing the problem.


Here is a great post from Mustard that describes how you can add your user to the sudoers file.
[http://ubuntuforums.org/showpost.php...70&postcount=4]("http://ubuntuforums.org/showpost.php?p=860170&postcount=4") 

(Original thread: [http://ubuntuforums.org/showthread.p...hlight=sudoers]("http://ubuntuforums.org/showthread.php?t=150021&highlight=sudoers"))

You basically need to boot into single user mode so you can become root, and then add your user to the sudoers file. Mustard's post is a great walkthrough of the process.

Hope this helps.

---

### Post by sliverman69 on 2006-03-30
no, I did not do an expert install that I am aware of.  I am pretty sure that I did not do an expert install if that is what I did, then I will just reinstall kubuntu, because I am getting a disc to keep from my friend because my Phillips DVD +RW 8631 burner is not working right and I am going to get dell to give me a new one because I have heard a lot of talk on the web about it not working properly and dell sending them a new drive. I just hope that they do not ask me to send it back because I opened the drive up (thereby voiding the warranty on it) after it stopped working properly.

---

### Post by 5-HT on 2006-03-31
Not to worry about the install, the link I provided should help you get 'sudo' rights for your user. If you have any problems just post back.
There shouldn't really be a need to reinstall unless lots of other issues are occuring.

Hope you get that drive replaced under warranty.

---

### Post by sliverman69 on 2006-04-16
i didn't have anything stored on the partition for linux so i just reinstalled and that fixed the problem.

---

