---
title: "Desktop effects wont enable"
date: 2007-11-10
forum: Desktop Effects &amp; Customization
---

### Post by baggies on 2007-11-10
I can't enable desktop effects using gutsy.
The chip is a ATI 200, using the ATI driver, is there a known issue with this chipset 
or is there a work around?

---

### Post by TadH on 2007-11-10
did you restart x after you chose custom settings?

---

### Post by baggies on 2007-11-10
"did you restart x after you chose custom settings?"

Sorry I'm a newbie as far as linux is concerned, can you explain, I got the "Desktop effects wont enable" message after trying the custom settings.
How do you restart x?

---

### Post by TadH on 2007-11-10
ctrl+alt+bacspace

---

### Post by TadH on 2007-11-10
check your restricted driver manager and tell me what it says also

system > admin > estricted driver manager

---

### Post by baggies on 2007-11-10
The "Restricted Drivers Manager" has the ATI driver selected and enabled.

---

### Post by TadH on 2007-11-10
wel then im pretty sure it should be working.

---

### Post by Forlong on 2007-11-10
> **baggies said:**
> The "Restricted Drivers Manager" has the ATI driver selected and enabled.
Then you need Xgl: ```
sudo apt-get install xserver-xgl
```

---

### Post by baggies on 2007-11-11
Done as you've said, but still can't enable desktop effects.
The desktop doesn't seem very stable either with Xgl.
How do you disable Xgl?

---

### Post by Forlong on 2007-11-11
What's the output of ```
compiz
``` in a terminal?

---

### Post by baggies on 2007-11-11
I had to do a clean install as with Xgl enabled the desktop was way too slow.

---

### Post by baggies on 2007-11-11
Here's the output for the command "SKIP_CHECKS=yes compiz"

 Checking for Xgl: not present. 
No whitelisted driver found
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator

(gtk-window-decorator:5507): Gdk-WARNING **: Using Cairo rendering requires the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap

(gtk-window-decorator:5507): Gdk-WARNING **: Using Cairo rendering requires the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap
/usr/bin/compiz.real (core) - Fatal: No composite extension

Don't want to enable Xgl again as it caused a few problems.

---

### Post by AMM6 on 2008-02-27
i had the same problem.  xgl has made it so i cant login without gnome failsafe please tell me how to remove it to.   anyway.   my computer sais there are no restricted drivers needed for my computer.

---

### Post by Yellow Pasque on 2008-02-27
> **AMM6 said:**
> i had the same problem.  xgl has made it so i cant login without gnome failsafe please tell me how to remove it to.   anyway.   my computer sais there are no restricted drivers needed for my computer.
```
sudo apt-get remove xserver-xgl
```

---

### Post by AMM6 on 2008-02-27
thx i thought i might have to reinstal everything

---

### Post by Yellow Pasque on 2008-02-27
> **AMM6 said:**
> thx i thought i might have to reinstal everything
You're welcome. Are all of your video issues fixed now?

---

### Post by AMM6 on 2008-02-27
the output im getting from code compiz is 
```
 aborting and using fallback: /usr/bin/metacity 
```
im guessing thats a problem
i also cannot activate ANY desktop effects

---

### Post by Yellow Pasque on 2008-02-27
Ok, what video card and driver are you using? Also, look at this post and make sure your /usr/bin/compiz is set up properly  [http://ubuntuforums.org/showpost.php?p=4202892&postcount=6](http://ubuntuforums.org/showpost.php?p=4202892&postcount=6)

---

### Post by AMM6 on 2008-02-27
well im guessing its my vid card now that im finding out that its a trident blade 3D   i cannot instal any drivers either

---

### Post by Yellow Pasque on 2008-02-27
Hmm. The trident drivers are included in Ubuntu's base package, so they should already be installed. Does this work for you?

Press Ctrl+Alt+F1, then run the following command. Trident driver should be one of the options.
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by AMM6 on 2008-02-27
its asking for a password but wont except any that i know and will the trident be able to run the desktop effects?

---

### Post by AMM6 on 2008-02-27
i did manage to get the  computer to recognize my card and find a matching driver in the screens and graphics menu 
but the desktop effects still will not turn on

---

### Post by Yellow Pasque on 2008-02-27
Type 'compiz' in the terminal. What output do you get?

---

### Post by AMM6 on 2008-02-28
```
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
```
When i go into screens and graphics it does have a driver listed.

---

### Post by Yellow Pasque on 2008-02-28
I'm not sure if the trident chip will work with compiz. Try adding trident to the WHITELIST in /usr/bin/compiz
```
sudo gedit /usr/bin/compiz
```
On line 71, add trident to the list. Also make sure the rest of the file is set correctly as I showed you in that link a few posts back.

---

### Post by AMM6 on 2008-03-05
```
compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1023:8500 (rev 6a) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 

