---
title: "HOW-TO: Compiz + Mac4Lin installation Guide with Metacity-Compiz switching Scripts"
date: 2008-04-09
forum: Desktop Effects &amp; Customization
---

### Post by nuclearpidgeon on 2008-04-09
[SIZE=4][COLOR=Black]**WELCOME!**[/COLOR][/SIZE]

This how to shows you how to install and configure compiz-fusion, then install the popular project, Mac4Lin. This includes Avant-Window-Navigator, A stylish mac-like Dock, Themes, Icons, Cursors, wallpapers, Desktop effects and Widgets. It also contains details on how to make scripts that allow you to switch between Metacity with a different theme (the Ubuntu 'Human' theme is used as an example), and Compiz, with the Mac4Lin theme. This is especially useful for laptop users, who have to worry about compiz chewing up their battery life.


[SIZE=5][COLOR=Black]**Before:**[/COLOR][/SIZE]
[IMG]http://members.westnet.com.au/thewebbs/images/hosted/Before.jpg[/IMG]
[SIZE=5][COLOR=Black]** After:**[/COLOR][/SIZE]
[IMG]http://members.westnet.com.au/thewebbs/images/hosted/After.jpg[/IMG]


This How-to **does not aim to give you lots of code and instructions to blindly run**, but rather to **teach** you how to do it, **so you understand what's going on** and come off with more knowledge about Linux.

[COLOR=Red]THIS HOWTO IS DESIGNED FOR **UBUNTU 7.10 GUSTY GIBBON AND 8.10 HARDY HERON.** I DO NOT THINK ALL OF IT WORKS ON VARIANTS (kubuntu etc.) DO SO AT YOUR OWN RISK.
**Support for 8.04**: Some repo changes may be needed, for example you need to use EnvyNG, not Envy. I'm currently using Hardy so i'm trying to incorporate both of the distros into it.
[/COLOR]
[COLOR=Red]** TO DO:**
[/COLOR]More Screenshots
AWN Dock theme
Scripts
Full 8.04 Support

**[COLOR=Navy] VERSION/UPDATE HISTORY[/COLOR]**
v0.1 - Started Compiz Section
v0.11 - Minor additions/Refinements
v0.2 - Put in some Hardy compatibility, added AWN section
v0.3 - Added Mac4Lin

NOTE: If you see any MINOR errors (spelling mistakes), just PM me, rather than posting it here and wasting comment space.

[COLOR=Cyan]**COMPIZ**[/COLOR]

Compiz is what's called a desktop manager. It controls how all the windows appear on your screen eg. Title bar colours, system Icons, cursors etc. Ubuntu already has one; it is called Metacity. The advantage of using compiz, is that it has lots of cool effects, including wobbly windows, which make your windows wobble about like jelly when you move them, minimization, opening, closing effects, Window Transparency, Desktop Cube, and various other eye-candy effects.
Compiz-Fusion was originally called Compiz, and had limited effects. Another window manager called Beryl had much the same effects as the current compiz-fusion, and eventually compiz and beryl combined, resulting in Compiz-Fusion

First off, before we install, you'll want to make sure that you have the latest drivers for your video card, and also make sure that your video card can run compiz. Generally if you have a recent computer (past 2-3 years) you should be able to run Compiz.
To find out what video card you have, open up a terminal (Applications => Accessories => Terminal) and type in:
```
lspci | grep VGA
```NOTE: All code is case-sensitive - if something doesn't work, just copy-paste it in (use Shift-Ctrl-V in terminal to paste)
Okay, now you may be wondering what on earth this command does. Well, the first word, lspci, is a command which lists all the hardware on your computer - eg sound cards, network cards etc. It includes the Video card, but typing lspci alone gives a list, and it can sometimes be trick to determine what you want. It is easier if you add the rest of the code: | grep VGA
Firstly, the | is called 'Bar' (the key for it is located to the left of your keyboard between backspace and enter). What it does is essentially let us run 2 commands at once. In this instance, we are using the 'grep VGA' command, which looks at the output, then displays only the lines which contain VGA. This is our video card line. For example, my output is:
```
lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
```**This how-to will only cover NVIDIA and ATI cards.** If you have a different one, search the internet and these forums for driver installation help. It may not even be required; My video card is supported by Ubuntu, which automatically installed it for me.

