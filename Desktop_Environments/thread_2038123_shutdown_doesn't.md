---
title: "shutdown doesn't"
date: 2012-08-05
forum: Desktop Environments
---

### Post by MichaelEber on 2012-08-05
I have a clean build of 12.04 LTS 64 bit running Unity.  
I have an HP EliteBook 8740W with 8 processors, 8G memory, 312G hard drive.
When I click the shutdown button I get the typical message
(want to shutdown?)

I click shutdown (not restart) and at first it looks like it is shutting down.  The screen goes black then there is a sound played that sounds like a drum roll.

Next the login screen pops up. 

If I try shutdown from here nothing at all happens.

The only way to shut down the system is hold in the power button for 10 seconds.

I have Avast! installed and running on the system as well.  Don't know if that is part of the problem or not.

I have found this to happen on the 32 bit version as well.

---

### Post by PinguyOS on 2012-08-06
Try using this command
```

sudo poweroff

```
If it works you can create a script.
Using gedit create a text file which contains the following command:
```

gksu poweroff

```
Save it on your desktop as a .sh file.
Open a terminal and type:
```

cd ~/Desktop
chmod +x your_file.sh

```
Now you can double click the file you created to shutdown the pc!

---

### Post by MichaelEber on 2012-08-06
all this command line crap is why I stayed away from linux.
I'm posting this to bring to the attention of Ubuntu developers.
(unless there is a different place to post bugs)

With that said, the next time things fail I will try the sudo poweroff command.

---

### Post by PinguyOS on 2012-08-07
Yes, there is place to post bugs. If you google you will find!
If you want a better solution to the problem you can install another desktop environment. I suggest XFCE. It's more stable than KDE Unity Gnome.

If you do not want to use command line you can install it via software center. Just search and install Xubuntu or xfce! After that logout and choose xfce or xubuntu at the login screen!
Hope this helps!

---

### Post by efflandt on 2012-08-08
Your issue is not something that most of use are experiencing, so it may be difficult to find someone who had that problem and resolved it.

It sure sounds like you (or something in your system, maybe specific to your hardware) is doing **logout** instead of **shutdown**.  Logout would go back to the login prompt.


Does your system properly shut down when you do it the old fashioned way from a terminal:

```
sudo shutdown -h now
```

---

### Post by Buntu Bunny on 2012-08-11
> **MichaelEber said:**
> I have a clean build of 12.04 LTS 64 bit running Unity. ...When I click the shutdown button I get the typical message(want to shutdown?)

I click shutdown (not restart) and at first it looks like it is shutting down.  The screen goes black ... Next the login screen pops up. If I try shutdown from here nothing at all happens.

The only way to shut down the system is hold in the power button for 10 seconds.

I am having the same problem but it didn't start until after I installed Cinnamon. Previously I installed the Gnome desktop options but liked what I read about Cinnamon and wanted to try it. Since then must force a shutdown like you.

---

### Post by Buntu Bunny on 2012-08-12
Last night the computer shut down from the menu. Prior, it would not. The difference was that I usually I have other family member signed into their user accounts. Yesterday I was the only one. In Lucid, the administrator could shut down the computer even if other users were signed in. Just wondering if that option was  removed with Precise(?)

---