```

---

### Post by abobo123 on 2008-03-05
I'm having the same issue with a radeon 9800 pro.  I'm using the fglrx driver.  I'm probably a little different in that i'm trying to get this working dualhead.  The effects worked when i ran a single screen.  I added fglrx to the whitelist and got the same output as above.  When i install xgl, i can only load gnome on failsafe, when i try to open a normal session, the second screen gets garbled and it shoots me back to the login.  any ideas?

---

### Post by larryfroot on 2008-03-05
try typing in a terminal

compiz --return 

and post the output

---

### Post by Yellow Pasque on 2008-03-05
> **abobo123 said:**
> I'm having the same issue with a radeon 9800 pro.  I'm using the fglrx driver.  I'm probably a little different in that i'm trying to get this working dualhead.  The effects worked when i ran a single screen.  I added fglrx to the whitelist and got the same output as above.  When i install xgl, i can only load gnome on failsafe, when i try to open a normal session, the second screen gets garbled and it shoots me back to the login.  any ideas?
Compiz version needs to be  0.7 or greater to work on multiple displays. i'm guessing the Ubuntu version is not.

---

### Post by abobo123 on 2008-03-05
Without the driver whitelisted i get the same output AMM6 had 6 posts up, xgl not present, no whitelisted driver found, falling back to metacity.  With the driver manually put on the whitelist, I get the following 

```
$ compiz --return
Checking for Xgl: not present. 
Detected PCI ID for VGA: 02:00.0 0300: 1002:4e48 (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 
metacity: Unknown option --return

```

I may have found something that will make my setup work here, i'm going to give it a try, but not till tomorrow.  Please let me know if you have any other suggestions. [http://fleshy.org.nz/yum/2007/10/05/ati-radeon-9600-with-compiz-and-dual-head/]("http://fleshy.org.nz/yum/2007/10/05/ati-radeon-9600-with-compiz-and-dual-head/")

Also found this blog with some interesting instructions for fglrx with aiglx support.  That'll be my next step should the first fail.  [http://forlong.blogage.de/article/2007/10/23/fglrx-8423---finally-with-AIGLX-support]("http://forlong.blogage.de/article/2007/10/23/fglrx-8423---finally-with-AIGLX-support")

You suggested i may not have the latest version of compiz.  I'm fairly new to this, how would i check my version?  I know it was just updated, are the repositories outdated?

Thanks

---

### Post by Yellow Pasque on 2008-03-06
```
dan@harvest:/etc/X11$ compiz --version
```
Or through Synaptic, I see compiz 0.6 (at least in Gutsy/7.10). You may be able to build Compiz from source or get the backported Hardy Heron/8.04 version.

---

### Post by abobo123 on 2008-03-06
I'd like to give the backports a shot, (you were right, I have version 0.6) i see the new version of compiz listed in there ([http://packages.ubuntu.com/hardy/x11/compiz]("http://packages.ubuntu.com/hardy/x11/compiz")).  I'm having trouble following through with it though.  I can download the file, but it won't get the dependencies and install.  When i try to add them (dependencies) manually, apt-get later on insists that they are broken and need to be downgraded.  I've tried I hardy-backports to my sources.list (with and without pinning) but it won't let me access anything.  Any advice?

Thanks again

---

### Post by abobo123 on 2008-03-06
I figured out why the backports won't work... The directories i added to my sources.list are all empty even though it's listed on that page.  Guess i should look at building it from source?  I'm still a bit green to this, I'll look for answers on what to do, but if you have any quick advice, i won't complain.

Thanks

---

