---
title: "Last try Enemy Territory"
date: 2007-03-10
forum: Gaming &amp; Leisure
---

### Post by Elena678 on 2007-03-10
hi, i just downloaded the newest (i tink so) version of Enemy Territory here
[http://www.fileshack.com/file.x?fid=2743](http://www.fileshack.com/file.x?fid=2743)

(i never could play on older :) )

now, i would realy like to try it out. so, do somboddy can tell me wath i need to do to make the .run file running?

greetings

---

### Post by rokixz on 2007-03-10
> **Elena678 said:**
> hi, i just downloaded the newest (i tink so) version of Enemy Territory here
[http://www.fileshack.com/file.x?fid=2743](http://www.fileshack.com/file.x?fid=2743)

(i never could play on older :) )

now, i would realy like to try it out. so, do somboddy can tell me wath i need to do to make the .run file running?

greetings


Go to terminal and enter this:

cd /path/where/the/file
sudo sh file.run

If you wanna sound in game you must enter this every time you restart computer :

sudo chown username /proc/asound/card0/pcm0c/oss
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss

---

### Post by Elena678 on 2007-03-10
he, thanks, the first thing is working :)

aboud the sound, that is also not the problem, now i only need to see somthing, becouse my screen still black :S

greets

---

### Post by rokixz on 2007-03-10
> **Elena678 said:**
> he, thanks, the first thing is working :)

aboud the sound, that is also not the problem, now i only need to see somthing, becouse my screen still black :S

greets


Maybe you don't have an OpenGL installed ?

If you use Automatix select NVIDIA or ATI drivers to install.

Or go [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29) (If Nvidia)
If ATI go to add remove programs, and select ATI driver and follow instructions

---

### Post by Razorback on 2007-03-14
I am trying to install the game but I keep getting:

Verifying archive integrity... All good.
Uncompressing Enemy Territory 2.55...........................................................................................................................................................................................................................................................................................................
It is recommended to install as the super user
Please enter the root password or hit enter to continue as is
Password:
su: Authentication failure
Sorry.
/home/pcuser/.setup7987: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
./setup.sh: line 143:  8016 Segmentation fault      "$setup" "$@" 2>>$NULL
The setup program seems to have failed on x86/glibc-2.1

See [http://zerowing.idsoftware.com/linux/](http://zerowing.idsoftware.com/linux/) for troubleshooting
pcuser@pcuser-desktop:~/Desktop$ gksudo ./et-linux-2.55.x86.run
Warning: Tried to connect to session manager, Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed

When I put in my password I get the same errors.  It doesn't seem to matter whether I enter a password or not - I get the same error.  And I cannot find the libgtk-1.2.so.0 file.  Any help would be appreciated. :)

---

### Post by tubasoldier on 2007-03-14
you can't really install it through sudo.

the best way is as a super user. 

sudo bash
passwd

that will allow you to set up a root password. Then su will work as it is supposed to.

---

### Post by kiddvenom on 2007-03-14
I strongly recommend using [this]("http://www.katanoon.nl/ubu-e/install.php") ([http://www.katanoon.nl/ubu-e/install.php](http://www.katanoon.nl/ubu-e/install.php)) guide. It insures that you properly install and run ET as stable as possible in no time. Their directions are very concise, straight and to the point.

---

### Post by Razorback on 2007-03-14
> **tubasoldier said:**
> you can't really install it through sudo.

the best way is as a super user. 

sudo bash
passwd

that will allow you to set up a root password. Then su will work as it is supposed to.

Super user - Is that the log on name and password?  I thought it was because any time I want to do something that requires root it asks for the password; i.e. Synaptic Package Manager, etc.  Or is super user another setup?

---

### Post by blanky on 2007-03-14
Super User is root, and I don't suggest doing that. Did you read kiddvenom's post?

---

