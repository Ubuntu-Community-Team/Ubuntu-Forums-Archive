---
title: "Receiving errors when install software"
date: 2017-05-26
forum: Debian
---

### Post by RobGoss on 2017-05-26
Hello everyone, I've been playing around with** Debian 8** and have one issue, After installing it all seem to run ok but when I tried installing software I get this error message

```
 Please insert the disk labeled:
Debian GNU/Linux 8.8.0 _Jessie_ - Official amd64 DVD Binary-1 20170506-14:13
in drive /media/cdrom/

```


After doing some research I read that I have to remove the **cdrom:** from my source list, I am trying to do this using **Gedit**
I was able to remove the sections that needed to be removed but after that I cannot save the changes

This is my source list

```

# 

# deb cdrom:[Debian GNU/Linux 8.8.0 _Jessie_ - Official amd64 DVD Binary-1 20170506-14:13]/ jessie contrib main

deb cdrom:[Debian GNU/Linux 8.8.0 _Jessie_ - Official amd64 DVD Binary-1 20170506-14:13]/ jessie contrib main

deb http://ftp.us.debian.org/debian/ jessie main
deb-src http://ftp.us.debian.org/debian/ jessie main

deb http://security.debian.org/ jessie/updates main contrib
deb-src http://security.debian.org/ jessie/updates main contrib

# jessie-updates, previously known as 'volatile'
deb http://ftp.us.debian.org/debian/ jessie-updates main contrib
deb-src http://ftp.us.debian.org/debian/ jessie-updates main contrib

```


I understand I have to remove  **cdrom:** from the first two listed but do I need to replace it with another resource list there. I cannot install any software when I try

Thanks so much

---

### Post by Dennis N on 2017-05-26
Did you elevate to root privileges? You need to do that to save your changes.

---

### Post by #&amp;thj^% on 2017-05-26
> **RobGoss said:**
> Hello everyone, I've been playing around with** Debian 8** and have one issue, After installing it all seem to run ok but when I tried installing software I get this error message

```
 Please insert the disk labeled:
Debian GNU/Linux 8.8.0 _Jessie_ - Official amd64 DVD Binary-1 20170506-14:13
in drive /media/cdrom/

```


After doing some research I read that I have to remove the **cdrom:** from my source list, I am trying to do this using **Gedit**
I was able to remove the sections that needed to be removed but after that I cannot save the changes

This is my source list

```

# 

# deb cdrom:[Debian GNU/Linux 8.8.0 _Jessie_ - Official amd64 DVD Binary-1 20170506-14:13]/ jessie contrib main

deb cdrom:[Debian GNU/Linux 8.8.0 _Jessie_ - Official amd64 DVD Binary-1 20170506-14:13]/ jessie contrib main

deb http://ftp.us.debian.org/debian/ jessie main
deb-src http://ftp.us.debian.org/debian/ jessie main

deb http://security.debian.org/ jessie/updates main contrib
deb-src http://security.debian.org/ jessie/updates main contrib

# jessie-updates, previously known as 'volatile'
deb http://ftp.us.debian.org/debian/ jessie-updates main contrib
deb-src http://ftp.us.debian.org/debian/ jessie-updates main contrib

```


I understand I have to remove  **cdrom:** from the first two listed but do I need to replace it with another resource list there. I cannot install any software when I try

Thanks so much

Coment out this line in your /etc/apt/source.list
```
deb cdrom:[Debian GNU/Linux 8.8.0 _Jessie_ - Official amd64 DVD Binary-1 20170506-14:13]/ jessie contrib main
```
So it looks like the first Via;
```
# deb cdrom:[Debian GNU/Linux 8.8.0 _Jessie_ - Official amd64 DVD Binary-1 20170506-14:13]/ jessie contrib main
```

---

### Post by RobGoss on 2017-05-26
> **Dennis N said:**
> Did you elevate to root privileges? You need to do that to save your changes.

Hello Dennis N, How would I do that? I tried the following, **su -**

Thanks so much

---

### Post by RobGoss on 2017-05-26
**1 Fallen**, Yes I'm trying to make the changes but having trouble editing the source.list

---

### Post by #&amp;thj^% on 2017-05-26
What is your text editor?

---

### Post by RobGoss on 2017-05-26
> **1fallen said:**
> What is your text editor?

I'm using **gedit** with Debian

---

### Post by #&amp;thj^% on 2017-05-26
> **RobGoss said:**
> I'm using **gedit** with Debian

