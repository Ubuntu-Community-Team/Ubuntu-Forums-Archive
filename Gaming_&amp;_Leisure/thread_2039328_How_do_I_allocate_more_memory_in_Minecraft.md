---
title: "How do I allocate more memory in Minecraft?"
date: 2012-08-08
forum: Gaming &amp; Leisure
---

### Post by Chemoflys on 2012-08-08
I've been searching YouTube and the internet for days trying to figure out how I can allocate 2GB of RAM to Minecraft, as I want to install Pure DB Craft's texture pack, it's HD and it says I don't have enough memory.

Can someone link me to a tutorial or something please?

---

### Post by papibe on 2012-08-08
Hi Chemoflys.

AFAIK, you can reserve memory for minecraft in the java paramenters. Take a look at this: [Start the Minecraft server]("http://www.minecraftwiki.net/wiki/Setting_up_a_server#Start_the_Minecraft_server").

Regards.

---

### Post by drmrgd on 2012-08-08
All you need to do is specify the amount that you want to allot when running the minecraft.jar file.  So, if you only wanted 256 MB for example:

```
 java -Xmx256M -Xms256M -cp minecraft.jar net.minecraft.LauncherFrame
```

The Xmx is the max heap size of memory alloted and Xms is the minimum heap size.  Just increase the values to your liking from there.

Hope that helps.

---

### Post by Chemoflys on 2012-08-08
> **drmrgd said:**
> All you need to do is specify the amount that you want to allot when running the minecraft.jar file.  So, if you only wanted 256 MB for example:

```
 java -Xmx256M -Xms256M -cp minecraft.jar net.minecraft.LauncherFrame
```

The Xmx is the max heap size of memory alloted and Xms is the minimum heap size.  Just increase the values to your liking from there.

Hope that helps.

Thanks for your help. So would I copy that code into a empty document I've made in my .minecraft folder, then call the document '2gb.bat' or something?

:popcorn:

---

### Post by drmrgd on 2012-08-08
What I did was to create a bash alias to run it.  To do that, you'd just have to edit the .bashrc file located in your /home directory with your favorite editor (gedit for example).  It's also a good idea to have a backup copy of .bashrc just in case something goes wrong.

Once you've got .bashrc open, scroll down to the section where you'll see a few entries like:

```
alias ll='ls -al'
```

Then enter in the command above, making sure to put in the full path of the minecraft.jar file.  So, let's say the minecraft.jar file is located in /home/chemoflys/Games/minecraft/, you'd make the alias look like this:

```
alias minecraft='java -Xmx256M -Xms256M -cp /home/chemoflys/Games/minecraft/minecraft.jar net.minecraft.LauncherFrame
```

Then save the file, close it, and re-source the file (you can also just launch another terminal instance if you want instead) by running:

```
source /home/chemoflys/.bashrc
```

That should reload your .bashrc file, which will then allow you run run minecraft by opening a terminal and simply typing 'minecraft'.  

Of course, there are also ways to make desktop launchers so you can just double-click an icon and launch it that way.  A quick Google search will give you a bunch of options in that regard.  I'm alway in the terminal, so I prefer to just use that to launch.

Hope that helps!

---

### Post by Chemoflys on 2012-08-08
> **drmrgd said:**
> What I did was to create a bash alias to run it.  To do that, you'd just have to edit the .bashrc file located in your /home directory with your favorite editor (gedit for example).  It's also a good idea to have a backup copy of .bashrc just in case something goes wrong.

Once you've got .bashrc open, scroll down to the section where you'll see a few entries like:

```
alias ll='ls -al'
```

Then enter in the command above, making sure to put in the full path of the minecraft.jar file.  So, let's say the minecraft.jar file is located in /home/chemoflys/Games/minecraft/, you'd make the alias look like this:

```
alias minecraft='java -Xmx256M -Xms256M -cp /home/chemoflys/Games/minecraft/minecraft.jar net.minecraft.LauncherFrame
```

