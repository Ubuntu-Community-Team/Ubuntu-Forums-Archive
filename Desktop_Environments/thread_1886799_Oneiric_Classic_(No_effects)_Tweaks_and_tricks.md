---
title: "Oneiric Classic (No effects) Tweaks and tricks"
date: 2011-11-25
forum: Desktop Environments
---

### Post by kansasnoob on 2011-11-25
**This guide is only for Ubuntu Oneiric/11.10, for Ubuntu Precise/12.04LTS please look here:**

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

***************

Before beginning please understand that I'm no genius, far from it, but only about three weeks ago I inquired at "Ubuntu +1 (Precise Pangolin)" about the sustainability of [a thread to discuss 'gnome-session-fallback']("http://ubuntuforums.org/showthread.php?t=1870612"). The response should be apparent because one of the mods thereafter started the [Gnome Classic Megathread]("http://ubuntuforums.org/showthread.php?t=1873765") , but that's only for Precise! After only about two weeks of playing with "Classic (No effects)" in Precise I was shocked at just how easy it was to get really close to a classic look and feel, so I decided to have a play with "Classic (No effects)" in Oneiric. 

I'm now fairly satisfied with the results, so I felt it was time to share what I've learned about setting up a Oneiric Classic (No effects) DE. **My focus has been on Classic (No effects) only** because I've never cared for compiz anyway and from what I've read it seems to be difficult to get it to run in a classic Oneiric DE. So, **[COLOR="Red"]if you want compiz this particular post is NOT for you[/COLOR]**, sorry. However I see someone has tried to [expand on using Compiz in Oneiric Classic]("http://mandriver.users.sourceforge.net/classic-gnome-guide.html").

I've tested this quite a bit, but only with fresh, **fully updated** Ubuntu Oneiric installs. Your mileage may vary with installations that have other underlying problems. I can only say that it works for me, no more and no less. **[COLOR="Red"]There are no guarantees![/COLOR]** Please DO read this all before beginning and **remember it's only for Ubuntu Oneiric**. I'll try my best to answer any questions but ultimately **[COLOR="Red"]if you break it you own it![/COLOR]** 

Additionally I'd ask that everyone do their best to keep this thread on track. My only intent is to share what little I've learned, not to express an opinion regarding any specific desktop environment or distro. Opinions and general chit-chat belong at the Community Cafe or Testimonials & Experiences. I will not hesitate to ask the mods to move off-topic or inflammatory posts!

************

**[COLOR="Red"]Important warning[/COLOR]**: Some of the changes made here **[COLOR="Red"]can and will break Unity[/COLOR]** so I highly recommend first testing this either in a virtual machine or a multi-boot. I personally prefer an actual multi-boot but that's just a matter of choice.

Another safe way to try this would be to create a new user account with administrative rights, that way the configuration files you change will only effect that new account. It's actually quite simple to create a new user account:

[https://help.ubuntu.com/11.10/ubuntu-help/user-accounts.html](https://help.ubuntu.com/11.10/ubuntu-help/user-accounts.html)

Then if you decide to apply the changes to your original user account the needed PPA's and packages will already be installed, so you'll only need to complete those steps needed to obtain the desired configuration. And then the new user account could be deleted.

************

**[COLOR="Red"]Important note[/COLOR]**: This guide is almost totally reliant on copy-n-pasting commands into gnome-terminal. Why? Quite simply not ALL of this can be completed using GUI tools like Ubuntu Tweak or 'gnome-tweak-tool', and installing 'gnome-tweak-tool' results in installing a great deal of unneeded packages including 'gnome-shell', and my only concern is getting a "classic w/o effects" DE running efficiently. Should someone care to use either Ubuntu Tweak or 'gnome-tweak-tool' I have no problem with that, I just prefer the CLI.

But copying and pasting commands that are "wrapped" in code tags couldn't be simpler as I explained here:

[http://ubuntuforums.org/showpost.php?p=11459388&postcount=160](http://ubuntuforums.org/showpost.php?p=11459388&postcount=160)

Also, if I didn't include "sudo" in the command then it's not needed, and in rare instances may result in changed permissions, so please just copy-n-paste! If something appears to fail please copy the full output from the terminal and paste it into a reply here along with an explanation and I'll try my best to help you.

Note: If a "step" can be performed using Ubuntu Tweak and/or 'gnome-tweak-tool' I will mention it briefly at the end of that individual step.

************

First let's look at what I ended up with and then I'll explain how I got there:

[ATTACH]207947[/ATTACH]

You'll notice that I prefer only one panel at the bottom. I realize some may want two panels, or one at the top only, it's purely a matter of preference. Be patient and I'll do my best to explain things. Just FYI my panel layout (beginning from the left) consists of:

Hide button/Main Menu/Terminal/Workspace Switcher/Screenshot/Opera/Firefox/Window List/_________/CPU Frequency Scaling Monitor/Caffeine/Indicator Applet/Clock/Trash/Hide button

And you'll notice that the Indicator Applet displays: /Update notifier/System Monitor Indicator/Hardware Sensors Indicator/Network widget/Mail widget/Volume widget

And this is as good a time as any to pause and discuss changes to the menu(s) and panel(s). You'll notice that the menu(s) have changed as shown in a later screenshot, but I think you'll likely find what you want if you just spend a couple of minutes familiarizing yourself with the new menu layout, be sure to check the Other, Accessories, and System Tools > System Settings categories. You'll find most of what you were used to seeing in System > Administration and System > Preferences is now just relocated.

You also need to know that you must now hold down either Alt key while right-clicking on a panel or applet to be able to edit panel preferences or to add/edit/move/remove more applets. That was an intentional move by the Gnome devs to prevent people from unintentionally breaking things. And you also can't just add application applets by right-clicking them and selecting "add to panel" anymore. You must now open the "add-to-panel" window and select Application Launcher > Forward, then the window changes and you can click on the "bullet" to the left of each category to display and add any app in the menu to the panel:

[ATTACH]207948[/ATTACH]

But lets also look at Panel Properties settings. Note here that in Panel Properties > Background I've found that 'Solid color' > Color > Color name #3F3E39 / Style > Opaque results in vastly improved appearance of the Workspace Switcher, a picture's worth a thousand words:

[ATTACH]207949[/ATTACH]

To be perfectly honest I now forget I'm even using Gnome 3 most of the time other than learning the new keyboard shortcuts which still confuse me. I do know that Ctrl + Alt + T launches gnome-terminal but even it can be fiddly. I suspect that the new keybindings are truly designed for Gnome Shell, not the "fallback" DE, which I expect to see disappear altogether eventually (hopefully not before the release of Precise Pangolin though).

************

Now it's time to move on to how I got there, one step at a time.

**Step #1**: We simply need to install 'gnome-session-fallback' which is already in the Ubuntu repos:

```
sudo apt-get install gnome-session-fallback

```
************

**Step #2**: You'd quickly find that 'indicator-applet', 'indicator-applet-complete', and 'indicator-applet-session' are lacking in "Add to panel". You'll really need either 'indicator-applet' or 'indicator-applet-complete' to display some of the notifications such as mail, the hardware sensors and/or system monitor indicators, and the update-notifier. (I personally only use 'indicator-applet' but we all have individual preferences). So we need to install [Jason Conti's PPA]("https://launchpad.net/~jconti/+archive/gnome3") and our first additional packages:

```
sudo add-apt-repository ppa:jconti/gnome3
```

```
sudo apt-get update
```

```
sudo apt-get install indicator-applet indicator-applet-complete indicator-applet-session

```
When that is complete it's time to take your first look at the new "classic" DE by simply logging out, then clicking on the "gear" to the right of your user name on the login screen, selecting Classic (No effects), entering your password, and logging back in. You'll hopefully see this:

[ATTACH]207950[/ATTACH]

************

Now, before continuing, please understand that **all of these additional steps are optional**. No two people want the exact same look, feel, or function out of a DE! This is just what I wanted. Pick and choose to suit your own desires.

************

**Step #3**: I quickly realized that the purple background of the terminal was killing my eyes so in terminal I clicked Edit > Profile Preferences > Colors and unticked the "Use colors from system theme" box. Then, in the same window, I clicked on the color block next to "Background color" and used the eyedropper to set the background to white. Ahhhh, much easier on the eyes.

************

**Step #4**: I found the screen lock thing very annoying, I live alone and don't like having to enter my password everytime the screen-"blanker" acivates. So you can just go to System Tools > System Settings > Screen and select Lock = Off. (I call it a screen-"blanker" mostly as a joke because it hardly resembles a screensaver anymore).

************

**Step #5**: Even after setting Lock to Off I found it annoying to have the screen-"blanker" activate while trying to watch videos or such. In Gnome 2 I used to be able to use 'gnome-inhibit-applet' but it's not available in Gnome 3. No worries, I found a very good replacement, Caffeine:

[https://launchpad.net/~caffeine-developers/+archive/ppa](https://launchpad.net/~caffeine-developers/+archive/ppa)

In my original screenshot the caffeine applet shows up next to the indicator-applet. I find it to be a sweet replacement for the old 'gnome-inhibit-applet'. Once installed and set up it allows you to "inhibit" the screen-"blanking", I think a picture is worth a thousand words so here:

[ATTACH]207951[/ATTACH]

Should you choose to install it you can setup Caffeine by going to Other > Caffeine preferences. Installation is easy:

```
sudo add-apt-repository ppa:caffeine-developers/ppa

```
```
sudo apt-get update
```

```
sudo apt-get install caffeine
```

Note: This works equally well in Unity.

************

**Step #6**: In Unity the update-notifications now show up in the Launcher but without the Launcher we now get no persistent update notifications. Still no worries, I got it to show up in either 'indicator-applet' or 'indicator-applet-complete' in gnome-panel by running the command:

```
gsettings set com.ubuntu.update-notifier auto-launch false
```

You can revert that by running:

```
gsettings set com.ubuntu.update-notifier auto-launch true
```

************

**Step #7**: I really liked using either 'gnome-sensors-applet' or 'computertemp' to display system temps in the panel but again they're not available with Gnome 3. Again no worries, Hardware Sensors Indicator comes to the rescue:

[https://launchpad.net/~alexmurray/+archive/indicator-sensors](https://launchpad.net/~alexmurray/+archive/indicator-sensors)

More about that here:

[http://ubuntuforums.org/showpost.php?p=11492701&postcount=4](http://ubuntuforums.org/showpost.php?p=11492701&postcount=4)

To install just run these three commands:

```
sudo add-apt-repository ppa:alexmurray/indicator-sensors
```

```
sudo apt-get update
```

```
sudo apt-get install indicator-sensors
```

It then shows up in System Tools > Hardware Sensors Indicator. After launching it the first time you must click on the new "applet" which just says "No active sensors" and click on Preferences. From there you can select which sensors to display and other options.

************

**Step #8**: It's also sometimes nice to display CPU and memory usage in the panel, so here's System Monitor Indicator:

[https://launchpad.net/indicator-sysmonitor](https://launchpad.net/indicator-sysmonitor)

More about it here:

[http://ubuntuforums.org/showpost.php?p=11473552&postcount=208](http://ubuntuforums.org/showpost.php?p=11473552&postcount=208)

To install just run these three commands:

```
sudo add-apt-repository ppa:alexeftimie/ppa
```

```
sudo apt-get update
```

```
sudo apt-get install indicator-sysmonitor
```

It then shows up in Accessories > System monitor indicator. Do not confuse it with System Monitor in System Tools. I think setting it up is almost self explanatory.

************

**Step #9**: 
I found the overlay-scrollbars to be inconsistent and annoying in the classic DE and I'd previously recommended just removing them altogether but I believe I've found a much better way to disable them on a per-user basis. Simply run one command:

```
echo export LIBOVERLAY_SCROLLBAR=0 >> ~/.xprofile
```

Then just log out and log back in for that change to take effect.

If you should later wish to revert that just run:

```
sed -i 's/^export LIBOVERLAY_SCROLLBAR.*/#&/' ~/.xprofile
```

************

**Step #10**: At this point I decided the window-management buttons really needed to be back on the right so I ran:

```
gconftool-2 --set "/apps/metacity/general/button_layout" --type string ":minimize,maximize,close"
```

Note: to restore the defaults run:

```
gconftool-2 --set "/apps/metacity/general/button_layout" --type string "close,minimize,maximize:"
```

Note: This step (#10) can also be performed using Ubuntu Tweak.

************

**Step #11**: At this point I'm fairly happy but the scrollbar color is hard on my eyes. It's like trying to differentiate between two shades of white. I'd really prefer having the scrollbars match the dark gray panel or window title-bar with a white background but I haven't been able to figure that out yet. The best alternative I've found so far is changing the metacity and gtk themes this way:

```
sudo add-apt-repository ppa:webupd8team/themes
```

```
sudo apt-get update
```

```
sudo apt-get install shiki-colors-metacity-theme zukitwo-dark-gtk-theme
```

```
gconftool-2 -s --type string /apps/metacity/general/theme Shiki-Colors-Metacity
```

```
gsettings set org.gnome.desktop.interface gtk-theme Zukitwo-Dark
```

I found that fairly pleasing to my eyes (it also replaced the drastic orange with a nice grayish-blue and I like the "retro" look of the window management buttons) but if you should decide to revert to the default Ambiance themes just run:

```
gconftool-2 -s --type string /apps/metacity/general/theme Ambiance
```

```
gsettings set org.gnome.desktop.interface gtk-theme Ambiance
```

Note: Both Ubuntu Tweak and 'gnome-tweak-tool' can be used for applying themes, but NOT installing themes.

I'm very open to suggestions about theming, this is simply the best combo I've come up with so far.

************

**Step #12**: I also dislike the missing menu and button icons so I run:

```
gsettings set org.gnome.desktop.interface menus-have-icons true
```

```
gsettings set org.gnome.desktop.interface buttons-have-icons true
```

Note: This step (#12) can also be performed using Ubuntu Tweak.

************

**Step #13**: This one is the hardest for me to explain. By default the Oneiric desktop is set to NOT display any icons, but it's possible for the desktop to display any combination of these icons/"actors":

```
Computer...........(computer-icon-visible)
Home...............(home-icon-visible)
Network............(network-icon-visible)
Trash..............(trash-icon-visible)
Mounted volumes....(volumes-visible)
```

But to do so you must first set the "stage" by running:

```
gsettings set org.gnome.desktop.background show-desktop-icons true
```

But that only sets the stage for the actors, now you must decide which actors you want on the stage. You're now the director.

After running that command either reboot or log out and log back in. When you get back to a blank DE background decide what you want displayed. (Hint, the "true" or "false" at the end of these commands is the key):

To show the Computer icon run:

```
gsettings set org.gnome.nautilus.desktop computer-icon-visible true
```

To hide the Computer icon run:

```
gsettings set org.gnome.nautilus.desktop computer-icon-visible false
```

To show the Home icon run:

```
gsettings set org.gnome.nautilus.desktop home-icon-visible true
```

To hide the Home icon run:

```
gsettings set org.gnome.nautilus.desktop home-icon-visible false
```

To show the Network icon run:

```
gsettings set org.gnome.nautilus.desktop network-icon-visible true
```

To hide the Network icon run:

```
gsettings set org.gnome.nautilus.desktop network-icon-visible false
```

To show the Trash icon run:

```
gsettings set org.gnome.nautilus.desktop trash-icon-visible true
```

To hide the Trash icon run:

```
gsettings set org.gnome.nautilus.desktop trash-icon-visible false
```

To show Mounted Volumes run:

```
gsettings set org.gnome.nautilus.desktop volumes-visible true
```

To hide Mounted Volumes run:

```
gsettings set org.gnome.nautilus.desktop volumes-visible false
```

Note: This step can also be performed using either Ubuntu Tweak or 'gnome-tweak-tool'.

************

**Step #14**: You may or may not find that you need to disable the Firefox and/or Thunderbird global menu add-ons. It seems to depend on the panel configuration, but I'm not quite sure. To do so in Firefox just go to Tools > Add-ons > Global Menu Bar integration and select Disable. You'll then be prompted to restart Firefox. I don't use Thunderbird so I can't be sure of the specific procedure with it, but I'd think it's similar.

**Update**: If you use only a bottom panel as I do you may notice after updates on Feb. 17, 2012 that the Unity top panel (aka: menu bar) is back on the desktop. This was also a problem immediately after the release of Oneiric but it was fixed shortly thereafter. This time I decided to actually kill it for good :)

I did so with one command:

```
sudo apt-get purge appmenu-gtk appmenu-qt indicator-appmenu appmenu-gtk3
```

Then just log out and log back in.

************

**Step #15**: Thanks to [Flynsarmy]("http://www.flynsarmy.com/2011/11/how-to-make-ubuntu-11-10-more-usable/") I've discovered another useful tweak. In Gnome 3 the "prescribed" method of launching the terminal is 'Ctrl+Alt+T' but I've found it to be fiddly and somewhat unreliable, like sometimes it either doesn't work or it launches multiple terminals. That post showed me how to get the "Run Command Prompt" back by pressing Alt+F2 just as it was in Gnome 2, and I love it.

It really couldn't be much simpler, just go to Applications > System Tools > System Settings > Keyboards > Shortcuts > System and highlight the line that says "Show the run command prompt". Then position the mouse pointer over where it says "Disabled" and left-click the mouse. Then you'll see "Disabled" change to "New shortcut". Then just press Alt+F2 and you'll see that change as you do so, while actually launching the classic run command prompt for the first time.

************

That's it for now. I hope others will share their favorite Oneiric classic tips and tricks. I'll be glad to edit this and add links to other threads or posts related to Oneiric classic. Maybe someone can even share how they got classic to run with Compiz since that's not my thing.

I recently realized that I left out **credit where credit is due**. I certainly owe a large number of other Ubuntu end users and early testers a debt of gratitude, along with the developers of the "add-on" apps/applets discussed here, but [the webupd8 team]("http://www.webupd8.org/") has been invaluable at providing not only great information but also providing the theme PPA needed to perform step #11.

I hope NOT to blow up too many computers.

---

### Post by arpanaut on 2011-11-26
Very Well Done!
Will be very helpful to those who prefer the traditional desktop.
I will be using this for my visually impaired nephew's rig when the 12.04 move is necessary.
I stick with LTS on his machine and was not looking forward to the huge transition Unity presents for him.
Thanks for doing the "heavy lifting" for me.

---

### Post by sammiev on 2011-11-26
This is great. I'm happy with gnome3 and unity but I'm sure many users will be trying out your setup. Thanks for all your hard work as I just had to add a well deserved comment. :popcorn:

---

### Post by kansasnoob on 2011-11-27
More about Hardware Sensors Indicator (largely because of the five screenshot limit), once installed it shows up in System Tools:

[ATTACH]208061[/ATTACH]

Once you click on that it launches in the panel, then clicking on the "applet" allows you to set the preferences as shown here:

[ATTACH]208062[/ATTACH]

I think it's pretty simple to figure out :)

It works equally well in Unity, enjoy. And many thanks to [Alex Murray]("https://launchpad.net/~alexmurray/+archive/indicator-sensors").

---

### Post by rewyllys on 2011-11-27
@kansasnoob

Wonderful post!:popcorn:

Many, many thanks!!

---

### Post by cmcanulty on 2011-11-28
Wow now I am back with Ubuntu, Thanks!!!I wish I had the skills to help. 2 issues- my screen still dims all the way at login or restart and I still can't get a large black cursor. Black shows as an option in advanced settings but doesn't work.Also there seems no way to configure advanced user settings. I run 10 library machines and need to set the options a certain way to protect our system.Hopefully this could become a new buntu called gnubuntu? Because is there was an easy option to do all this at install lots of people would opt for it.

---

### Post by kansasnoob on 2011-11-28
> **cmcanulty said:**
> Wow now I am back with Ubuntu, Thanks!!!I wish I had the skills to help. 2 issues- my screen still dims all the way at login or restart and I still can't get a large black cursor. Black shows as an option in advanced settings but doesn't work.Also there seems no way to configure advanced user settings. I run 10 library machines and need to set the options a certain way to protect our system.Hopefully this could become a new buntu called gnubuntu? Because is there was an easy option to do all this at install lots of people would opt for it.

I'm preparing for Precise Alpha 1 iso-testing here so I might not be very responsive until after the 1st. I'll have to study the large black cursor thing a bit because I've always just used the default, but what you're describing about the screen dimming during boot and shutdown sounds like it could be graphics card related.

Like On my AMD/nVidia box I'm using a 22" wide-screen LCD monitor and I'll get an "out-of-range" error until I've tweaked the "plymouth/splash" resolution settings. So, when you have time, it would be helpful to see the output of:

```
lspci | grep VGA
```

That'll tell me what graphics chip you have :)

I'm not altogether sure what you mean by "advanced settings" either. Maybe you could be a bit more descriptive?

I certainly want to try and help you, but be patient. I love librarians and teachers :)

BTW I have no desire to create or even participate in a "respin" of Ubuntu. I assume, and hope, that the gnome "fallback" session will still be alive in Precise. That would be awesome because Precise is not only an LTS, but the desktop version is going to be supported for 5 years just like the server version.

That will allow a full five years for both Unity and Gnome Shell to evolve and gain acceptance. I'm not doing this because I hate the new DE's. I'm perfectly happy with Unity on my 18.5" monitor and with Lubuntu on the 22" but I recognized a need so I decided to see what I could do.

I do need to add a bit to that initial post, something like "Advanced user tips", about how to shorten the procedure but I wanted to get something up so users could share their favorite tweaks and also share any problems they have with any specific tip.

I'd almost bet a year or so from now we'll all laugh about all of the hoopla over the changes in Ubuntu and Gnome. Change is always controversial.

---

### Post by cmcanulty on 2011-11-28
Kansas, Thanks for all your work. I misspoke- the screen control is in sys settings & controls brightness. I can raise it to high but with every reboot or logout it is again dim.I tried several tweaks but they didn't work in fact they made the screen brightness slider stay on min and grayed out.The only way out of that was reinstall several times. I spent a lot of time today following numerous threads on the screen dimming issue but no good solutions. I really can't go forward until that is fixed as the librarian would have to constantly get up and show people how to undim the computers.On the mouse it always worked until 11.10 now the option for color is there but doesn't work. The sizing option is gone. I am running a new this year HP G72t laptop. I bought it  from linux city as they had a good price and sold them with linux so I knew it would work which it did well until this issue with 11.10. It has 4GB Ram, 500GB hard drive. The graphics is VGA compatible controller-Intel Corp integrated graphics controller (rev 2) (prog-if 00 [VGA controller]subsystem Hewlett Packer Device 1439. I also tried mint 12 and Ubuntu 10 with unity, classic, and xfce all have the dim issue. Numerous others have this problem with many varied laptops. I sure would love if we could get the classic in 12.04 and have it 5 years. I am sure gnome 3 will eventually get tweaked enough to be useful for work but so far it is a mess and most of the themes don't even work.I am happy to help on this project though I am no expert. So far I have tried a acpi tweak, editing various etc and local files but nothing worked. Other than that issue classic is fine with me though it also lost sound on an older desktop I upgraded yesterday. I won't upgrade the lib machine until it is dead solid and the dimness issue is gone.On a cheerful note I fixed up a real old laptop for a little girls birthday today with xubuntu and it works great and wireless even works with 512 RAM so she is happy. Took me many hours to get the dinosaur going smoothly.

---

### Post by kansasnoob on 2011-12-01
> **cmcanulty said:**
> Kansas, Thanks for all your work. I misspoke- the screen control is in sys settings & controls brightness. I can raise it to high but with every reboot or logout it is again dim.I tried several tweaks but they didn't work in fact they made the screen brightness slider stay on min and grayed out.The only way out of that was reinstall several times. I spent a lot of time today following numerous threads on the screen dimming issue but no good solutions. I really can't go forward until that is fixed as the librarian would have to constantly get up and show people how to undim the computers.On the mouse it always worked until 11.10 now the option for color is there but doesn't work. The sizing option is gone. I am running a new this year HP G72t laptop. I bought it  from linux city as they had a good price and sold them with linux so I knew it would work which it did well until this issue with 11.10. It has 4GB Ram, 500GB hard drive. The graphics is VGA compatible controller-Intel Corp integrated graphics controller (rev 2) (prog-if 00 [VGA controller]subsystem Hewlett Packer Device 1439. I also tried mint 12 and Ubuntu 10 with unity, classic, and xfce all have the dim issue. Numerous others have this problem with many varied laptops. I sure would love if we could get the classic in 12.04 and have it 5 years. I am sure gnome 3 will eventually get tweaked enough to be useful for work but so far it is a mess and most of the themes don't even work.I am happy to help on this project though I am no expert. So far I have tried a acpi tweak, editing various etc and local files but nothing worked. Other than that issue classic is fine with me though it also lost sound on an older desktop I upgraded yesterday. I won't upgrade the lib machine until it is dead solid and the dimness issue is gone.On a cheerful note I fixed up a real old laptop for a little girls birthday today with xubuntu and it works great and wireless even works with 512 RAM so she is happy. Took me many hours to get the dinosaur going smoothly.

Both of my LCD monitors are Hanns-G and I don't even get the "dimming" option in System Settings so I'm clueless on that issue :(

---

### Post by cmcanulty on 2011-12-01
Thanks again I reinstalled and have it pretty clean now but still no fix for screen dimming issue. I sure hope we can continue this in 12.04 as that is LTS and would go 5 years. By then who knows what a desktop will be.

---

### Post by cmcanulty on 2011-12-03
I got the brightness issue fixed with this thread I found after like weeks of work, shouldn't be that hard but now I can go forward and upgrade all the library laptops, whew!
[http://forums.linuxmint.com/viewtopic.php?f=42&t=45271]("http://forums.linuxmint.com/viewtopic.php?f=42&t=45271")

---

### Post by kansasnoob on 2011-12-03
> **cmcanulty said:**
> I got the brightness issue fixed with this thread I found after like weeks of work, shouldn't be that hard but now I can go forward and upgrade all the library laptops, whew!
[http://forums.linuxmint.com/viewtopic.php?f=42&t=45271]("http://forums.linuxmint.com/viewtopic.php?f=42&t=45271")

Awesome! I'll try to watch for others having such issues and pass it along.

---

### Post by bossltr on 2011-12-04
hey thanks for this work and explanation very helpful
Brian :guitar:

---

### Post by cmcanulty on 2011-12-04
Only thing I still can't fix is getting large cursor should be easy but nothing I've tried has worked. But I am am so happy to be able to upgrade the library machines now so thank you

---

### Post by ale.mlow on 2011-12-13
helped a lot, i used almost everything! thank you!

---

### Post by cmcanulty on 2011-12-14
Of the library machines I run all but 3 are not dimming the screen- I have to fix this. I am considering copying the entire etc directory on one of the no screen dim issue laptops to the ones that are still dimming. 2 questions 1)is this safe to do-all are identical machines 2) is there any other file location outside of /etc that could cause this?

---

### Post by kansasnoob on 2011-12-14
> **cmcanulty said:**
> Of the library machines I run all but 3 are not dimming the screen- I have to fix this. I am considering copying the entire etc directory on one of the no screen dim issue laptops to the ones that are still dimming. 2 questions 1)is this safe to do-all are identical machines 2) is there any other file location outside of /etc that could cause this?

Since I've never had that problem the simple answer is that I don't know :(

I wish I could be more help regarding that but I just don't know. Is the issue the same regardless of DE used?

Or does it work OK with Unity, but not with "Classic (no effects)"?

---

### Post by cmcanulty on 2011-12-14
yes the same with unity, classic, mint, xfce but was never an issue before 11.10

---

### Post by ttoolin on 2011-12-14
Thank you for your hard work on this document.  It is a very informative guide.

---

### Post by droa on 2011-12-28
thanks a lot

---

### Post by VanillaMozilla on 2012-01-12
Just one critical question:  Will gnome-session-fallback continue to be supported?

---

### Post by tenkoji on 2012-01-12
hi nice thread, im(atom processor with very small screen) uuh..just trying to keep my performance high with no effects(seriously after the minute i reboot for upgrading to oneirc, i can feel it's really hot at my touchpad area) but when i press alt-tab/windowkey+tab it'll b able to show me switching between apps

which settings should i try

i also noticed a change when i press windowkey+r im pretty sure i've customised it to pop me a terminal window but now,...please help this lil duck who's still very new to linux...@_@

---

### Post by kansasnoob on 2012-01-13
> **VanillaMozilla said:**
> Just one critical question:  Will gnome-session-fallback continue to be supported?

I'm reasonably confident that it will be in Precise (12.04) which is a 5 year LTS. But I can't be certain until April.

Beyond Precise who knows?

---

### Post by kansasnoob on 2012-01-13
> **tenkoji said:**
> hi nice thread, im(atom processor with very small screen) uuh..just trying to keep my performance high with no effects(seriously after the minute i reboot for upgrading to oneirc, i can feel it's really hot at my touchpad area) but when i press alt-tab/windowkey+tab it'll b able to show me switching between apps

which settings should i try

i also noticed a change when i press windowkey+r im pretty sure i've customised it to pop me a terminal window but now,...please help this lil duck who's still very new to linux...@_@

Well first of all I'd think that you could use either Unity-2D or Classic/no-effects based on your own preferences. I'd think resource usage should be similar between the two.

Going back to my OP the apps described in steps 7 & 8 should be useful in monitoring system temp and cpu/memory usage. They both work equally well in Unity and Classic, but in order to get them to display properly in Classic you'll need to use the versions of either 'indicator-applet' or 'indicator-applet-complete' provided by the PPA shown in step #2.

Just shout if you need more help, but I admittedly don't know much about laptops or notebooks :)

---

### Post by VanillaMozilla on 2012-01-13
We very much appreciate your efforts, Kansas.  If anyone from Canonical or Gnome should ask you, it would be a really smooth move if THEY would take the responsibility to make it work like it used to.  :)

---

### Post by cmcanulty on 2012-02-08
a new issue has cropped up for me, a bit irritating.When I rt click a link the little box pops up with a description and immediately closes before it can be read in firefox. However I have been experimenting with desktops and this only happens in classic. xfce and even cinnamon it stays up to be read as it should. How can I correct this

---

### Post by kansasnoob on 2012-02-08
> **cmcanulty said:**
> a new issue has cropped up for me, a bit irritating.When I rt click a link the little box pops up with a description and immediately closes before it can be read in firefox. However I have been experimenting with desktops and this only happens in classic. xfce and even cinnamon it stays up to be read as it should. How can I correct this

I don't know, it's working fine here:

[ATTACH]212306[/ATTACH]

I suspect something is borked in the firefox profile, but I'm not sure. Do you have a mix of Xubuntu, Cinnamon, and Ubuntu classic all operating on the same OS? Or are they multi-booted? Or on different machines?

You could **close** Firefox, go to Home, select View > Show hidden files, then rename ".mozilla" something like ".mozilla_OLD". Then when you open Firefox again a new .mozilla will be created.

Be darn sure to close Firefox before you try that or you will absolutely bork the old profile!

---

### Post by Imgoing2LearnUbunt2 on 2012-02-25
Hi, I am a new user so I dont know how big my voice is on here but can anyone tell me the cons of this so called 'Unity'. I been a Windows user pretty much most of the time but Ive had linux courses while I was in college, so Ive been exposed to the look and feel of linux, *somewhat. *I just booted up 11.04 and was welcomed by Unity and I have to be honest, I did miss the original way Gnome felt, and just where things were.. However, Unity is or appears, bold and simple and elegant and as if it could be smart to a mac user.... But... I can see where one would ask, does this look limited? 

Im a begginner into Linux but Im here to stay as, My career in IT would def prosper if I mastered Linux and Ive (as of 10 minutes ago) made it my primaryOS. So Im asking, What would you do?:popcorn:

---

### Post by kansasnoob on 2012-02-26
> **Imgoing2LearnUbunt2 said:**
> Hi, I am a new user so I dont know how big my voice is on here but can anyone tell me the cons of this so called 'Unity'. I been a Windows user pretty much most of the time but Ive had linux courses while I was in college, so Ive been exposed to the look and feel of linux, *somewhat. *I just booted up 11.04 and was welcomed by Unity and I have to be honest, I did miss the original way Gnome felt, and just where things were.. However, Unity is or appears, bold and simple and elegant and as if it could be smart to a mac user.... But... I can see where one would ask, does this look limited? 

Im a begginner into Linux but Im here to stay as, My career in IT would def prosper if I mastered Linux and Ive (as of 10 minutes ago) made it my primaryOS. So Im asking, What would you do?:popcorn:

IMHO it's simply a matter of choice. I actually like Unity-2D on my Intel Atom box with an 18.5" widescreen monitor, Lubuntu on my old VIA C-7, and either Lubuntu or a Classic Gnome DE as described in my OP here on my AMD HTPC with a 22" widescreen.

I think you should open a discussion at the Community Cafe and see what other users use and why they use it:

[http://ubuntuforums.org/forumdisplay.php?f=11](http://ubuntuforums.org/forumdisplay.php?f=11)

---

### Post by merlin_zaraza on 2012-03-01
Thanks for this great manual ;)

---

### Post by domsom on 2012-04-02
Thanks for the post - I just used a few of them, but reading Step 15 just wanted me to point out Gnome Do (package is gnome-do, [http://do.davebsd.com/](http://do.davebsd.com/)) to you. It's similar to OSX's highlight search, but customizable with a lot of plugins. In default, you summon it with Win+Space, and you just type whatever you want to launch/open/calculate/search etc. On my box, it's much faster and a lot more useful than Unity's Dash. And as the Win+Space shortcut is incompatible with Unity, it's the main reason I don't want to use Unity.

Disclaimer: I'm not (yet) a contributor to Do ;-)

---

### Post by kansasnoob on 2012-04-02
> **domsom said:**
> Thanks for the post - I just used a few of them, but reading Step 15 just wanted me to point out Gnome Do (package is gnome-do, [http://do.davebsd.com/](http://do.davebsd.com/)) to you. It's similar to OSX's highlight search, but customizable with a lot of plugins. In default, you summon it with Win+Space, and you just type whatever you want to launch/open/calculate/search etc. On my box, it's much faster and a lot more useful than Unity's Dash. And as the Win+Space shortcut is incompatible with Unity, it's the main reason I don't want to use Unity.

Disclaimer: I'm not (yet) a contributor to Do ;-)

Thanks for this info. Personally I'm quite happy with Unity on some of my machines, and Lubuntu on others, but I'm going to need a classic LTS solution for others in Precise so I decided to get started early and just wanted to share what I've learned.

I'll certainly have a look at Gnome Do sometime in the near future.

---

### Post by shshank on 2012-04-15
> **kansasnoob said:**
> Before beginning please understand that I'm no genius, far from it, but only about three weeks ago I inquired at "Ubuntu +1 (Precise Pangolin)" about the sustainability of [a thread to discuss 'gnome-session-fallback']("http://ubuntuforums.org/showthread.php?t=1870612"). The response should be apparent because one of the mods thereafter started the [Gnome Classic Megathread]("http://ubuntuforums.org/showthread.php?t=1873765") , but that's only for Precise! After only about two weeks of playing with "Classic (No effects)" in Precise I was shocked at just how easy it was to get really close to a classic look and feel, so I decided to have a play with "Classic (No effects)" in Oneiric. 

I'm now fairly satisfied with the results, so I felt it was time to share what I've learned about setting up a Oneiric Classic (No effects) DE. **My focus has been on Classic (No effects) only** because I've never cared for compiz anyway and from what I've read it seems to be difficult to get it to run in a classic Oneiric DE. So, **[COLOR=Red]if you want compiz this particular post is NOT for you[/COLOR]**, sorry. However I see someone has tried to [expand on using Compiz in Oneiric Classic]("http://mandriver.users.sourceforge.net/classic-gnome-guide.html").

I've tested this quite a bit, but only with fresh, **fully updated** Ubuntu Oneiric installs. Your mileage may vary with installations that have other underlying problems. I can only say that it works for me, no more and no less. **[COLOR=Red]There are no guarantees![/COLOR]** Please DO read this all before beginning and **remember it's only for Ubuntu Oneiric**. I'll try my best to answer any questions but ultimately **[COLOR=Red]if you break it you own it![/COLOR]** 

Additionally I'd ask that everyone do their best to keep this thread on track. My only intent is to share what little I've learned, not to express an opinion regarding any specific desktop environment or distro. Opinions and general chit-chat belong at the Community Cafe or Testimonials & Experiences. I will not hesitate to ask the mods to move off-topic or inflammatory posts!

************

**[COLOR=Red]Important warning[/COLOR]**: Some of the changes made here **[COLOR=Red]can and will break Unity[/COLOR]** so I highly recommend first testing this either in a virtual machine or a multi-boot. I personally prefer an actual multi-boot but that's just a matter of choice.

Another safe way to try this would be to create a new user account with administrative rights, that way the configuration files you change will only effect that new account. It's actually quite simple to create a new user account:

[https://help.ubuntu.com/11.10/ubuntu-help/user-accounts.html](https://help.ubuntu.com/11.10/ubuntu-help/user-accounts.html)

Then if you decide to apply the changes to your original user account the needed PPA's and packages will already be installed, so you'll only need to complete those steps needed to obtain the desired configuration. And then the new user account could be deleted.

************

**[COLOR=Red]Important note[/COLOR]**: This guide is almost totally reliant on copy-n-pasting commands into gnome-terminal. Why? Quite simply not ALL of this can be completed using GUI tools like Ubuntu Tweak or 'gnome-tweak-tool', and installing 'gnome-tweak-tool' results in installing a great deal of unneeded packages including 'gnome-shell', and my only concern is getting a "classic w/o effects" DE running efficiently. Should someone care to use either Ubuntu Tweak or 'gnome-tweak-tool' I have no problem with that, I just prefer the CLI.

But copying and pasting commands that are "wrapped" in code tags couldn't be simpler as I explained here:

[http://ubuntuforums.org/showpost.php?p=11459388&postcount=160](http://ubuntuforums.org/showpost.php?p=11459388&postcount=160)

Also, if I didn't include "sudo" in the command then it's not needed, and in rare instances may result in changed permissions, so please just copy-n-paste! If something appears to fail please copy the full output from the terminal and paste it into a reply here along with an explanation and I'll try my best to help you.

Note: If a "step" can be performed using Ubuntu Tweak and/or 'gnome-tweak-tool' I will mention it briefly at the end of that individual step.

************

First let's look at what I ended up with and then I'll explain how I got there:

[ATTACH]207947[/ATTACH]

You'll notice that I prefer only one panel at the bottom. I realize some may want two panels, or one at the top only, it's purely a matter of preference. Be patient and I'll do my best to explain things. Just FYI my panel layout (beginning from the left) consists of:

Hide button/Main Menu/Terminal/Workspace Switcher/Screenshot/Opera/Firefox/Window List/_________/CPU Frequency Scaling Monitor/Caffeine/Indicator Applet/Clock/Trash/Hide button

And you'll notice that the Indicator Applet displays: /Update notifier/System Monitor Indicator/Hardware Sensors Indicator/Network widget/Mail widget/Volume widget

And this is as good a time as any to pause and discuss changes to the menu(s) and panel(s). You'll notice that the menu(s) have changed as shown in a later screenshot, but I think you'll likely find what you want if you just spend a couple of minutes familiarizing yourself with the new menu layout, be sure to check the Other, Accessories, and System Tools > System Settings categories. You'll find most of what you were used to seeing in System > Administration and System > Preferences is now just relocated.

You also need to know that you must now hold down either Alt key while right-clicking on a panel or applet to be able to edit panel preferences or to add/edit/move/remove more applets. That was an intentional move by the Gnome devs to prevent people from unintentionally breaking things. And you also can't just add application applets by right-clicking them and selecting "add to panel" anymore. You must now open the "add-to-panel" window and select Application Launcher > Forward, then the window changes and you can click on the "bullet" to the left of each category to display and add any app in the menu to the panel:

[ATTACH]207948[/ATTACH]

But lets also look at Panel Properties settings. Note here that in Panel Properties > Background I've found that 'Solid color' > Color > Color name #3F3E39 / Style > Opaque results in vastly improved appearance of the Workspace Switcher, a picture's worth a thousand words:

[ATTACH]207949[/ATTACH]

To be perfectly honest I now forget I'm even using Gnome 3 most of the time other than learning the new keyboard shortcuts which still confuse me. I do know that Ctrl + Alt + T launches gnome-terminal but even it can be fiddly. I suspect that the new keybindings are truly designed for Gnome Shell, not the "fallback" DE, which I expect to see disappear altogether eventually (hopefully not before the release of Precise Pangolin though).

************

Now it's time to move on to how I got there, one step at a time.

**Step #1**: We simply need to install 'gnome-session-fallback' which is already in the Ubuntu repos:

```
sudo apt-get install gnome-session-fallback

```************

**Step #2**: You'd quickly find that 'indicator-applet', 'indicator-applet-complete', and 'indicator-applet-session' are lacking in "Add to panel". You'll really need either 'indicator-applet' or 'indicator-applet-complete' to display some of the notifications such as mail, the hardware sensors and/or system monitor indicators, and the update-notifier. (I personally only use 'indicator-applet' but we all have individual preferences). So we need to install [Jason Conti's PPA]("https://launchpad.net/%7Ejconti/+archive/gnome3") and our first additional packages:

```
sudo add-apt-repository ppa:jconti/gnome3
``````
sudo apt-get update
``````
sudo apt-get install indicator-applet indicator-applet-complete indicator-applet-session

```When that is complete it's time to take your first look at the new "classic" DE by simply logging out, then clicking on the "gear" to the right of your user name on the login screen, selecting Classic (No effects), entering your password, and logging back in. You'll hopefully see this:

[ATTACH]207950[/ATTACH]

************

Now, before continuing, please understand that **all of these additional steps are optional**. No two people want the exact same look, feel, or function out of a DE! This is just what I wanted. Pick and choose to suit your own desires.

************

**Step #3**: I quickly realized that the purple background of the terminal was killing my eyes so in terminal I clicked Edit > Profile Preferences > Colors and unticked the "Use colors from system theme" box. Then, in the same window, I clicked on the color block next to "Background color" and used the eyedropper to set the background to white. Ahhhh, much easier on the eyes.

************

**Step #4**: I found the screen lock thing very annoying, I live alone and don't like having to enter my password everytime the screen-"blanker" acivates. So you can just go to System Tools > System Settings > Screen and select Lock = Off. (I call it a screen-"blanker" mostly as a joke because it hardly resembles a screensaver anymore).

************

**Step #5**: Even after setting Lock to Off I found it annoying to have the screen-"blanker" activate while trying to watch videos or such. In Gnome 2 I used to be able to use 'gnome-inhibit-applet' but it's not available in Gnome 3. No worries, I found a very good replacement, Caffeine:

[https://launchpad.net/~caffeine-developers/+archive/ppa]("https://launchpad.net/%7Ecaffeine-developers/+archive/ppa")

In my original screenshot the caffeine applet shows up next to the indicator-applet. I find it to be a sweet replacement for the old 'gnome-inhibit-applet'. Once installed and set up it allows you to "inhibit" the screen-"blanking", I think a picture is worth a thousand words so here:

[ATTACH]207951[/ATTACH]

Should you choose to install it you can setup Caffeine by going to Other > Caffeine preferences. Installation is easy:

```
sudo add-apt-repository ppa:caffeine-developers/ppa

``````
sudo apt-get update
``````
sudo apt-get install caffeine
```Note: This works equally well in Unity.

************

**Step #6**: In Unity the update-notifications now show up in the Launcher but without the Launcher we now get no persistent update notifications. Still no worries, I got it to show up in either 'indicator-applet' or 'indicator-applet-complete' in gnome-panel by running the command:

```
gsettings set com.ubuntu.update-notifier auto-launch false
```You can revert that by running:

```
gsettings set com.ubuntu.update-notifier auto-launch true
```************

**Step #7**: I really liked using either 'gnome-sensors-applet' or 'computertemp' to display system temps in the panel but again they're not available with Gnome 3. Again no worries, Hardware Sensors Indicator comes to the rescue:

[https://launchpad.net/~alexmurray/+archive/indicator-sensors]("https://launchpad.net/%7Ealexmurray/+archive/indicator-sensors")

More about that here:

[http://ubuntuforums.org/showpost.php?p=11492701&postcount=4](http://ubuntuforums.org/showpost.php?p=11492701&postcount=4)

To install just run these three commands:

```
sudo add-apt-repository ppa:alexmurray/indicator-sensors
``````
sudo apt-get update
``````
sudo apt-get install indicator-sensors
```It then shows up in System Tools > Hardware Sensors Indicator. After launching it the first time you must click on the new "applet" which just says "No active sensors" and click on Preferences. From there you can select which sensors to display and other options.

************

**Step #8**: It's also sometimes nice to display CPU and memory usage in the panel, so here's System Monitor Indicator:

[https://launchpad.net/indicator-sysmonitor](https://launchpad.net/indicator-sysmonitor)

More about it here:

[http://ubuntuforums.org/showpost.php?p=11473552&postcount=208](http://ubuntuforums.org/showpost.php?p=11473552&postcount=208)

To install just run these three commands:

```
sudo add-apt-repository ppa:alexeftimie/ppa
``````
sudo apt-get update
``````
sudo apt-get install indicator-sysmonitor
```It then shows up in Accessories > System monitor indicator. Do not confuse it with System Monitor in System Tools. I think setting it up is almost self explanatory.

************

**Step #9**: I found the overlay-scrollbars to be inconsistent and annoying in the classic DE so I removed them, but that was totally a matter of preference, and this is one of those steps that really seems to somewhat break Unity! Should you want to remove them run:

```
sudo apt-get purge liboverlay-scrollbar-0.2-0 liboverlay-scrollbar3-0.2-0 overlay-scrollbar
```Note: You'll likely have to reboot for that change to fully take effect.

************

**Step #10**: At this point I decided the window-management buttons really needed to be back on the right so I ran:

```
gconftool-2 --set "/apps/metacity/general/button_layout" --type string ":minimize,maximize,close"
```Note: to restore the defaults run:

```
gconftool-2 --set "/apps/metacity/general/button_layout" --type string "close,minimize,maximize:"
```Note: This step (#10) can also be performed using Ubuntu Tweak.

************

**Step #11**: At this point I'm fairly happy but the scrollbar color is hard on my eyes. It's like trying to differentiate between two shades of white. I'd really prefer having the scrollbars match the dark gray panel or window title-bar with a white background but I haven't been able to figure that out yet. The best alternative I've found so far is changing the metacity and gtk themes this way:

```
sudo add-apt-repository ppa:webupd8team/themes
``````
sudo apt-get update
``````
sudo apt-get install shiki-colors-metacity-theme zukitwo-dark-gtk-theme
``````
gconftool-2 -s --type string /apps/metacity/general/theme Shiki-Colors-Metacity
``````
gsettings set org.gnome.desktop.interface gtk-theme Zukitwo-Dark
```I found that fairly pleasing to my eyes (it also replaced the drastic orange with a nice grayish-blue and I like the "retro" look of the window management buttons) but if you should decide to revert to the default Ambiance themes just run:

```
gconftool-2 -s --type string /apps/metacity/general/theme Ambiance
``````
gsettings set org.gnome.desktop.interface gtk-theme Ambiance
```Note: Both Ubuntu Tweak and 'gnome-tweak-tool' can be used for applying themes, but NOT installing themes.

I'm very open to suggestions about theming, this is simply the best combo I've come up with so far.

************

**Step #12**: I also dislike the missing menu and button icons so I run:

```
gsettings set org.gnome.desktop.interface menus-have-icons true
``````
gsettings set org.gnome.desktop.interface buttons-have-icons true
```Note: This step (#12) can also be performed using Ubuntu Tweak.

************

**Step #13**: This one is the hardest for me to explain. By default the Oneiric desktop is set to NOT display any icons, but it's possible for the desktop to display any combination of these icons/"actors":

```
Computer...........(computer-icon-visible)
Home...............(home-icon-visible)
Network............(network-icon-visible)
Trash..............(trash-icon-visible)
Mounted volumes....(volumes-visible)
```But to do so you must first set the "stage" by running:

```
gsettings set org.gnome.desktop.background show-desktop-icons true
```But that only sets the stage for the actors, now you must decide which actors you want on the stage. You're now the director.

After running that command either reboot or log out and log back in. When you get back to a blank DE background decide what you want displayed. (Hint, the "true" or "false" at the end of these commands is the key):

To show the Computer icon run:

```
gsettings set org.gnome.nautilus.desktop computer-icon-visible true
```To hide the Computer icon run:

```
gsettings set org.gnome.nautilus.desktop computer-icon-visible false
```To show the Home icon run:

```
gsettings set org.gnome.nautilus.desktop home-icon-visible true
```To hide the Home icon run:

```
gsettings set org.gnome.nautilus.desktop home-icon-visible false
```To show the Network icon run:

```
gsettings set org.gnome.nautilus.desktop network-icon-visible true
```To hide the Network icon run:

```
gsettings set org.gnome.nautilus.desktop network-icon-visible false
```To show the Trash icon run:

```
gsettings set org.gnome.nautilus.desktop trash-icon-visible true
```To hide the Trash icon run:

```
gsettings set org.gnome.nautilus.desktop trash-icon-visible false
```To show Mounted Volumes run:

```
gsettings set org.gnome.nautilus.desktop volumes-visible true
```To hide Mounted Volumes run:

```
gsettings set org.gnome.nautilus.desktop volumes-visible false
```Note: This step can also be performed using either Ubuntu Tweak or 'gnome-tweak-tool'.

************

**Step #14**: You may or may not find that you need to disable the Firefox and/or Thunderbird global menu add-ons. It seems to depend on the panel configuration, but I'm not quite sure. To do so in Firefox just go to Tools > Add-ons > Global Menu Bar integration and select Disable. You'll then be prompted to restart Firefox. I don't use Thunderbird so I can't be sure of the specific procedure with it, but I'd think it's similar.

**Update**: If you use only a bottom panel as I do you may notice after updates on Feb. 17, 2012 that the Unity top panel (aka: menu bar) is back on the desktop. This was also a problem immediately after the release of Oneiric but it was fixed shortly thereafter. This time I decided to actually kill it for good :)

I did so with one command:

```
sudo apt-get purge appmenu-gtk appmenu-qt indicator-appmenu appmenu-gtk3
```Then just log out and log back in.

************

**Step #15**: Thanks to [Flynsarmy]("http://www.flynsarmy.com/2011/11/how-to-make-ubuntu-11-10-more-usable/") I've discovered another useful tweak. In Gnome 3 the "prescribed" method of launching the terminal is 'Ctrl+Alt+T' but I've found it to be fiddly and somewhat unreliable, like sometimes it either doesn't work or it launches multiple terminals. That post showed me how to get the "Run Command Prompt" back by pressing Alt+F2 just as it was in Gnome 2, and I love it.

It really couldn't be much simpler, just go to Applications > System Tools > System Settings > Keyboards > Shortcuts > System and highlight the line that says "Show the run command prompt". Then position the mouse pointer over where it says "Disabled" and left-click the mouse. Then you'll see "Disabled" change to "New shortcut". Then just press Alt+F2 and you'll see that change as you do so, while actually launching the classic run command prompt for the first time.

************

That's it for now. I hope others will share their favorite Oneiric classic tips and tricks. I'll be glad to edit this and add links to other threads or posts related to Oneiric classic. Maybe someone can even share how they got classic to run with Compiz since that's not my thing.

I recently realized that I left out **credit where credit is due**. I certainly owe a large number of other Ubuntu end users and early testers a debt of gratitude, along with the developers of the "add-on" apps/applets discussed here, but [the webupd8 team]("http://www.webupd8.org/") has been invaluable at providing not only great information but also providing the theme PPA needed to perform step #11.

I hope NOT to blow up too many computers.

Many thanks, Keep it ..(Your Help) On

---