Cool throw this in the terminal:
```
sudo -H gedit /etc/apt/sources.list
```
Now while your there you may as well add the non-free repo's as well.
Add these two lines.
```
deb http://security.debian.org/ jessie/updates main contrib non-free
deb-src http://security.debian.org/ jessie/updates main contrib non-free

###Also add the following line underneath the lines displayed above:###

deb http://http.us.debian.org/debian jessie main contrib non-free

```

Once configured, your re-configured source lines should look as follows:

```
# deb cdrom:[Debian GNU/Linux 8 _Jessie_...
# deb cdrom:[Debian GNU/Linux 8 _Jessie_...
deb http://security.debian.org/ jessie/updates main contrib non-free
deb-src http://security.debian.org/ jessie/updates main contrib non-free
deb http://http.us.debian.org/debian jessie main contrib non-free
```

---

### Post by howefield on 2017-05-26
Just mentioning that ...

```
sudo apt edit-sources
```

will probably work as well. This would open your sources.list giving a choice of editors but uses nano by default.

---

### Post by Dennis N on 2017-05-26
Yep. that ^ should work. I rarely run a GUI app like gedit as root. As an alternative, I would have suggested:

```
sudo nano /etc/apt/sources.list
```

when done, CTRL+O to save, CTRL+X to quit.

---

### Post by RobGoss on 2017-05-26
I tried a few suggestions but can't get it to save the changes

When I run, **sudo nano /etc/apt/sources.list** I get the following below

```
bash: sudo: command not found

```

---

### Post by #&amp;thj^% on 2017-05-26
> **RobGoss said:**
> I tried a few suggestions but can't get it to save the changes

When I run, sudo nano /etc/apt/sources.listIi get the following below

```
bash: sudo: command not found

```

Open the Terminal
    - Click "Activities"
    - Click in the "Type to search..." box
    - Type in "Terminal" and press the [enter] key

Switch to root user
    - Type in the Terminal the following command
       ```
 su
```
    - then press [enter]
    - now type in the root password and press [enter]
        - The command prompt should now look like this...
            root@debian:/home/yourusernamehere#
    
Install "sudo"
    - Now that you are root user within the Terminal lets install "sudo"
    - Type in the following command...
        ```
apt-get install sudo
```
    - then press [enter]

Add your username to the sudo group
    - Type in the following command...
       ```
 adduser yourusernamehere sudo
```
    - then press [enter]
    
Now add your name to /etc/sudoers file
    - Type in the following command...
      ```
  nano /etc/sudoers
```
    - then press [enter]
    - Scroll down and look for the line "%sudo  ALL=(ALL:ALL) ALL"
    - Below that line type in the following...
       ```
 yourusernamehere  ALL=(ALL:ALL) ALL
```
    - Press "Ctrl+x" then press "y" and then press [enter] to exit and save the file
    
Now we exit out of the Terminal completely
    - Type in the following command...
     ```
   exit
```
    - then press [enter]
    - Type exit again...
       ```
 exit
```
    - then press [enter]
    - That should have closed the Terminal application 
    
Now let's open a new Terminal and test to see if sudo is working for your user name.
BTW I forgot to mention here you colud also just use "su" instead of "sudo"
So if you dont want to add sudo just use "su -"

---

### Post by RobGoss on 2017-05-26
Is there anyway Debian works right out of the box with out all the mods just to get software installed?

Thanks so much and I do appreciate all the suggestions

---

### Post by #&amp;thj^% on 2017-05-26
> **RobGoss said:**
> Is there anyway Debian works right out of the box with all the mods just to get software installed?

Thanks so much and I do appreciate all the suggestions

Ha! You've been spoiled by Ubuntu....Makes you a bit more Appreciative dose'nt it.;)
BTW: Just an FYI, debian will install sudo during installation if you do not specify a root password when prompted.

---

### Post by RobGoss on 2017-05-26
>   Ha! You've been spoiled by Ubuntu....Makes you a bit more Appreciative dose'nt it  

Ha ha you bet ya, LOL

I've always been wondering about Debian but never like the installation process so I decided to give it a try, I got it all installed on a external drive and surprising it's really fast, but I have this little problem with installing software...I still love Ubuntu


>  BTW: Just an FYI, debian will install sudo during installation if you do not specify a root password when prompted   

If I do this will I bypass this problem?

Thanks so much

---

### Post by #&amp;thj^% on 2017-05-26
> **RobGoss said:**
> Ha ha you bet ya, LOL

I've always been wondering about Debian but never like the installation process so I decided to give it a try, I got it all installed on a external drive and surprising it's really fast, but I have this little problem with installing software...I still love Ubuntu




If I do this will I bypass this problem?

Thanks so much

Yes, but you don't need to if you will just use **"su" or "su -" **when needed instead of 'sudo'.

---

