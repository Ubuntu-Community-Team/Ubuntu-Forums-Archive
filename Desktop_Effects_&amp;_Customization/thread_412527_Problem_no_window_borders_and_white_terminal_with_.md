---
title: "Problem: no window borders and white terminal with desktop effects."
date: 2007-04-18
forum: Desktop Effects &amp; Customization
---

### Post by digby280 on 2007-04-18
Hi,

If I turn on desktop effects my windows borders disappear and all terminal windows appear as white boxes.  Can anyone suggest anything I can do to get desktop effects working properly? I've attached a before and after screen shot to make this a little clearer.

[ATTACH]29985[/ATTACH]

[ATTACH]29986[/ATTACH]

---

### Post by Buggin on 2007-04-18
I'm actually having the same issue. I got it to work on my laptop that already had Beryl running before the uprade by using the beryl manager to select compiz s the window manager. On my work computer though, this is not an option bcuase I don't have beryl. I'm not sure what I'm going to try to fix it but if I come up with something Ill let you know.

---

### Post by skyconcert on 2007-04-18
Same problem here.  No border on ANY window system wide, and white terminal screen too.  Am running beryl though, and did not choose "desktop effects" under Feisty Preferences.  Does not work either when "compiz" is chosen as the desktop manager.  When Gnome Desktop Manager is selected, everything returns to normal.  Probably hear about this "one" from alot of users.

---

### Post by old_geekster on 2007-04-18
Are you all using the latest version of Beryl?

I had the same problem with older versions.  Now, however, it is working perfectly.  I am running Feisty (2.6.20.15).

Also, have you updated to the latest video drivers.  This will definitely make a difference.  ATI presents more of a challenge than nVidia.

---

### Post by digby280 on 2007-04-18
> **old_geekster said:**
> Are you all using the latest version of Beryl?

I had the same problem with older versions.  Now, however, it is working perfectly.  I am running Feisty (2.6.20.15).

Also, have you updated to the latest video drivers.  This will definitely make a difference.  ATI presents more of a challenge than nVidia.

Well I'm using the desktop-effects utility which I believe uses Compiz, but I installed the latest version of beryl Beryl from the feisty repositories to see if that works and had the same problem.  My video card is an nVidia GeForce FX 5200 and I have the latest drivers for it.  I'm using the same version of Feisty as you 2.6.20.15.

---

### Post by badlogic on 2007-04-18
make sure that this line is in your xorg.conf


Option         "AddARGBGLXVisuals" "True"

once I added that then did an alt ctrl backspace to reload it fixed it.

---

### Post by digby280 on 2007-04-18
> **badlogic said:**
> make sure that this line is in your xorg.conf


Option         "AddARGBGLXVisuals" "True"

once I added that then did an alt ctrl backspace to reload it fixed it.

Excellent! It works perfectly now.  I knew there had to be some really simple solution.  Thanks badlogic

---

### Post by shadeless on 2007-04-18
can you please tell me where exactly i have to add this line ?

i tried it in the monitor and device sections but it didn't work.
would be great if anyone could help me out :)

---

### Post by digby280 on 2007-04-18
> **shadeless said:**
> can you please tell me where exactly i have to add this line ?

i tried it in the monitor and device sections but it didn't work.
would be great if anyone could help me out :)

I put it under Section "Screen".

Hope that helps.

---