Then save the file, close it, and re-source the file (you can also just launch another terminal instance if you want instead) by running:

```
source /home/chemoflys/.bashrc
```

That should reload your .bashrc file, which will then allow you run run minecraft by opening a terminal and simply typing 'minecraft'.  

Of course, there are also ways to make desktop launchers so you can just double-click an icon and launch it that way.  A quick Google search will give you a bunch of options in that regard.  I'm alway in the terminal, so I prefer to just use that to launch.

Hope that helps!

Thank you for your help, when I typed in Minecraft after it came up with a few errors in terminal but then it opened. It's just a shame I have to keep terminal open whilst using Minecraft. But no worries :P.

---

### Post by drmrgd on 2012-08-08
> **Chemoflys said:**
> Thank you for your help, when I typed in Minecraft after it came up with a few errors in terminal but then it opened. It's just a shame I have to keep terminal open whilst using Minecraft. But no worries :P.

Well, like I said, have a quick Google search for Linux Minecraft Launchers, and you'll find a ton of hits on how to make a nice little desktop icon to double click and launch minecraft.  I can't search for that from where I am due to firewalls.  However I know I've seen a bunch of stuff.  

I prefer not to have stuff on my desktop and I use Yakuake (Guake in Ubuntu) to make drop down terminals that I can put away quickly.  I also like to keep track of errors and stuff in the terminal as I run.  So for me a bash alias is the way to go.

Glad you got it working!

---

### Post by Chemoflys on 2012-08-08
> **drmrgd said:**
> Well, like I said, have a quick Google search for Linux Minecraft Launchers, and you'll find a ton of hits on how to make a nice little desktop icon to double click and launch minecraft.  I can't search for that from where I am due to firewalls.  However I know I've seen a bunch of stuff.  

I prefer not to have stuff on my desktop and I use Yakuake (Guake in Ubuntu) to make drop down terminals that I can put away quickly.  I also like to keep track of errors and stuff in the terminal as I run.  So for me a bash alias is the way to go.

Glad you got it working!

I bumped it up to 2GB in the file but when I true Aspax Pure DB Texture pack it gets stuck on the title, I know it's HD and all. Does it perhaps need to be patched in MC Patcher before I can use it? It's quite fustraiting, damn I miss my Windows Pc lol.

---

### Post by drmrgd on 2012-08-08
I'm not all that familiar with the HD texture packs (or many texture packs in general to be honest!).  I'm home now and did a quick Google search of that pack.  I couldn't find the specific one that you listed, but did find this, which is close:

[http://www.minecraftforum.net/topic/376784-16x-32x-64x-128x-256x-512x10-to-131-sphax-purebdcraft-080812/](http://www.minecraftforum.net/topic/376784-16x-32x-64x-128x-256x-512x10-to-131-sphax-purebdcraft-080812/)

If you go to the FAQ, there is a suggestion that you need to be running a 64-bit OS and have a 64-bit version of java installed to make this work:

[http://bdcraft.net/faq-frequently-asked-questions](http://bdcraft.net/faq-frequently-asked-questions)

Maybe that's relevant to your problem?

---

### Post by Chemoflys on 2012-08-08
> **drmrgd said:**
> I'm not all that familiar with the HD texture packs (or many texture packs in general to be honest!).  I'm home now and did a quick Google search of that pack.  I couldn't find the specific one that you listed, but did find this, which is close:

[http://www.minecraftforum.net/topic/376784-16x-32x-64x-128x-256x-512x10-to-131-sphax-purebdcraft-080812/](http://www.minecraftforum.net/topic/376784-16x-32x-64x-128x-256x-512x10-to-131-sphax-purebdcraft-080812/)

If you go to the FAQ, there is a suggestion that you need to be running a 64-bit OS and have a 64-bit version of java installed to make this work:

[http://bdcraft.net/faq-frequently-asked-questions](http://bdcraft.net/faq-frequently-asked-questions)

Maybe that's relevant to your problem?

Oh, that'll be why then. Thanks very much for your help :guitar:

---

