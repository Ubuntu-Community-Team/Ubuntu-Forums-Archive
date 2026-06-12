---
title: "Beryl Via Synaptic"
date: 2007-04-29
forum: Desktop Effects &amp; Customization
---

### Post by dannymichel on 2007-04-29
I used Synaptic to download and install Beryl and all it's components.
I see the red ruby in my taskbar, but I really don't see anything fancy going on.
I have an ATI radeon x1650 Pro PCIE.
Can anyone help me?

---

### Post by rolf-c on 2007-04-29
Right-click on the Beryl icon and select "Beryl Settings Manager"

Click on the Desktop icon (third from the left)

Ensure 'Desktop Cube' is checked.

If so, hold down CTRL-ALT, left click and roll your mouse around to see the cube.

---

### Post by dannymichel on 2007-04-29
Desktop cube is checked and I did what you told me and got nothing

---

### Post by rolf-c on 2007-04-29
Ok, open a terminal by clicking Applicatioins -> Accessories -> Terminal.

At the prompt, type 'glxinfo |grep direct'.  You want to see this as output
```

direct rendering: Yes

```

If the answer is No or there is no grep output, then there is work to be done yet to get the sweet eye candy.

If the answer is Yes, past the contents of your /etc/X11/xorg.conf file here.

---

### Post by acidphex on 2007-04-29
There's an issue with XGL and Feisty for Beryl. There is currently no support from the Ubuntu repositories. 

Uninstall **beryl** then you will have to disable the **universe** repository and use the repository  from the tutorial below to re-install beryl. 

After you've gone through the tutorial you have to lock the **beryl** packages so Ubuntu doesn't try to upgrade them and then re-enable the **universe** repository.

**The tutorial:**

_[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL)_

---

### Post by dannymichel on 2007-04-29
I see:
danny@danny-desktop:~$ glxinfo |grep direct
direct rendering: Yes
danny@danny-desktop:~$

---

### Post by scanez on 2007-04-29
Are you sure you are actually using beryl? (The red ruby does not mean it is necessarily running)

Right click on the ruby -> Select Window Manager -> make sure Beryl is checked.

---

### Post by acidphex on 2007-04-29
Type in **beryl** in command prompt and paste the out put here.

---

### Post by dannymichel on 2007-04-29
> **scanez said:**
> Are you sure you are actually using beryl? (The red ruby does not mean it is necessarily running)

Right click on the ruby -> Select Window Manager -> make sure Beryl is checked.
it wont check itself no matter how many times i check it.

---

### Post by dannymichel on 2007-04-29
> **acidphex said:**
> Type in **beryl** in command prompt and paste the out put here.

danny@danny-desktop:~$ beryl
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension
danny@danny-desktop:~$

---

### Post by acidphex on 2007-04-29
> **dannymichel said:**
> danny@danny-desktop:~$ beryl
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension
danny@danny-desktop:~$

Yup, you have to uninstall beryl and follow my first post. Beryl is using AIGLX instead of ATI's XGL.I had the same issue with Feisty btw...

---

### Post by dannymichel on 2007-04-29
How do I uninstall?
Can I get a setp>by step> on how exactly> i can fix this issue and get beryl working
step>by>step> for newbs like me.

Thanks so much bro.

---

### Post by acidphex on 2007-04-30
**So what we're going to do is:**
-Uninstall Beryl
-Disable universe repository
-Add new repository that has support for ATI XGL/Beryl
-Re-Install Beryl with the new repository
-Lock the Beryl versions
-Enable universe repository
-Add the login scripts and shortcuts to run XGL
-Make Beryl autostart.



[SIZE="5"]**Uninstall Beryl:**[/SIZE]

1. Open up terminal from Applications > Accessories > Terminal

2. Type in, this all one entry: 
```

sudo aptitude remove beryl beryl-core beryl-manager beryl-plugins beryl-plugin-data beryl-settings beryl-setting-bindings libberyldecoration0 libberylsettings0 libemeraldengine0

```



[SIZE="5"]After removing beryl we're now going to be disabling the **universe** repositiory, thats where Ubuntu installs beryl from. Since we don't want it from the Ubuntu repositories we want it from [www.beryl-project.org](www.beryl-project.org), we disable it.[/SIZE]

1. So before we can do that we need to backup the source list so if we mess up we can always revert. So type in:
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
```

2. Disable **universe** repository:
```
gksu synaptic
```

3. We're going to disable the repositories (repos) through the GUI application called Synaptec

	Goto **Settings** > **Repositories** > 
	-on the *Ubuntu Software* tab **uncheck** the second option:
	 "*Community-maintained Open Source software (universe)*"

4. Now we're going to add the repository from beryl-project.org:
	-Click on "**Third-Party Software**" tab in **Software Source** window
	-Click on **+Add...** and paste this line:
	```
deb http://ubuntu.beryl-project.org/ feisty main
```
	-Click on **+Add Soure**
	-Cose the **Software Source** window. Close **Synaptic Package Manager**

5. No we need to add the keys to that repo we just added we do that by typing this in the command line:
   ```
wget http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg -O- | sudo apt-key add -
```

6. No we update apt with:
   ```
sudo aptitude update
```

7. After it's been updated we install XGL & Beryl:

   ```
sudo aptitude install xserver-xgl beryl emerald-themes
```

8. Add script for XGL login session:
   
   ```
gksu gedit /usr/local/bin/startxgl.sh
```
	
	Paste this in gedit:

```
	
#!/bin/sh
Xgl :1 -fullscreen -ac -dpi 96 -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec dbus-launch --exit-with-session gnome-session
```
	Save and close.

9. Making it executable:
   ```
sudo chmod a+x /usr/local/bin/startxgl.sh
```

10. Login session entry:
    ```