### Post by Dennis N on 2017-05-26
Interesting stuff I didn't know about Debian! I for one will steer clear of it.

---

### Post by RobGoss on 2017-05-27
> **Dennis N said:**
> Interesting stuff I didn't know about Debian! I for one will steer clear of it.

May I ask why? It seems to run on this external drive I have faster then anything else I have on my desktops so I decided to give it a shot but for the life of me can't get it to install any new software

---

### Post by RobGoss on 2017-05-27
> **1fallen said:**
> Yes, but you don't need to if you will just use **"su" or "su -" **when needed instead of 'sudo'.

I was able to make changes and saved them but when I tried to install software I get the same error, so I look in the folder were the sources.list is located and there are two files with the same EXT only one of those files has **save** at the end, **sources.list.save** and that's the file were the changes are. I tried to rename it and was unable to

This is what the file looks like now

```
# 

# deb http://security.debian.org/ jessie/updates main contrib non-free
deb-src http://security.debian.org/ jessie/updates main contrib non-free
deb http://http.us.debian.org/debian jessie main contrib non-free

deb http://ftp.us.debian.org/debian/ jessie main
deb-src http://ftp.us.debian.org/debian/ jessie main

deb http://security.debian.org/ jessie/updates main contrib
deb-src http://security.debian.org/ jessie/updates main contrib

# jessie-updates, previously known as 'volatile'
deb http://ftp.us.debian.org/debian/ jessie-updates main contrib
deb-src http://ftp.us.debian.org/debian/ jessie-updates main contrib

```

---

### Post by Dennis N on 2017-05-27
> **RobGoss said:**
> May I ask why? It seems to run on this external drive I have faster then anything else I have on my desktops so I decided to give it a shot ...

I've never used Debian, but Ubuntu is based on it, so I expect the experience should be very similar - after all, you have the same package management and it has the same packages and Desktop environments available. There would have to be a compelling reason to use it except in a trial run.

By analogy, maybe Ubuntu is to Debian as Korora is to Fedora and Manjaro is to Arch. In each comparison, the first is more user-friendly out of the box. I'm all for user-friendly.

For lightness and speed I would go with Lubuntu which has a great release for 17.04. I use it on my old laptop.

---

### Post by RobGoss on 2017-05-27
Yes Dennis N, I would have to agree, but even tho it's based off of Ubuntu there's noting easy about setting things up, Why would the developers make it so complex for installation. I mean I can get it installed but this error has made me not like it right from the start not being able to at least use the desktop as it was meant to be used 

No matter what desktop environment I install it stops here with this error.....  I don't mind working hard to get things running but when I go to the extra mile I expect things to run

I'm always trying different distributions just to see what options I have..


>   For lightness and speed I would go with Lubuntu which has a great release for 17.04. I use it on my old laptop.   

Yes I have it already installed it on one of my testing machines works very good

---

### Post by Dennis N on 2017-05-27
> **RobGoss said:**
> ...I look in the folder were the sources.list is located and there are two files with the same EXT only one of those files has **save** at the end, **sources.list.save** and that's the file were the changes are. I tried to rename it and was unable to.


Your computer is going to look at sources.list and sources.list.d when checking for updates. I would not change sources.list.save

On my computer, looks like sources.list.save is a backup of the previous version of sources.list when you change and save sources.list (or change the software sources through another method). If you made multiple saves, then each may create a new copy of that backup, so your changes could appear there too if you did more than one save. Note sources.list does not have PPAs - at least on my 17.04 - those are in a separate folder, sources.list.d.

Alternate ways: You can also disable the CD rom source from Synaptic Package Manager by un-checking it under Settings > Repositories > Other Software; or use the "Software and Updates" tool which has the same dialog.

---

### Post by RobGoss on 2017-05-27
>   Alternate ways: You can also disable the CD rom source from Synaptic Package Manager by un-checking it under Settings > Repositories > Other Software; or use the "Software and Updates" tool which has the same dialog. 

You nailed it Dennis N, that worked like a charm after doing this I am able to install software with out having to jump threw hoops. I knew there must have been a easier method... Thank you so much for sharing your wisdom with me, you to **1Fallen **


**NOTE:** I also have a Dell Optiplex 755, and I tried installing Debian on it but for some reason it does not run as smooth it has about 3-GB of Ram, I would have to see what the graphic card is, any suggestions or should I open up a new thread..

Thank you guys so much

---

### Post by #&amp;thj^% on 2017-05-27
Sorry late for the party...But looks like your in good hands with [COLOR=#000000]Dennis N. :D
Very glad you got sorted out,  Happy Debian-ing...;)[/COLOR]

---