[COLOR=Lime]** INSTALLING ENVY/DRIVERS**[/COLOR]

Installing the drivers manually is a pain in the butt. Thankfully, [Alberto Milone]("http://www.albertomilone.com") Made a program called Envy. It automatically installs the drivers for you. To install it, we first have to enable 'universe' and 'multiverse' repositories. These are essentially internet sources that contain extra programs, some of which are required to run envy. To enables these, open Software Sources (System=>Administration=>Software Sources). Enter your password to continue, the Tick the universe and multiverse boxes, then click OK. Now we need to tell ubuntu to reload it's software package list, because we've added a new source. Go into terminal and type:
```
sudo apt-get update
```sudo tells the computer to run the command as root, or super user. Google this for more info.
apt-get is a program which controls the software packages.
update tells apt-get to download all the package lists.
Once it's finished, we're ready to install envy!
Download the package [**here**]("http://albertomilone.com/ubuntu/nvidia/scripts/legacy/envy_0.9.10-0ubuntu10_all.deb")
Go to where you downloaded it, and double-click it to run it. Click 'Install Package', and then enter your password  again. When it's finished, close the window.
Now, run envy (Applications=>System Tools=>Envy).
Choose your video card Name (NVIDIA or Ati), the click Apply. Enter your root password, then wait until it finishes. Could take 2-10 minutes depending on your internet speed. Click 'Yes' to automatically configure X. X is what actually controls the screen and the programs that run on it like metacity or compiz.
Reboot once it's done.

[B][COLOR=SeaGreen][COLOR=Sienna] INSTALLING COMPIZ[/COLOR]

[/COLOR][/B] installing compiz is really easy.
GUTSY:
Type this in terminal
```
sudo apt-get install compiz compizconfig-settings-manager compiz-fusion-plugins-main compiz-fusion-plugins-extra emerald
```This tells apt-get to install compiz, the compiz advanced settings manager, the plugins and emerald, which controls the window borders and buttons.
HARDY:
compiz should be installed by default. Simply type
```
sudo apt-get install compizconfig-setting-manager
Once it's finished, you'll need to run compiz. We'll run it through gnome, rather than the terminal. This just guarantees that you'll get effects on first run. Go System=>Preferences=>Appearance, then click on the 'Visual Effects' tab. Now click normal or extra, and close that window. notice the animation effect? If you wanna configure it, go to System=>Preferences=>Advanced Desktop Effects Settings and have a look through the settings.

**[COLOR=DarkOrange]INSTALLING AVANT WINDOW NAVIGATOR[/COLOR]**

Stable Version:

These instructions work for Hardy
Simply type
[code]sudo apt-get install avant-window-navigator
```into a terminal window.
Once again we're using apt-get. apt is very useful for installing software. In this example, we are telling it to install awn, by typing install, then the package name, avant-window-navigator. You can use apt-get install to install lots of programs, just add the package source if necessary, the type in apt-get install <package name>, and it'll install it all for you.
Now to start AWN, just go to Applications => Accessories => Avant-window Navigator. Congrats, you should now have shiny new dock, showing all your open windows. To add a launcher, simply drag a launcher from the main menu onto the dock, and it should pop up. To organise the order of these, go to System => Preferences => Awn Manager, and go to the Launchers tab.

Unstable Version
(Gustsy and Hardy)
The unstable version has more features, but is a bit buggy.
To install it, first we need to add the awn package lists.
Go to System => Administration => Software Sources and click the Third-Party Software tab. Now click add, and in the text box type:
Hardy:
```
[COLOR=Black][FONT=Verdana]deb http://ppa.launchpad.net/awn-testing/ubuntu hardy main[/FONT][/COLOR]
```Gutsy:
```
deb http://ppa.launchpad.net/awn-testing/ubuntu gutsy main
```Now do the same thing again, but this time put this in the text box:
Hardy:
```
deb-src http://ppa.launchpad.net/awn-testing/ubuntu hardy main
```[COLOR=Black]
Gutsy
```
 deb-src http://ppa.launchpad.net/awn-testing/ubuntu hardy main
```[/COLOR]
Now close the window, and when prompted, update your package sources list.

