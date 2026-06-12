---
title: "Could not open location 'file:///home/sedky69"
date: 2009-04-20
forum: General Help
---

### Post by sedky69 on 2009-04-20
Hello,
I get this error when I click anything "Home Folder" or "Desktop" under "Places"

I am new to Ubuntu. Any help is appreciated.

---

### Post by dragos240 on 2009-04-20
First thing's first, what ubuntu version do you have, ie did you download it last summer (doubtfull) or very recently, you probably have intrepid, try rebooting and booting up again. In my experience with hardy, this kept happening, also make sure that the files you have actually exist.

---

### Post by sedky69 on 2009-04-20
It is the latest version. 8.1 server I believe. I downloaded it and installed it last weekend. When I installed it, it installed in command line mode. I had to take a number of steps to get xwindow running. I am not sure what the visual environment is called.

I did restart a few times with the same results. 

Another problem that I have is at the login screen, the screen is messed up. I have to wait until I login and fix the resolution manually to the maximum the system allows me (800x600)

---

### Post by dragos240 on 2009-04-20
> **sedky69 said:**
> It is the latest version. 8.1 server I believe. I downloaded it and installed it last weekend. When I installed it, it installed in command line mode. I had to take a number of steps to get xwindow running. I am not sure what the visual environment is called.

I did restart a few times with the same results. 

Another problem that I have is at the login screen, the screen is messed up. I have to wait until I login and fix the resolution manually to the maximum the system allows me (800x600)

Hmm.... try installing graphics drivers, that will help. The login screen is pretty funny that way. And the virtual environment as you call is is GNOME (GNU network object model environment) so it's pronounced guh-nome. Also it would of saved you a lot of time and effort if you installed the desktop version, and if you wanted command line, then the alt-install would've worked.

---

### Post by sedky69 on 2009-04-20
My final goal is to use this at work. That is why I am experimenting with the server version. What about my original problem?

---

### Post by dragos240 on 2009-04-20
That is most likely caused by the manual install of X, and gnome. Not installing these correctly can easily result in errors like this.

---

### Post by Alterax on 2009-04-21
Hmmm...I have an idea!

If the username was created before the desktop environment was installed, then it's entirely possible that the user's home folders were created using the /etc/skel schema from the base install--which is to say without the standard folders of Desktop, Documents, Videos, Music, and Pictures.

Try this:  Log in with the terminal:

sudo mkdir -P /home/sedky69/Documents
sudo mkdir -P /home/sedky69/Videos
sudo mkdir -P /home/sedky69/Pictures
sudo mkdir -P /home/sedky69/Music
sudo mkdir -P /home/sedky69/Desktop
sudo chown -R sedky69:sedky69 /home/sedky69

This creates the folders as root (in case permissions aren't set properly)
then changes the ownership of your home directory and its contents to you.  If the directories exist, then it may error out, but your data will not be adversely affected.

Let me know if this works; I'll consider other options in the meantime.

---

