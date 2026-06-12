---
title: "Trying to get Minecraft to run on Xubuntu 11.10"
date: 2011-11-05
forum: Gaming &amp; Leisure
---

### Post by JordyBoyy on 2011-11-05
Hey Everyone,

I've recently updated my machine to Xubuntu 11.10 and am wanting to try and play Minecraft on it, since it's supported on Linux. I have downloaded the .jar file from the official website and when I try to open the file it says "The file '/home/user/Documents/minecraft.jar' is not marked as executable. If this was downloaded or copied from an untrusted source, it may be dangerous to run. For more details, read about executable bit."

I have tried going into properties and then going onto permissions to mark it as an executable like you do on Ubuntu 11.10, but it doesn't even show up.

So if someone could help me with this issue I'd be really happy.

Thanks,
JordyBoyy

---

### Post by bud986 on 2011-11-05
Try this installer script, [http://www.minecraftforum.net/topic/250945-install-ubuntu-minecraft-installer-update-20/]("http://www.minecraftforum.net/topic/250945-install-ubuntu-minecraft-installer-update-20/")
Otherwise running minecraft is as running any other .jar on linux install java and run them with the following command java -jar filename.jar
Or mark them as executables.

---

### Post by JordyBoyy on 2011-11-05
@bud982 Thanks for that, I'll try out that Minecraft installer script and if it doesn't work I'll do what you said and install Java and enter the command for it to see if that works instead.

---

### Post by Rubykuby on 2011-11-05
sudo chmod a+x /path/to/file 

that should make it executable

---

### Post by JordyBoyy on 2011-11-05
**@bud982** I managed to successfully install Minecraft and played it using
 the install script, but there was a slight problem that the desktop disapeared 
and only displayed the log-on screen. but I managed to fix it by un-installing it 
and managed to make the desktop come back.

I wonder if it's because of the old hardware I'm currently using, or is it the
software or Java playing up? I might just have to troubleshoot it on the homepage
and see if there's a way around it.

[B]
@Rubykuby[/B] I tried using the sudo chmod a+x /path/to/file, but it said the directory
didn't exist, so I'm wondering if I typed it in wrong or something, but I definitely double
checked to see if it was just me or not. I might have to give that another go.

---

### Post by bud986 on 2011-11-05
That sounds like a really wierd problem >S I used a script before and had no problems :)

---

### Post by Rubykuby on 2011-11-06
> **JordyBoyy said:**
> 
[B]
@Rubykuby[/B] I tried using the sudo chmod a+x /path/to/file, but it said the directory
didn't exist, so I'm wondering if I typed it in wrong or something, but I definitely double
checked to see if it was just me or not. I might have to give that another go.
Linux is case-sensitive. If it's in your Documents folder, where I keep minecraft, the command will look like *sudo chmod a+x /home/yourusernamehere/Documents/minecraft.jar*

Also, do you have an ATI graphics card? If yes, this may cause some problems with java. The problems can be worked around, but I'm a bit reluctant in putting it out there as I had to do a fresh install after a failed attempt to fix it.

---

### Post by ctrlaltnarwhal on 2012-11-25
Hey if anyone is still interested I reworked the installer to eliminate graphics issues. Also the hosting for minecraft.jar needed to be changed. The desktop shortcut is no longer installed but [FONT=Courier New]minecraft [/FONT]will still bring up the login.[ http://dl.dropbox.com/u/26498135/installer.sh]("http://dl.dropbox.com/u/26498135/installer.sh")

---

