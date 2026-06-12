---
title: "How to change to Cinnamon?"
date: 2013-08-14
forum: Desktop Environments
---

### Post by eAMxfTT on 2013-08-14
I have installed cinnamon as it said I should the website, and the install seems to have gone without a hitch. But when I restart and want to change my desktop environment in the logon screen, the only two options I have are Ubuntu and Ubuntu 2D which pretty much seems identical. So how do I change to Cinnamon? I don't mind having to do it in the terminal, as long as I can just do it once and then it's permanent. I'm running 12.04 by the way.

---

### Post by SweetAurora on 2013-08-14
Did you try restarting the PC? A new desktop enviroment dosen't always show up immediately after install, a reboot will update LightDM's list and should show it.

---

### Post by eAMxfTT on 2013-08-14
Yes... as I stated, I restarted the computer after installing. But LightDM's list? Is that the list of environments that appears when I click on the icon beside my username on the logon screen?

---

### Post by SweetAurora on 2013-08-14
LightDM is Ubuntu's Login Manager. That's what displays on the screen after boot up and what you give your Username and Password to so it can log you into your desktop. Strange that it didn't show up. How exactly did you install it?

Edit: I guess I need glasses... Didin't see the restart part in your question, sorry.

---

### Post by eAMxfTT on 2013-08-14
I used the terminal and wrote the commands:
sudo add-apt-repository ppa:gwendal-lebihan-dev/cinnamon-stable
sudo apt-get update
sudo apt-get install cinnamon

It should be that simple... it just isn'&#7831; in my case for some reason.

---

### Post by RadicaX on 2013-08-14
hmm, sounds like the login manager did not update to add it. Do you know of a command that allows you to update LightDM? Should work out then I would imagine, especially if the commands went through perfect and you got all the packages with no failure.

---

### Post by crazymonkey05 on 2013-08-14
try a different DM i use lightdm but gnomedm might work for you

```
[COLOR=#000000][FONT=UbuntuBeta Mono]sudo dpkg-reconfigure gdm[/FONT][/COLOR]
```

and just google diffrent dm's if you dont already have any

---

### Post by eAMxfTT on 2013-08-14
No I don't know a command to update LightDM. If I did, I would have tried it though, but thanks. 

I tried installing GDM... your command didn't work, and so it took me a while to guess at the solution, because it's not called GnomeDM but GDM, so I couldn't find any help on the web. The right command was just: 
Sudo get-apt install gdm
However it did not work. I can still only access the other installed GUIslike GNOME, Gnome Classic, Ubuntu 2D etc. But Cinnamon is still a no show. I should mention as well, that no file has occured in the /usr/share/xsession folder for Cinnamon. There are files for all the other ones.

---

### Post by RadicaX on 2013-08-15
Try installing the packages again, it sounds like some of them did not get through then. If you are not finding it where it should be that is.

---

### Post by eAMxfTT on 2013-08-15
I have already tried reinstalling it three times.

---

### Post by RadicaX on 2013-08-15
Hmm... That is odd. It should make a desktop file, if it is not, something has messed up with your distro it sounds like. You use Ubuntu 12.04? I have looked at my desktop files, and they are all there. Did you do it from the command line to check? my bet is that it moved it to some other directory. Let's look through it with a GUI shall we? Go into your file system, go to etc, go to xdg, and try posting a picture of it here. My bet is the file is stuck in some other directory though. So we can look for it through other ones and such till we find it. Then just move the desktop file to the proper directory. I found several downloads by mistake in my tmp directory due to my sister. So it can be in a lot of places.

---

### Post by eAMxfTT on 2013-08-16
Alright... this is what it looks like. So where should I look? And I'm not sure why there should be a file on the desktop? It's a desktop manager so shouldn't there just be files in the system and then an option in the logon manager?

---

### Post by RadicaX on 2013-08-16
[ATTACH=CONFIG]245406[/ATTACH]  Look at how different your setup is than mine? Now the .desktop file is basically what makes it work, you should have those for each one like you said. but for some reason they are all going to some weird place. Do you have other accounts on your computer perhaps? Otherwise, if it is on your computer, we are going to need to look for them. (I found downloads in tmp once.)

---

### Post by eAMxfTT on 2013-08-16
Well there are a lot of differences? I'm not sure exactly what you want me to notice and what to do about the differences... 

No I am the only user.

---

### Post by RadicaX on 2013-08-16
Right now I just wanted to check what the differences. Because if we know the differences, we can see what is wrong.[ATTACH=CONFIG]245419[/ATTACH]   Okay try going to usr/share/xsessions. You should have your .desktop files there. I looked around on the web some too, one guy to fix it made a .desktop file. To which I have no clue. You might after taking a look at a screenshot open another thread asking why you are missing .desktop files? And explain a bit of what is going on. A title like that will get more people to come, and most likely more skilled people. And you do not have UFW blocking your downloads, and you can install, it just is doing some kind of weird install or something. Keep at it, we will get it down sooner or later. And remember, a good title can bring in different kinds of people for it. (Because they see how drastic the problem is then.) How to change to cinnamon just sounds like a normal DE download question, not this whole can of worms we have opened.

---

