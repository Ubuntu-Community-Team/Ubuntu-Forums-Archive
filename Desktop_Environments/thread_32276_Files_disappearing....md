---
title: "Files disappearing..."
date: 2005-05-06
forum: Desktop Environments
---

### Post by YourSurrogateGod on 2005-05-06
Ok, I have a couple of problems here...
1) The first and most important one is that some of my files are disappearing. I have a bunch of JPGs stored and every time that I right-click on them, one of them goes away :( . It literally vanishes! When I reboot my machine (or simply press "Up" and go back the desired directory or hit refresh), I see that it's there back, wtf? I'm guessing that Gnome doesn't like me.

2) Also, I have set it so that every time that I see the file, there would be a small clip of it shown up in the folder, it doesn't do this... Instead I see a small footprint (I'm guessing that this is the default file picture) and then a the name of the file.jpg. How can I set it so that I see a small clip of it and make sure that it stays that way?

3) I can't change my root password! I thought of changing it to something else so that it would be more difficult to crack. I did the "sudo passwd" and changed the password, but when I went to make sure that it has infact changed (such as going to Synaptic and trying the new password), it accepted only the old one :( . Any ideas why I'm having all of these problems?

---

### Post by enquiry on 2005-05-06
1. Your files aren't disappearing, it's just that they become "invisible" if you haven't got permission to read them. See command chmod and chown for how to change permissions and ownership.

2. I'm guessing this is 'cause of problem 1. (you haven't got permission to view the file/picture).

3. To change the root password write:
sudo passwd root
This doesn't apply if you haven't got a root user (which there isn't by default in Ubuntu).
The password for your user account you change by writing:
sudo passwd <username> (where <username> is your user).

---

### Post by nad on 2005-05-06
Are these 'disappearing' files stored on a vfat file system?

In order to change the 'emblem' associated with a particular mime type, you have to edit your theme. I read a thread here about that.

I assume you mean _your_ password, as sudo uses the sudo users password to access superuser functions. You have to log out and back in for your password change to take effect and don't forget to: sudo /etc/init.d/sudo restart .

---

### Post by YourSurrogateGod on 2005-05-06
[QUOTE=nad]Are these 'disappearing' files stored on a vfat file system?[/quote]
I don't follow. What's a vfat file system? How do I know that I have a vfat file system.
[quote=nad]In order to change the 'emblem' associated with a particular mime type, you have to edit your theme. I read a thread here about that.[/quote]
Yeh, I figured that. The problem was that I had the permissions screwed up. I'm still sometimes mentally in Windows land :) .
[quote=nad]I assume you mean _your_ password, as sudo uses the sudo users password to access superuser functions. You have to log out and back in for your password change to take effect and don't forget to: sudo /etc/init.d/sudo restart .[/QUOTE]
What does "sudo /etc/init.d/sudo restart" do?

---

### Post by YourSurrogateGod on 2005-05-06
Every time that I use Mozilla and would like to go to Gmail it says that the page can't be opened and that I need a Personal Security Manager? What's that?

---

### Post by nad on 2005-05-06
Sloooow down. Let's get the disappearing files corrected first (besides I haven't got a clue how to configure gmail).

Vfat is the M$ fat32 filesystem. The linux vfat driver does some pretty strange things depending on the case and size of a vfat file name.

sudo /etc/init.d/sudo restart  will reload your hopefully synchronized password files and allow you to continue to use sudo with your new password.

---

### Post by YourSurrogateGod on 2005-05-06
[QUOTE=nad]Sloooow down. Let's get the disappearing files corrected first (besides I haven't got a clue how to configure gmail).[/quote]
Actually that's fixed :) . I know where I messed up, I should have paid a more careful attention to the permissions when I set them :roll: .
[quote=nad]Vfat is the M$ fat32 filesystem. The linux vfat driver does some pretty strange things depending on the case and size of a vfat file name.[/quote]
I want to say that I have ext3. I remember something like that, albeit vageuly, when I installed Ubuntu.
[quote=nad]sudo /etc/init.d/sudo restart  will reload your hopefully synchronized password files and allow you to continue to use sudo with your new password.[/QUOTE]
Didn't seem to work, the new password doesn't do anything :( .

[edit]

FireFox works fine with GMail, but I tend to prefer Mozilla over the former, hence my Mozilla question.

---

### Post by crazybill on 2005-05-07
Remember that file names are case sensitive. This assumes the extension of your "missing" files are ".jpg" and not ".JPG"
[B]
sudo find / -name *.jpg -print[/B]

The reason for going into root is incase logged in as user, you may not have permission to view the files.

---