gksu gedit /usr/share/xsessions/xgl.desktop
```

	Paste the following:
    ```

[Desktop Entry]
Encoding=UTF-8
Name=Xgl-Beryl-Gnome
Exec=/usr/local/bin/startxgl.sh
Icon=
Type=Application
```

	Save and close



[SIZE="5"]Okay we're almost done just one more thing to do is lock the **beryl** packages and re-enable the **universe** repos.
[/SIZE]
1. open up synaptic again, in commandline:

   ```
gksu synaptic
```

2. To lock the packages: **Search** > type in **Beryl**

	- Hold CTRL key on your keyboard and click on the packaged that are installed to select them.
	- Click on Packages > Lock Version.

3. Re-enable universe repos, because in the future you'll need to install packages that come from these repos.
  	- Click Settings > Repositories
	- on the **Ubuntu Software** tab **check** mark the second option:
	 "**Community-maintained Open Source software (universe)**"
	
	Close Software Resources. Close Synaptic Package Manager.



[SIZE="5"]All we have to do now is add Beryl-Manager to startup, so you don't have to load it when you login.[/SIZE]

Goto **System** > **Preferences** > **Sessions**
   -Select **Startup Programs** tab 
   -Click **Add** type in **beryl-manager**
   Close.

Now just restart Ubuntu. 
At the login screen under **Sessions** select **Xgl-Beryl-Gnome** option. 
Then log in and you should have beryl running with the eye candy working.




[SIZE="5"]Troubleshoot ([COLOR="Red"]DO THIS ONLY IF X CRASHES[/COLOR]):[/SIZE] If you get a black screen on boot and X crashes, which won't because we didn't even touch the xserver configurations. Just in case you can do the following:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by dannymichel on 2007-04-30
WOW
Thanks so much!
That was perfect!

What I did:
Re-installed Ubuntu
Installed Envy and my ATI drivers
Followed your directions to the T
Restarted with Xgl-Beryl-Gnome option. l **[COLOR="Red"]STOP![/COLOR]**
Problem - Wont boot into Ubuntu unless i DON'T choose that option.

I DON'T GET A BLACK SCREEN, IT DOESN'T BOOT IN. That's all.
This is the screen I get with that configure Xorg thing

---

### Post by dannymichel on 2007-04-30
Any ideas?

---

### Post by acidphex on 2007-04-30
> **dannymichel said:**
> Any ideas?

You had the driver working already with direct rendering and everything. **Eny** might've messed  that up, What I would do is **uninstall** the Envy drivers and **go back** to the initial method you installed the drivers with or through Ubuntu's **Restricted Drivers Manager**.

---

### Post by dannymichel on 2007-04-30
The original metho dI used to install the drivers was Envy.
I couldn't install without it.

---

### Post by dannymichel on 2007-05-01
I saw in one tutorial that x1650 was not supported.
Is this true?

If not, Is there a tutorial that can teach me how to install x1650 pro PCIE 64 bit drivers?

---

### Post by dannymichel on 2007-05-01
I still haven't been able to fix this.
Is there anyone that can help me further?
I appreciate all the help so far.
I'm so close, but no cigar.

---

### Post by ksamvel on 2007-05-03
I had problems setting things up in Kubuntu 6.10. With 7.04 I simply followed [instructions]("http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon") and it worked just fine.

Meanwhile the same tutorial says that ATI cards of series x1600 are not supported. (That is exactly what was going on with my card a while ago). Thus I'd say you are unlucky person and have to wait for another Ubuntu release with wider support of hardware or replace your laptop with something more powerful.

---

### Post by dannymichel on 2007-05-03
Yes, I think you are right.
X1600 cards are not supported

---

### Post by dannymichel on 2007-05-08
Ok, I got a new video card, but the x-Something GNOME still crashes on a black scree.
I have a nVidia GT 7600

---

### Post by strumluff on 2007-05-09
> **dannymichel said:**
> Ok, I got a new video card, but the x-Something GNOME still crashes on a black scree.
I have a nVidia GT 7600

Well life is much easier for you now you have an nvidia graphics card.

I'm assuming you are running Feisty so

System -> Administration -> Restricted Drivers Manager

Enable the Nvidia driver. Let it install and reboot.

You will have to remove any version of beryl and XGL you currently have to be on the safe side. Then simply install beryl and emerald from the universe repo, you don't need any other specific repo. 

```
sudo aptitude install beryl emerald-themes beryl-manager
```

Then type beryl-manager to start, should work a charm without XGL as the nvidia drivers work with AIGLX, so remember to log in on a standard gnome session.

If you want beryl to startup then just add beryl-manager to your Startup Programs in System -> Preferences -> Sessions

---

### Post by dannymichel on 2007-05-09
So undo EVERYTHING I did to install Beryl and just do what you just said?

---

### Post by dannymichel on 2007-05-09
I don't think Envy installed the nVidia driver the right way because I can't just go into Preferences>Screen Resolution to change the screen resolution. I have to go to applications>system something>then click on the nVidia icon and change the resolution through the nVidia control panel every time I re-start my computer. And when I do that xorg config thing it shows that I don't have the driver installed I thin cause I hit a dead end. Is there any way you can tell me how to manually install the nVidia driver 64 bit then install Beryl and Synaptic and have it working?
For some reason, no matter how many times I install Ubuntu, I don't seem to have permision to do anything. I mount it to / . Have I done something wrong?

---

### Post by Meshuggah27 on 2007-05-09
There is a huge issue with beryl and ATI drivers.  I have an ATI x800 GTO myself and i got it running after days of trying different things people were telling me on the forum.  Even if you do get it to run,  It wont run as well as it would on an Nvidia card.  And trust me,  Im the biggest ATI fanboy.

---

### Post by dannymichel on 2007-05-09
I have an nVidia card.

---