### Post by shadeless on 2007-04-18
thanks for the quick reply, but sadly it didnt work :(

---

### Post by digby280 on 2007-04-18
Did you restart your computer or press Ctrl, Alt, backspace after you changed it?

---

### Post by shadeless on 2007-04-18
yeah, did a crtl alt backspace. but it didnt work.

---

### Post by kpel on 2007-04-18
I had the same problem by simply enabling the desktop effects in Feisty (2.6.20.15) with the NVIDIA 1.0-9755 drivers.

Adding the line that badlogic provided to the xorg.conf file fixed the window borders and gave me the wobble effect, though it killed my workspaces.  If desktop effects are on (with or without cube selected) I will have only one workspace available.  Turning it off gives me the normal two.

---

### Post by digby280 on 2007-04-19
> **kpel said:**
> I had the same problem by simply enabling the desktop effects in Feisty (2.6.20.15) with the NVIDIA 1.0-9755 drivers.

Adding the line that badlogic provided to the xorg.conf file fixed the window borders and gave me the wobble effect, though it killed my workspaces.  If desktop effects are on (with or without cube selected) I will have only one workspace available.  Turning it off gives me the normal two.

I had that problem too.  You need to install the gnome-compiz-manager:

```
sudo apt-get install gnome-compiz-manager
```

And then go to System >> Preferences >> GL Desktop >> Workspaces

and change the number of viewpoints.

---

### Post by coolix on 2007-04-19
> **shadeless said:**
> yeah, did a crtl alt backspace. but it didnt work.

I added the line in the Device section of xorg.conf, not Screen
Hope that helps

---

### Post by thecure on 2007-04-19
> **badlogic said:**
> make sure that this line is in your xorg.conf


Option         "AddARGBGLXVisuals" "True"

once I added that then did an alt ctrl backspace to reload it fixed it.

I saw this same solution at [http://forum.beryl-project.org/viewtopic.php?f=35&t=1631]("http://forum.beryl-project.org/viewtopic.php?f=35&t=1631")
 and it also worked great for me.

---

### Post by hobieone on 2007-04-19
worked form me ! once i [ut that line in the device section and did the alt+ctrl+backspace thatnks, also had install the compiz manger as with earlier post to get the deskspaces back.

i agree with earlier post that the will be a common issue posted probably should get something about the fixes sticky as a fact or something so others can easly find it

---

### Post by hobieone on 2007-04-19
just another tip. before using cedega or wine shutdown the desktop effects or you'll take a big performance hit with those apps

---

### Post by Curtisc on 2007-04-20
I'm not entirely sure what it does, but I got rid of the same problem with

Option		"XaaNoOffscreenPixmaps"	"on"

in the "Screen" section.

---

### Post by chenel on 2007-04-21
badlogic -  worked for me as well.  Thanks.

Why is this the right fix, though?

---

### Post by mefellows on 2007-04-25
I had both Beryl and Compiz installed - Beryl worked fine as well as Metacity, but compiz alas had no window borders. However, typing the following command into a terminal seemed to fix it:

```
gtk-window-decorator --replace --sync
```

Obviously i didn't want to do this each time i started up and it didn't seem elegant to run a script (i.e. covering up the real problem), editing compiz's gconf entry didn't help either.

Unfortunately uninstalling all Beryl related packages (especially the ones related to window decordation) was the only thing that worked for me; i think it the decoration library of Beryl was conflicting with that of Compiz's. I will try re-installing Beryl now to see if the conflict arises again...

---

### Post by mefellows on 2007-04-25
Re-installation of Beryl worked a treat; all three window managers work. Here is a list of the packages that i installed for anyone who is interested:

[LIST]
[*]beryl                           - Compositing window manager, decorator and 
[*]A beryl-core                      - Compositing window manager - Beryl Project
[*]A beryl-manager                   - Tray application launcher tool - Beryl Pro
[*]A beryl-plugins                   - Collection of plugins for Beryl           
[*]beryl-plugins-data              - Plugins data - Beryl Project              
[*]beryl-settings                  - Plugin and configuration tool - Beryl Proj
[*]beryl-settings-bindings         - Plugin and configuration tool - Beryl Proj
[*]beryl-ubuntu                    - Simplified Plugin and configuration tool -
[*]libberyldecoration0             - Settings library for plugins - Beryl Proje
[*]libberylsettings0               - Settings library for plugins - Beryl Proje
[*]libberylsettings0-gconf         - Settings library for plugins - Beryl Pro
[/LIST]

---

### Post by waggygee on 2007-07-10
> **badlogic said:**
> make sure that this line is in your xorg.conf


Option         "AddARGBGLXVisuals" "True"

once I added that then did an alt ctrl backspace to reload it fixed it.

How do I save the xorg.conf after adding that line.... (I opened it manually). I didnt allow me to save it though, is there a terminal command I can put in that will open it and allow me to save the new line?:confused:

---

### Post by chenel on 2007-07-10
Did you open it as root?  If you didn't, you won't have the appropriate permissions to save it...

---

### Post by waggygee on 2007-07-11
> **chenel said:**
> Did you open it as root?  If you didn't, you won't have the appropriate permissions to save it...

How do I do that when opening it manually?

---

### Post by waggygee on 2007-07-11
> **badlogic said:**
> make sure that this line is in your xorg.conf


Option         "AddARGBGLXVisuals" "True"

once I added that then did an alt ctrl backspace to reload it fixed it.

I managed to add these lines into xorg.conf but when I clicked atl, ctrl nd backspace, the screen went blue it failed to do what it was supposed to. And now when I boot Ubuntu, I dont have a graphic interface.... the screen is black with white writting! When I log in its like Im using the terminal. Is there a way I can edit my xorg.conf now?

---

### Post by timothywcrane on 2007-10-12
Great advice. I edited my xconf file, restarted my X, reactivated NVidia drivers and then restarted the computer, than activated beryl. no prob.

One thing that I think helped was to make sure you have the correct video card listed in xconf. there is an auto update command listed in the file itself. If your problem was with a white term, use the run command function on your GUI. Run the script in terminal, and when it pops up, enter your sudo pass (even though you cannot see it) and hit enter. Thanks for the advice.

Beryl and Compriz (Fusion) and NVidia FX5200. Works great.

---

### Post by ezgoinguy on 2007-12-31
Adding the Option to my xorg.conf file did the trick also, but it was not easy to do, since I could not see to type anything in my terminal window!  Ended up enabling root user and editing the xorg.conf file that way.  Funny thing is, this was a re-install on the same hardware with the same installation media....I didn't have this issue the first time through.

---

