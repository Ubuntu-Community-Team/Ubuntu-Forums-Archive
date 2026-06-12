---
title: "Installing Mac4Lin (Ubuntu 10.04"
date: 2010-06-10
forum: Desktop Environments
---

### Post by PhilDawg09 on 2010-06-10
Hello all I am a former Windows User :D That's right I decided to make the plunge into the open source community and I am quite liking it. Any-who my problem lies with the mac4lin installation process can anybody guide me through it I've tried looking on youtube, But to no avail... The tutorials don't show FULLY how to do it, and also I need to get my video card out of Low resolution (VIA/S3G Unichrome PRO IGP K8M800 Chipset do not know the make of mainboard sadly D; as it's a prebuilt PC) ANywho thanks for taking the time to read this newbish question!

Best Reguards, 

-Philip k.-

---

### Post by kennedyvelez on 2010-06-10
> **PhilDawg09 said:**
> Hello all I am a former Windows User :D That's right I decided to make the plunge into the open source community and I am quite liking it. Any-who my problem lies with the mac4lin installation process can anybody guide me through it I've tried looking on youtube, But to no avail... The tutorials don't show FULLY how to do it, and also I need to get my video card out of Low resolution (VIA/S3G Unichrome PRO IGP K8M800 Chipset do not know the make of mainboard sadly D; as it's a prebuilt PC) ANywho thanks for taking the time to read this newbish question!

Best Reguards, 

-Philip k.-



Sir,

 Try this:
[http://maketecheasier.com/turn-your-ubuntu-hardy-to-mac-osx-leopard/2008/07/23](http://maketecheasier.com/turn-your-ubuntu-hardy-to-mac-osx-leopard/2008/07/23)
[http://www.howtoforge.com/mac4lin_make_linux_look_like_a_mac](http://www.howtoforge.com/mac4lin_make_linux_look_like_a_mac)

 I've already done it, but I get tired of ... what do you call  that?  AWN -avant! so i remove it all and return everything to ubuntu... its quite an adventure...

---

### Post by PhilDawg09 on 2010-06-10
> **kennedyvelez said:**
> Sir,

 Try this:
[http://maketecheasier.com/turn-your-ubuntu-hardy-to-mac-osx-leopard/2008/07/23](http://maketecheasier.com/turn-your-ubuntu-hardy-to-mac-osx-leopard/2008/07/23)
[http://www.howtoforge.com/mac4lin_make_linux_look_like_a_mac](http://www.howtoforge.com/mac4lin_make_linux_look_like_a_mac)

 I've already done it, but I get tired of ... what do you call  that?  AWN -avant! so i remove it all and return everything to ubuntu... its quite an adventure...

Ah well thank you for your ime :)

---

### Post by aala on 2010-08-31
[[COLOR="Blue"]Download it from here![/COLOR]]("http://sourceforge.net/projects/mac4lin/")

And just unpack it, i.e: If it was download at "***/home/your name/Downloads***" directory, just open nautilus( "*Nautilus is your file manager, like Explorer for windows*" ) go to "**Places/Downloads**" in your MenuBar and once you'll open it, right click on the **"Mac4Lin_Install_v1.0.zip"** archive and click on the "**Extract Here**" option. Once extracted open the **Mac4Lin_Install_v1.0** folder and there will be 2 folders, but don't bother going into the one that's named "*_MACOSX*" and go into the one that's named "**Mac4Lin_Install_v1.0**".

Ok now, in this directory you should have 18 items in it, 16 folders, and 2 shell scripts ("**.sh**") one for installing the theme, and the other one for uninstalling it. So now just click on the one named "**Mac4Lin_Install_v1.0.sh**" for installing the great Mac4Lin theme but make sure it is allowed for execution by right clicking on it, go to Properties; when the properties window pop up go to the 3rd tab "**Permissions**", and look for "**Execute:**" option, and just make sure it's checked. You may have a little window popping up asking you for an option to take, something like "**[COLOR="Navy"]Run in Terminal / Display / Cancel[/COLOR]**", and just like you've guested it, choose "**Run in terminal** option and just follow the instructions from the Terminal Window ("[COLOR="DarkRed"]Terminal[/COLOR] *[I]is like CMD console for Windows*[/I]"). "And you are good 2 Go.

Alright hopefully you'll get it.

---

### Post by Insanejake666 on 2010-09-29
Thanks

---

### Post by Jonny87 on 2010-10-11
Sorry to bring up an old thread but I have just installed this and have noticed that some apps like Synaptic Package Manager have gone to an old style look like they do in KDE is there a way to fix this?

---

### Post by ankspo71 on 2010-10-11
Hi Jonny87
When we run programs such as Synaptic Package Manager, it will run as the root user... which means it will also automatically use the root user's theme settings too. 

Below are commands that will link the root user's theme settings to your theme settings so that they always share the same theme settings.

```
sudo ln -s ~/.themes /root/.themes
sudo ln -s ~/.icons /root/.icons
sudo ln -s ~/.fonts /root/.fonts
```

Hope this helps.

---

### Post by Jonny87 on 2010-10-11
> **ankspo71 said:**
> Hi Jonny87
When we run programs such as Synaptic Package Manager, it will run as the root user... which means it will also automatically use the root user's theme settings too. 

Below are commands that will link the root user's theme settings to your theme settings so that they always share the same theme settings.

```
sudo ln -s ~/.themes /root/.themes
sudo ln -s ~/.icons /root/.icons
sudo ln -s ~/.fonts /root/.fonts
```Hope this helps.

](*,)
Doh!!! I should have known that... I mean its not like I didn't have to enter my sudo password or anything. Sorry for the noob question.

---

### Post by aala on 2010-10-15
> **Jonny87 said:**
> ](*,)
Doh!!! I should have known that... I mean its not like I didn't have to enter my sudo password or anything. Sorry for the noob question.
Do what ankspo71 told you about linking those folders, and you may also want to do a:

gksu gnome-appearance-properties

and also choose from there, the theme, icons and fonts that you want (if not already chosen).

=======
~~~~~~~
Or you can just download the macbuntu theme, it's similar tu mac4lin, but implemented for lucid and maverick ubuntu versions. Plus the script for that theme is kind of smarter than the one on mac4lin (*[COLOR="Gray"]this one it's old! too old![/COLOR]*).

You can download it from here [**[COLOR="Blue"]MACBUNTU[/COLOR]**]("http://gnome-look.org/content/show.php/Macbuntu?content=129021")

---

