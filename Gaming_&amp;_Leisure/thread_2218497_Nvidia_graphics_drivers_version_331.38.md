---
title: "Nvidia graphics drivers version 331.38"
date: 2014-04-20
forum: Gaming &amp; Leisure
---

### Post by ken30 on 2014-04-20
I'm running Lubuntu 14.04. I've tried installing Nvidia binary drivers for version 331.38(Proprietary, tested) and when I reboot my PC all text its super tiny like scribble and cannot be read. I don't understand what the problem is its like its zoomed out. Also I'm sorta new to Linux. Please help!:(

---

### Post by oldrocker99 on 2014-04-21
Did you install the 331.38 drivers from the "Additional Drivers" app, or from a nVidia download?

---

### Post by ken30 on 2014-04-21
Additional drivers

---

### Post by vanquishedangel on 2014-04-21
I am replacing my post because as I was testing it out I discovered that there was some funny issues, with both computers I have. I don't want people to try that recommendation that I posted so I deleted it.

For my computers I discovered that fglrx-updates was installed on both despite the fact that I never installed that package.  I had to open synaptic and look specifically for fglrx because "additional drivers" did not show that fglrx-updates was installed

On my mothers computer I never installed proprietary drivers ever.

On my computer I never installed fglrx-updates

both computers had fglrx-updates installed, both are fairly new installations of 13.10 that were installed fresh shortly before 14.04 came out. Both were updated to 14.04. It is not possible that I made a mistake on this.

**So use a package manager like synaptic to check what versions of your graphics drivers are installed and make sure that only one version is installed.** My first post here was misinformed, "additional drivers" showed open sourced drivers installed but actually fglrx-updates was.

---

### Post by MikeCyber on 2014-04-21
Works fine here with nvidia331 but don't select nvidia-updates. I think that's broken and why for heaven's saken do we need two nvidia packages? About as silly as the Grub error in 14.04. Only select nvidia 331 and nvidia-settings nothing else, works for me.

---

### Post by vanquishedangel on 2014-04-21
> **MikeCyber said:**
> Works fine here with nvidia331 but don't select nvidia-updates. I think that's broken and why for heaven's saken do we need two nvidia packages? About as silly as the Grub error in 14.04. Only select nvidia 331 and nvidia-settings nothing else, works for me.

I am sure one is more stable and nvidia-updates is a more updated but less stable nvidia driver, it is like that with ati. The more updated ones were added because of pressure from the community I am sure, people back in the day hated having outdated drivers, not that they were that outdated mind you, and people criticized the drivers for not being newer.

---

### Post by ken30 on 2014-04-21
> **vanquishedangel said:**
> I am replacing my post because as I was testing it out I discovered that there was some funny issues, with both computers I have. I don't want people to try that recommendation that I posted so I deleted it.

For my computers I discovered that fglrx-updates was installed on both despite the fact that I never installed that package.  I had to open synaptic and look specifically for fglrx because "additional drivers" did not show that fglrx-updates was installed

On my mothers computer I never installed proprietary drivers ever.

On my computer I never installed fglrx-updates

both computers had fglrx-updates installed, both are fairly new installations of 13.10 that were installed fresh shortly before 14.04 came out. Both were updated to 14.04. It is not possible that I made a mistake on this.

**So use a package manager like synaptic to check what versions of your graphics drivers are installed and make sure that only one version is installed.** My first post here was misinformed, "additional drivers" showed open sourced drivers installed but actually fglrx-updates was.


OMG, thank you so much! I've checked my version it says im running 331.38(proprietary, tested) under software and updates with no small text! Thank you so much!! Oh and one more thing I was looking at other desktop environments for Linux are they easy to change without installing a different version of Linux? Like from going to LXDE to Unity or Gnome or even Cinnamon?

---

### Post by adec2 on 2014-04-21
Alternative desktop environments

[http://askubuntu.com/questions/65083/what-different-desktop-environments-and-shells-are-available](http://askubuntu.com/questions/65083/what-different-desktop-environments-and-shells-are-available)

After installing it will appear on the login screen dropdown box

---

### Post by vanquishedangel on 2014-04-21
> **ken30 said:**
> OMG, thank you so much! I've checked my version it says im running 331.38(proprietary, tested) under software and updates with no small text! Thank you so much!! Oh and one more thing I was looking at other desktop environments for Linux are they easy to change without installing a different version of Linux? Like from going to LXDE to Unity or Gnome or even Cinnamon?

I prefer LXDE, but yes you can install a ton of others on just about any linux, you will not need a different linux but they will install their own programs, if you are running Lubuntu and want LXDE, type it in synaptic. Lubuntu and LXDE are different. All the desktops in the *buntu series come with their own set of applications, so since you started with lubuntu and if you decide to install gnome, you will have two media players. You will have mplayer (part of the Lubuntu desktop) and totem (part of the gnome desktop). If you install similar desktops environments then you will have less of this, xubuntu, Lubuntu, LXDE share many of the same default applications (ie xfburn).

---

### Post by ken30 on 2014-04-21
Thanks guys :D. So I did some testing with that graphics driver. And I have horrible framerate on 2 games i played Minecraft and Left 4 dead 2 from steam, compared to just using the open source stock graphics driver. Am I missing something here? Isn't the Nvidia driver supposed to boost my performance?

---

### Post by vanquishedangel on 2014-04-22
> **ken30 said:**
> Thanks guys :D. So I did some testing with that graphics driver. And I have horrible framerate on 2 games i played Minecraft and Left 4 dead 2 from steam, compared to just using the open source stock graphics driver. Am I missing something here? Isn't the Nvidia driver supposed to boost my performance?

Yes it is supposed to be better and almost always is, Did you use "synaptic"  and search "nvidia" , when I did it I found about a ton of different drivers . There was, nvidia-173, nvidia-304, nvidia-304-updates, nvidia-310, nvidia-310-updates, nvidia-313-updates, nvidia-319, nvidia-319-updates, nvidia-331, nvidia-331-updates.

If you are using* nvidia-331*, you** cannot **have *nvidia-331-updates* installed. They will conflict and cause problems usually. You will have to choose one or the other. Also any previous versions should be removed, make sure only nvidia-331 is installed and not nvidia-173 or any others.

Since you are on Lubuntu you should have synaptic package manager installed by default, usually under the preferences menu. The GUI method is harder to explain, try below first to see if it works.



You may also be able to check this running the below command and then rebooting:

sudo apt-get install --reinstall nvidia-331

---

### Post by ken30 on 2014-04-22
I've done exactly that and was still getting horrible framerate :( I don't know if there is anything else that I need to install from synaptic package manager for the graphics driver 331 with updates. That will improve my framerate.

---

### Post by vanquishedangel on 2014-04-22
> **ken30 said:**
> I've done exactly that and was still getting horrible framerate :( I don't know if there is anything else that I need to install from synaptic package manager for the graphics driver 331 with updates. That will improve my framerate.

Use the other driver, not nvidia-331-updates, just use nvidia-331. If that does not work I am not sure I can help you any further. As another poster stated the nvidia-331-updates package may not be working right. Whatever you choose I hope it gets worked out, I primarily use ATI/AMD graphics.

steam works at a playable frame rate for me for dota2 but my computer is also old (almost 10 years old). It plays with decent graphics as well (they are set fairly high). I read somewhere that steam is using a custom version of wine for games, this means that steam games would still actually be windows games and not actually native linux games and therefore you may not get the same frame rates you did in windows.

Minecraft is not on steam and I have never played it. With a quick look I see that it is a game written in java, and the author does have a linux version and I will post the link below that I found on my quick search and you can see if that is how you installed it.

[http://www.everydaylinuxuser.com/2013/12/how-to-install-minecraft-for-ubuntu.html](http://www.everydaylinuxuser.com/2013/12/how-to-install-minecraft-for-ubuntu.html)

it would be helpful if you told us how you installed it.

---

### Post by shahnawaz2 on 2014-04-22
Definitly Nvidia will boost your performance and for future installation I would like to give a suggestion ..Kindly avoid update driver online it is always better to update this kind of driver  from a proper downloaded setup ,You can use CD or pendrive for portability .

---

### Post by ken30 on 2014-04-22
Thanks for the help everyone. Alas, I still have no luck with the Nvidia drivers I've installed older versions from the synaptic manager and I still have horrible frame rate compared to the open source driver from Linux. I've uninstalled the open source one to I guess ill just stick to keeping my windows hard drive specifically for gaming and use my Linux hard drive for general everyday stuff and Minecraft. :)

---

### Post by oldrocker99 on 2014-04-22
You should type this:
```
sudo apt-get remove nvidia*
```
**before** installing a different version of a driver.

I installed 14.04 beta 2, and the nvidia-331-updates driver did not work at installation, but nvidia-331 works fine with my GeFoce 650ti.

---

### Post by ken30 on 2014-04-23
I did and it says "nothing was installed, so not removed". It seems I will never have luck with Linux lol. I've tried the nvidia-331 before with everything uninstalled and I still have horrible framerate with my 550ti.

---

### Post by ken30 on 2014-04-23
So I reinstalled the nvidia-331 driver and my framerate is better than normal again but this is were my glitch comes in my earlier comments everything is so microscopic all the text I acutally have to make all the text bigger by hand from 12pt to 32pt to be able to read all the text on my desktop, task bar, and when I open folders and such. I did uninstall the open source driver to. :(

---

### Post by vanquishedangel on 2014-04-23
Did you try adjusting your resolution or font size? Here is a post I found about it that has some useful adjustments:

System Font - Font used in the file manager, main menu and window menus: Set in Preferences > Customized Look and Feel > Widget Tab. Look on the lower right - called default font. 

Desktop Icon Font - Can be set by right-clicking on the desktop and choosing Desktop Preferences.

Window Title Font - Set in Preferences > Customized Look and Feel > Window Border Tab. Below that are tabs for Theme, Title Bar, Misc. Title Bar tab has settings for the Window Title.

Task Bar Buttons - The font used is the same as the System Font, but the font's size is fixed in any given panel size and icon size chosen.

---

### Post by ken30 on 2014-04-23
I've done all of that I manually made font bigger from 12pt to  32pt. I dont understand this glitch at all :o Even my login screen is microscopic.

---

### Post by ken30 on 2014-04-23
So I've done some research and came across modifying my xorg.conf file and my DPI is set at 24. From what I was reading upping the DPI could fix this glitch I'm having. Except everytime I try to modify the file and save it. It will not allow me because I don't have permission.

---

### Post by oldrocker99 on 2014-04-23
```
gksudo gedit /etc/Xorg/xorg.conf
```

That's how you edit despite permissions. You can also (from a terminal)
```
sudo nano /etc/Xorg/xorg.conf
```

---

### Post by ken30 on 2014-04-23
Well, so I was able to fix it it turns out I didn't even have a xorg.conf file..lol. So I created one with instructions I found online and just restarted my computer and Voila! My text size was all fixed and was enormous from my recent upscale and now its all fixed! :D Thank you guys for all the help! It's weird that the xorg.conf file was not created on its own when I installed the binary driver.

---

### Post by oldrocker99 on 2014-04-23
Glad to have been of some help.

---

### Post by MikeCyber on 2014-04-24
Without reading all, you can simply change resolution in nvidia-settings.-

---

### Post by ken30 on 2014-04-24
Yea that doesn't work for me. It's my DPI setting.

---

### Post by ken30 on 2014-04-24
> **oldrocker99 said:**
> ```
gksudo gedit /etc/Xorg/xorg.conf
```

That's how you edit despite permissions. You can also (from a terminal)
```
sudo nano /etc/Xorg/xorg.conf
```

Hey is there a command that I can use after modifying it to lock the file back up so no further modifications can be made.

---

### Post by verymadpip on 2014-04-25
Hi there.
What was the command you used to generate the xorg.conf.  I've found a couple of methods online, but so far I've just made things worse.
I'm having a horrible time between mouse & graphics problems at the moment.

---

### Post by ken30 on 2014-04-25
> **verymadpip said:**
> Hi there.
What was the command you used to generate the xorg.conf.  I've found a couple of methods online, but so far I've just made things worse.
I'm having a horrible time between mouse & graphics problems at the moment.

I believe I used this command.
[COLOR=#C20CB9]**sudo**[/COLOR] nvidia-xconfig [COLOR=#660033]--no-use-edid-dpi

Heres the website I got it from.

[http://www.techytalk.info/lubuntu-change-fonts-dpi-when-using-proprietary-nvidia-driver/](http://www.techytalk.info/lubuntu-change-fonts-dpi-when-using-proprietary-nvidia-driver/)[/COLOR]

---

### Post by verymadpip on 2014-04-26
Hi ken30.
Thanks for the link.  I tried the nvidia-xconfig (without your mod) with awful results before asking my question in this thread.
I worked round by just creating the xorg.conf with the section I needed for my mose as the only entry in it.

I appreciate the reply though :)

---

### Post by dannyboy79 on 2014-04-26
i have read many people having issues with the nvidia driver provided thru the additional drivers and or ubuntu repo's. I have never had an issue running the nvidia binary driver from the nvidia website. I'm currently running 334.21 with my GTX 760 with no issues

---

### Post by verymadpip on 2014-04-26
I'm pretty sure my problem was with alterations to xorg.conf for the mouse, as opposed to the nvidia driver itself.

---

### Post by ken30 on 2014-04-27
> **verymadpip said:**
> Hi ken30.
Thanks for the link.  I tried the nvidia-xconfig (without your mod) with awful results before asking my question in this thread.
I worked round by just creating the xorg.conf with the section I needed for my mose as the only entry in it.

I appreciate the reply though :)

No problem, glad to have tried to help!:o

---

### Post by ken30 on 2014-04-30
So I have a question that is not at all related to my problem. And need help making a decision. My other hard drive I have which has had windows 7 on it for about 8 years now and its developed bad sectors. Im debating about wiping it out and installing a fresh install of linux mint onto it and still see if the bad sectors are still there because they could just be corrupted data. I know some people said that 8 years for a hard drive and it has bad sectors means its toast. But it still runs just occasionally has a memory dump here and there when playing games with steam, barely has any problems with anything else. So should I wipe it? Or just let it slowly die away. It does still pass S.M.A.R.T test if anyone knows what im talking about.

---

### Post by oldrocker99 on 2014-05-01
A format should find bad sectors, map them and replace them with extra reserved sectors, especially if the drive passed a S.M.A.R.T. test. It's worth a try, but I would try a deep format, which writes 0000 to each sector, rather than a quick format. Your drive, if it has many bad sectors, would likely fail the deep format, and that's the best (if slowest) way to find out.

---

### Post by ken30 on 2014-05-01
> **oldrocker99 said:**
> A format should find bad sectors, map them and replace them with extra reserved sectors, especially if the drive passed a S.M.A.R.T. test. It's worth a try, but I would try a deep format, which writes 0000 to each sector, rather than a quick format. Your drive, if it has many bad sectors, would likely fail the deep format, and that's the best (if slowest) way to find out.

Thank you for the info. :) Also for anybody to answer does Linux Mint 16, update just like Ubuntu does? Like they have regular software updates and can even update to the next version of Linux Mint? I've read somewhere to update to newer versions you backup your files and such and wipe it and reinstall the newest version is this true?

---

### Post by oldrocker99 on 2014-05-01
> **ken30 said:**
> Thank you for the info. :) Also for anybody to answer does Linux Mint 16, update just like Ubuntu does? Like they have regular software updates and can even update to the next version of Linux Mint? I've read somewhere to update to newer versions you backup your files and such and wipe it and reinstall the newest version is this true?

Mint does NOT update quite the way Ubuntu does, and you cannot easily update to the latest version of Mint (something that is more common than you might expect among distros). I have used Mint several times, and have found it a bit annoying: you cannot use the ping test to find the best server, using the Software Center can be a real pain, as it does not recognize that you are running a Ubuntu system, etc. I do thank Mint for having gotten both MATE and Cinnamon off the ground. I guess I'm too much of a *buntu loyalist. I really, really like having access to the Ubuntu repos. I'm typing this on a 7 year old Toshiba A215-S4697 laptop using Razor-qt-desktop on top of Lubuntu. It runs, of course, just fine.

---

### Post by ken30 on 2014-05-02
> **oldrocker99 said:**
> Mint does NOT update quite the way Ubuntu does, and you cannot easily update to the latest version of Mint (something that is more common than you might expect among distros). I have used Mint several times, and have found it a bit annoying: you cannot use the ping test to find the best server, using the Software Center can be a real pain, as it does not recognize that you are running a Ubuntu system, etc. I do thank Mint for having gotten both MATE and Cinnamon off the ground. I guess I'm too much of a *buntu loyalist. I really, really like having access to the Ubuntu repos. I'm typing this on a 7 year old Toshiba A215-S4697 laptop using Razor-qt-desktop on top of Lubuntu. It runs, of course, just fine.

Well thanks for the heads up. I'm kinda disappointed now with what I'm hearing about Linux Mint lol. And now even debating of installing it on my bigger hard drive. :O I really don't like that they have not made it simple to upgrade to the next version of Linux Mint like Ubuntu does.. "sigh" :( Is it really that much of a pain?

---

### Post by oldrocker99 on 2014-05-02
Actually, the best thing to do is, when installing, to make a smallish system partition (my laptop's system partition is only 32GB, and it's less than 30% full, after installing quite a few programs) and make the rest of the disk a separate partition, mounted as /home. Then, when you do reinstall, your documents, settings, and all the other stuff in /home are mounted but unchanged.

Reinstallations aren't usually that big a deal; you'll have to re-enable some PPAs, and reinstall your favorite programs. Not a big deal at all.

---

### Post by ken30 on 2014-05-04
Just installed the KDE environment and I think im in love. I really enjoy the notifications it gives you for updating and such. And like the customization aspect of it.

---

### Post by oldrocker99 on 2014-05-05
KDE has come a long, long way; it predates GNOME as a desktop, and the current version has (in MHO) one heck of a lot more going for it than the current GNOME or Unity. Configurable as all get out, lots of apps, and very good fullscreen game performance, if you open Desktop Effects, click on the "Advanced" tab, and make sure that "Suspend desktop effects for fullscreen windows" is checked.

---

### Post by ken30 on 2014-05-05
> **oldrocker99 said:**
> KDE has come a long, long way; it predates GNOME as a desktop, and the current version has (in MHO) one heck of a lot more going for it than the current GNOME or Unity. Configurable as all get out, lots of apps, and very good fullscreen game performance, if you open Desktop Effects, click on the "Advanced" tab, and make sure that "Suspend desktop effects for fullscreen windows" is checked.

Thank you :). I'm guessing that saves me performance for when I'm ever gaming on Linux? I also just did a fresh install of Kubuntu because I love the KDE environment so much. Updated the graphics driver again and I still got extra tiny text again my original problem. But there is one thing that I like that Kubuntu or the KDE environment does, in system settings under application appearance and font I am able to manually set the DPI without making any modifications to my xorg.cong file like last time. I set it at 120 DPI and all my text and everything is perfectly fine now! :D This envoriment has really some really near effects. Any idea were I can get HD screen savers for Linux? I did install a bunch that I believe are from other Linux distros but are in my opinion not HD quality, I want something that's gonna pop!

---

### Post by ken30 on 2014-05-07
Alas, after using Kubuntu for some time I am having issues with it. Such as my headset and microphone do not work well just the microphone part. And I cannot run skype for some reason like I used to on Lubuntu it doesn't even start up on Kubuntu. I'm gonna try using Linux Mint 16 and give that try and see how it all works out. Also, gonna download and burn Xubuntu and Ubuntu all on discs to try them out if I do not like Linux Mint. :)

---

### Post by shahnawaz2 on 2014-05-07
definitely it is gonna boost your over all performance and one more things always download the addon driver it will work always..

---

### Post by ken30 on 2014-05-09
Installed Kubuntu 14.04 everything works from my original problem with mic and skype not working. Also, I didn't like that Linux Mint withheld latest kernal updates which is a huge security hole to me. So ill stick with the buntu ecosystem. :)

---