To install, type this into a terminal:
```
sudo apt-get install avant-window-navigator-trunk
```See the above section for starting it.
[COLOR=Purple][B]
MAC4LIN INSTALLATION[/B][/COLOR]

NOTE: I first installed this on Gutsy &#8211; It worked fine, nothing was wrong. I now have hardy, and after installing, I can see that the new menu layout has meant that the Icons need 'refurbishing' to slot in with the new applications. The theme itself, however, works fine.

First off, we need to download all the necessary files. Go to [http://sourceforge.net/projects/mac4lin/](http://sourceforge.net/projects/mac4lin/) and download Part 1, 2 and 3
Now get the Shere Khan X Cursors &#8211; These ones have the authentic 'beachball' effect.
[http://www.gnome-look.org/content/show.php/Shere+Khan+X?content=57588](http://www.gnome-look.org/content/show.php/Shere+Khan+X?content=57588)
Get these Modded Black Cursors if you want black hands (you'll see later on)
[http://www.gnome-look.org/content/show.php/Shere+Khan+Black+Hand?content=62141](http://www.gnome-look.org/content/show.php/Shere+Khan+Black+Hand?content=62141)
Now extract Mac4Lin part 1 somewhere, and then put part 2 in the new folder. You should be able to extract them by judt double-clicking them and using Archive Manager.

Now, to Installation!

First, go to System => Preferences => Appearance. In this window, click the install button.

Now, in the new window navigate to your Mac4lin Folder, Then the the GTK Metacity theme, then choose Mac4Lin GTK 0.4

Now repeat this for the 3 other files in that directory.

Once done, click install again,then click Mac4Lin Icons ARCHIVE. The Archive is the Mac4Lin_Icons_v0.3a**.tar.gz** file. **Don't extract the folders from the archive**, you need to use the actual Archive.

Finally, the cursors. In gutsy, you should be able to just go Install, then choose the archive. But in Hardy, for some reason, I needed to install them manually:

Press Alt+F2 &#8211; This opens the 'Run' dialog, which lets you run terminal commands without the terminal.
Type in ```
gksudo nautilus
```. This tell the computer to run the file browser nautilus as root &#8211; the gk before sudo is used for graphical applications. Enter your password and then navigate to /usr/share/icons. This is where icons and Cursors are kept. In another window, extract the cursors a directory, then copy that directory (the Shere_Khan_X one that was extracted) into the root nautilus folder. Re-open the appearance folder. Time to apply those themes!

Click the Customize button. Now scroll through the list and click Mac4lin_GTK_v0.4, or the graphite one if it takes your fancy. Next go to the Window Border tab and click the corresponding Mac4Lin theme. Now on the Icons tab, click the Leopard Mac4Lin Icons. Finally, goto the cursors tab and click Shere_Khan_X. And there you have it! Welcome to Mac4Lin!

But the window borders could be better. If you're using Hardy, you need to install emerald &#8211; gutsy users should have installed it before. Just type ```
sudo apt-get install emerald
``` into a terminal. To install the theme, go to System=>Preferences=>Emerald Theme Manager. Click Import... and navigate to your Mac4Lin folder, then the Emerald Theme folder. Click the corresponding theme &#8211; Traffic Lights or Graphite. Finally we need to run emerald. Press Alt+F2 and this time type ```
emerald &#8211;replace
```This tells emerald to replace the existing window decorator. Now you should have better window decorations.

If you want to get the right-hand button to shade, not bring up the menu then we need to edit the theme. Go back to Emerald Theme Manager, and click the Edit Themes tab. Now go to the Titlebar tab, and look at the Title-bar Object layout. Change the text here to ```
C(5)N(5)X:(5)T:SM:OSX Layout
``` This simply uses the shade button, not the menu button. Another addition I like is putting the window icon next to the window text, to do this just put I in before the T:SM.

AWN Dock theme and switching scripts coming soon. A you can see, being this thorough requires a lot of effort.

---

### Post by criptonite on 2008-04-27
Hi, what a brilliant set of instructions.  Even though I'm a relative newbie I could follow them very easily...all except for one part (definitely down to my lack on knowledge though).

"Once done, click install again,then click Mac4Lin Icons ARCHIVE. Don't extract the folders, as you need to use the Archive."

 Is the Mac4Lin icons archive the folder called Mac4Lin_icons_v.04?  If I just click on it, nothing happens.  if I double click on I have lots of other folders that I still don't know what to do with.

Excuse my stupidness.

I have an almost total mac look now, just now icons.  It look great.  Thanks!

---

### Post by nuclearpidgeon on 2008-04-28
> **criptonite said:**
> Hi, what a brilliant set of instructions.  Even though I'm a relative newbie I could follow them very easily...all except for one part (definitely down to my lack on knowledge though).

"Once done, click install again,then click Mac4Lin Icons ARCHIVE. Don't extract the folders, as you need to use the Archive."

 Is the Mac4Lin icons archive the folder called Mac4Lin_icons_v.04?  If I just click on it, nothing happens.  if I double click on I have lots of other folders that I still don't know what to do with.

Sorry, I'll edit that soon. An *archive* is a single file that contains compressed file. There are lots of different types of archives - common linux ones are foobar.tar.gz, foobar.tar, foobar.gz, foobar.zip etc. (foobar is just a  wildcard used to represent the file's name)
> **criptonite said:**
> Excuse my stupidness.

Don't worry mate - I was at your stage once too. That's why I wrote this howto!

---

### Post by metrorat on 2008-04-28
Ahoyhoy  - nice howto, I'd already got the mac look from the Mac4Lin site but I was hoping you might be able to help me iron out a few glitches.  I'm running Hardy with compiz/emerald and *almost* everything looks the part.  Problem is that some program windows do not seem to accept the window theme.  Firefox & Rhythmbox look lovely but Firestarter and Synaptic (amongst others) retain a crappy Gnome-esque look within the emerald (OSX-esque) window borders.  Any help on this? 

Also I'd like to replace the logout icon that comes with Mac4Lin (it sucks) but not affect any of the other icons in the theme.  Is this possible?  I've found a few other threads posing similar questions but no solution as yet.

Cheers...

---

### Post by metrorat on 2008-04-28
Here are a couple of screenshots so you can see what I mean...

---

### Post by nuclearpidgeon on 2008-04-29
> **metrorat said:**
> Ahoyhoy  - nice howto, I'd already got the mac look from the Mac4Lin site but I was hoping you might be able to help me iron out a few glitches.  I'm running Hardy with compiz/emerald and *almost* everything looks the part.  Problem is that some program windows do not seem to accept the window theme.  Firefox & Rhythmbox look lovely but Firestarter and Synaptic (amongst others) retain a crappy Gnome-esque look within the emerald (OSX-esque) window borders.  Any help on this? 

Also I'd like to replace the logout icon that comes with Mac4Lin (it sucks) but not affect any of the other icons in the theme.  Is this possible?  I've found a few other threads posing similar questions but no solution as yet.

Cheers...

The 1st problem is to do with the theme file. I dunno how to fix it, but try asking somewhere to do with theming, or Mac4Lin. They just haven't applied the regular theme to the 'root' user.

Changing the icons is easy - i've done it myself so that the nm-applet icons are the curved bars. Just extract the icons folder somewhere, then search for the icon, modify it, re zip the archive and re-install the icons (uninstall the old first)

---

### Post by metrorat on 2008-04-29
Thanks for the advice np... Found a solution to the root theme prob:
```
sudo ln -s /home/<insert your username here>/.themes /root/.themes
sudo ln -s /home/<insert your username here>/.icons /root/.icons
```
Linking the theme and icon directories from your home dir to root's works a treat for me.  I also found some advice to copy your current theme file from ~/.themes to /usr/share/themes but this did not work for me.  Linking also seems like a neater solution.

Soon I shall be rid of that pesky icon and all shall be well... for now.

---

### Post by nuclearpidgeon on 2008-04-29
> **metrorat said:**
> Thanks for the advice np... Found a solution to the root theme prob:
```
sudo ln -s /home/<insert your username here>/.themes /root/.themes
sudo ln -s /home/<insert your username here>/.icons /root/.icons
```

No need to use <insert your username here>, just use the '~' (tilda).
In terminal the ~ represents the home directory (of the current user). Might find that handy.
> 
Soon I shall be rid of that pesky icon and all shall be well... for now.

Good for you :mrgreen:

---

