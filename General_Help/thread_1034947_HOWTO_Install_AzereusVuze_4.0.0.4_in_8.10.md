---
title: "HOWTO: Install Azereus/Vuze 4.0.0.4 in 8.10"
date: 2009-01-08
forum: General Help
---

### Post by davidcaiazzo on 2009-01-08
_Note: At the time of writing the current version was 4.0.0.4 the script included ONLY supports that version as well as this tutorial. I will update this post as newer versions come out._

**Manual way:**
Okay first things first you are going to need to download the newest version of Azureus and install the java runtime environment.

**For Azureus/Vuze 32bit:**
In the terminal:
```
wget http://prdownloads.sourceforge.net/azureus/Vuze_4.0.0.4_linux.tar.bz2?download && tar xvjf Vuze_4.0.0.4_linux.tar.bz2 && sudo aptitude install sun-java6-bin
```

**For Azureus/Vuze 64bit:**
In the terminal:
```
wget http://prdownloads.sourceforge.net/azureus/Vuze_4.0.0.4_linux-x86_64.tar.bz2?download && tar xvjf Vuze_4.0.0.4_linux-x86_64.tar.bz2&& sudo aptitude install sun-java6-bin
```

Next we are going to have to edit the azureus script in order to point it to the location we are going to move the core files to.
```
 
cd vuze
gedit azureus

```

Now find this line in the file:
```

#PROGRAM_DIR="/home/username/apps/azureus"	# use full path to Azureus bin dir

```

and replace it with this:
```

PROGRAM_DIR="/usr/share/vuze"

```

_Remember to remove the # _or else it won't work. Now it is time to move everything where it needs to be. While still in the vuze directory in the terminal type:
```

sudo mv "azureus" "/usr/bin/azureus"
sudo mv "vuze" "/usr/bin/vuze"
cd ..
sudo mv "vuze" "/usr/share/vuze/"

```

**Script:**
*WARNING: The tar files attached contain already modified versions of the azureus start script as well as my script containing the "rm" command. If you feel uncomfortable with this please follow the manual instructions. As always this script is available without warrenty so use at your own risk!*

Download the appropriate script attached to this thread. From there unzip it and move into that directory. DO NOT CLOSE THE TERMINAL WHEN DONE!
**32bit:**
```

?tar xvzf vuzeinstall-4_0_0_4-32bit.tar.gz && cd vuzeinstall-4_0_0_4-32bit

```

**64bit:**
```

?tar xvzf vuzeinstall-4_0_0_4-64bit.tar.gz && cd vuzeinstall-4_0_0_4-64bit

```

Now you have to get the newest version of Azureus/Vuze and install the java-jre:
**For Azureus/Vuze 32bit:**
In the terminal:
```
wget http://prdownloads.sourceforge.net/azureus/Vuze_4.0.0.4_linux.tar.bz2?download && tar xvjf Vuze_4.0.0.4_linux.tar.bz2 && sudo aptitude install sun-java6-bin
```

**For Azureus/Vuze 64bit:**
In the terminal:
```
wget http://prdownloads.sourceforge.net/azureus/Vuze_4.0.0.4_linux-x86_64.tar.bz2?download && tar xvjf Vuze_4.0.0.4_linux-x86_64.tar.bz2&& sudo aptitude install sun-java6-bin
```

Now make the script executable and run it:
```

chmod +x vuzeinstall
sudo ./vuzeinstall

```

Thats it your done! Happy torrenting.
[B]
Script Source:[/B]
```

#!/bin/sh
mv "azureus" "/usr/bin/azureus"
cd vuze
rm azureus
mv "vuze" "/usr/bin/vuze"
cd ..
mv "vuze" "/usr/share/vuze/"
chmod -R 777 /usr/share/vuze

```
[B]
Optional Steps:[/B]
[B]
Make it so Vuze can update itself now:[/B]
```

sudo chmod -R 777 /usr/share/vuze

```
[B]
Add icon to applications menu:[/B]
Goto System->Main Menu->Internet->New Item
```

Type:Application
Name: Vuze
Command: vuze

```
In order to get the frog icon for it click the spring board looking icon on this dialog to the left.
Where it says browse type in /usr/share/vuze and wait a second for it to load. You should now see something called vuze.png. Click on it and hit okay and you are done!

---

### Post by ferronica on 2009-01-14
nice updated my azureus to 4.0.0.4 :)

---

### Post by hyper_ch on 2009-01-14
howtos belong in the tutorials section and need to be approved first.

---

### Post by davidcaiazzo on 2009-01-15
I did submit it to the tutorials page, some how it ended up in general help. Albeit I did submit it when I was getting some apache errors.

---

### Post by hyper_ch on 2009-01-16
then I apologize :)

---

### Post by David Valentine on 2009-01-16
```
sudo chown -R 777 /usr/share/vuze
```should be 
```
sudo chmod -R 777 /usr/share/vuze
```

---

### Post by flaggh on 2009-01-16
EDIT: My mistake.

---

### Post by davidcaiazzo on 2009-01-16
> **David Valentine said:**
> ```
sudo chown -R 777 /usr/share/vuze
```should be 
```
sudo chmod -R 777 /usr/share/vuze
```

Ops didn't notice that. Thank you it's been changed.

---

### Post by Clancy_s on 2009-01-19
That worked beautifully updating my old version to 4.0.0.4, thank you.

64 bit - I installed the beta of 64 bit java yesterday, it worked fine with Vuze 3.* so I skipped the java install, and edited the menu properties for the existing Vuze button rather than making a new entry.

All good.

---

### Post by OisinT on 2009-04-24
I'm having trouble with a few steps that aren't working:

```
?tar xvzf vuzeinstall-4_0_0_4-64bit.tar.gz && cd vuzeinstall-4_0_0_4-64bit
bash: ?tar: command not found

```

```
chmod +x vuzeinstall
sudo ./vuzeinstall
chmod: cannot access `vuzeinstall': No such file or directory
```

---

### Post by relaxedcrazyman on 2009-04-27
cant help with part of it, but i know this:

```
?tar xvzf vuzeinstall-4_0_0_4-64bit.tar.gz && cd vuzeinstall-4_0_0_4-64bit
bash: ?tar: command not found
```

should be:

```
tar xvzf vuzeinstall-4_0_0_4-64bit.tar.gz && cd vuzeinstall-4_0_0_4-64bit
```


oh yea, thanks a s**t load for this, i tried so many different guides and stuff, nothing worked till this. thanks so much

---

