---
title: "su: authentication failure during java install"
date: 2009-04-29
forum: General Help
---

### Post by Lateralus138 on 2009-04-29
Ok, I am not sure where to post this as I am completly new to Ubuntu and I don't know what the problem involves... I have just installed Ubuntu for the very first time on a second hard drive and on my other I have Vista 64bit. I know a great deal about Windows, but I don't know anything at all about Ubuntu, I hav ebarely learned how to find things like the terminal and how to change the appearance etc... I tried to install java for Firefox so that my mom can play on Pogo.com, but when I started learning how to install it I was told to go to the terminal and enter "su" (without quotations) and then enter my password. I have only made one password and that is when I installed the system so I entered that and it said "Authentiction failure" or failed or something to that effect. I have not changed any settings since I installed. I know a great deal about using a console like cmd/dos, so I understand the concept of using this terminal I just don't know any commands or what they do. Please help! lol

---

### Post by _Purple_ on 2009-04-29
Use sudo instead of su. To install any package 
```
sudo apt-get install packagename
```

It will ask for your password. Enter the password for the first user that you have created. In Ubuntu, root account is not enabled by default and it is not a good idea to enable it. su is used to login as root. sudo gives you the privileges of root for a limited time using the password of your first user account.

For more details you can check
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Lateralus138 on 2009-04-29
> **_Purple_ said:**
> Use sudo instead of su. To install any package 
```
sudo apt-get install packagename
```

It will ask for your password. Enter the password for the first user that you have created. In Ubuntu, root account is not enabled by default and it is not a good idea to enable it. su is used to login as root. sudo gives you the privileges of root for a limited time using the password of your first user account.

For more details you can check
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
Thank you very much, I have seen that sudo, but I would hav efigured that the java instructions would hav mentioned it. Thank you for your help... I wil be here alot for a while, lol.

---

### Post by Lateralus138 on 2009-04-29
When I put the app name do I also put what folder it is in? When I typed what all that in it said it could not find the app. I just found this: sudo apt-get install sun-java5-jdk ,,,,, is it ok to use? This is the new problem I get: 
ian@ian-Linux:~$ sudo apt-get install jre-6u13-linux-x64.bin
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
Update: ok, now I have fixed that and it resorts back to the package not found.

---

### Post by _Purple_ on 2009-04-30
Run the following command in terminal
```
sudo apt-get install sun-java6-jre sun-java6-bin sun-java6-plugin
```

---

### Post by Lateralus138 on 2009-04-30
> **_Purple_ said:**
> Run the following command in terminal
```
sudo apt-get install sun-java6-jre sun-java6-bin sun-java6-plugin
```
Alright, thanx it is working. May I ask what these commands are doing exactly. I have leaqrned enough to know that sudo is giving temporary time admin like authorization and I can assume what install is (self explanatory, but what does the apt-get do and why do those three files not have extensions? ANd also what is the difference between the "sudo apt-get install jre-6u13-linux-x64.bin" and the one you just gave me?  I would appreciate it. ANd also when that thing gets done running will it pop up with my name agaain like this: 
ian@ian-Linux:~$

---

### Post by _Purple_ on 2009-04-30
apt-get is the command-line tool for handling packages. When installing packages using apt-get, you do not have to give the package extension- only the package name. You were trying to install a .bin file. It is easier to install using apt-get. For more details, type the following command and scroll down to install
```
man apt-get
```
Once the installation is complete, you can type again in the same terminal window.

---

### Post by Lateralus138 on 2009-04-30
> **_Purple_ said:**
> apt-get is the command-line tool for handling packages. When installing packages using apt-get, you do not have to give the package extension- only the package name. You were trying to install a .bin file. It is easier to install using apt-get. For more details, type the following command and scroll down to install
```
man apt-get
```
Once the installation is complete, you can type again in the same terminal window.
Awesome, thanx for your help.

---

### Post by SuperSonic4 on 2009-04-30
su is mentioned because in nearly every other distro typing su will give you a root shell until such a time as you exit whereas sudo gives root for that one command. Su is linked to the root account since you put in *root's* password whereas sudo uses the sudoers file and the user's password. Ubuntu is actually pretty unique in disabling the root account :p

---

### Post by Monotoko on 2009-04-30
If you need the root account for multiple commands, just run

```
sudo su
```

---

### Post by Lateralus138 on 2009-04-30
> **Monotoko said:**
> If you need the root account for multiple commands, just run

```
sudo su
```

Thanx all, I also learned the "sudo -i" and "sudo nautilus". I like Ubuntu, but I don't like these restrictions. I know they are there to keep me from screwing things up and to protect me, but it is more of an annoyance than anything else.

---

### Post by _Purple_ on 2009-04-30
When opening graphical applications, it is better to use gksudo instead of sudo.

```
gksudo nautilus
```

---

### Post by Lateralus138 on 2009-04-30
> **_Purple_ said:**
> When opening graphical applications, it is better to use gksudo instead of sudo.

```
gksudo nautilus
```

Ok thank you, that is helpful. I started watching an avi movie and it crashed my system, is there way to watxh movie in Ubuntu?

---

### Post by _Purple_ on 2009-04-30
You can try Totem Movie player(Applications > Sound & Video > Movie Player) or VLC player.

To install VLC
```
sudo apt-get install vlc
```

---

### Post by Lateralus138 on 2009-04-30
> **_Purple_ said:**
> You can try Totem Movie player(Applications > Sound & Video > Movie Player) or VLC player.

To install VLC
```
sudo apt-get install vlc
```

Ah, thank you.... actually the normal movie player is what crashed my system.... (Applications > Sound & Video > Movie Player). Ok it all works now, thanx.

---

