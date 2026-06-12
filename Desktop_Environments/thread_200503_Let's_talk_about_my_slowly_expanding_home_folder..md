---
title: "Let's talk about my slowly expanding home folder."
date: 2006-06-20
forum: Desktop Environments
---

### Post by Joey French on 2006-06-20
Hi all, 
it seems lately that my home folder is being filled with files created by all manner of apps on my machine. When any application spits out a file (config, mostly) it ends up in my home folder. I have removed gnome completely from my system, but no matter what I do, I return to my home folder to a newly created "gnome-whatever" config file (usually more than one). I also have files spit out from dvd shrinking apps, web editing tools, you name it, it ends up in my home folder. On top of that, when I install tarballs, I use sudo, and I am under the impression that this will setup programs globally. However, this seems not to be the case, as I have to run programs from the path to the home folder (Google Earth, Firefox, etc). What is going on here? My home folder is now full of mostly useless files (that I do not want there to begin with) or from programs I didn't know I had installed. Can I make them go somewhere else? Am I just being an anal neatfreak? Does everyone's home folder grow huge over time?

Thanks,
Joey French

---

### Post by joske on 2006-06-20
I guess this is the way things are in the unix world. Most applications write a so-called dotfile in your homedir to store their config. I have hundreds of them. Nothing to do about it, I'm affraid (at least not for all files). But normally these files don't show up in the file manager or with ls on the command line, so this is not really a big problem. It would be a lot better if there was a generic way for storing config, used by all applications. Gnome has gconf for this, but not all (read: non-gnome) applications use this.

Regarding installations of tar-balls, you don't have to install them in your home dir. You can install them in /opt (which is the LSB standard place for them). Then you can symlink the executables to /usr/local/bin or something, so you don't have to type the complete path every time (/usr/local/bin is in the $PATH).

hth,
jos

---

### Post by stanz on 2006-06-20
Hi Joey...
If I've learnt this right, all the "." {dot} files, can be hidden.
On the toolbar, in naultius, tick "view", & look for "show hidden files".
If it has a checkmark next to it, "tick it".
EDIT:: So as NOT to show hidden files, thus- no check next to it. {sry}
Dot files should now be hidden...leaving you a neat looking window! 
I agree with using "/opt" folder also, it's another way to keep the home folder lite!
Let us know if this helps...!

---

### Post by Joey French on 2006-06-20
Yes, I have long since set my hidden files to be visible, so no hope for me there. However, the movement to the /opt folder may be a good idea. It is not really a big deal, but it seems that my home folder is now full of them, and I was wondering what others has to say about their homes collecting debris over time.

---

### Post by GoogleNinja on 2006-06-20
The first thing to keep in mind when using a new OS is that things are done differently. 

[QUOTE=Joey French]Hi all, 
it seems lately that my home folder is being filled with files created by all manner of apps on my machine. When any application spits out a file (config, mostly) it ends up in my home folder. I have removed gnome completely from my system, but no matter what I do, I return to my home folder to a newly created "gnome-whatever" config file (usually more than one). I also have files spit out from dvd shrinking apps, web editing tools, you name it, it ends up in my home folder. 
[/quote]
This is because linux is a multiuser system. Apps (for the most part), don't have "global" configurations for all users. This wouldnt work, as normal users don't have permission to write in the directories that apps are installed into. This is one of the fundamental differences with windows, which (for all intents and purposes) is a single-user os.

So instead of config files being stored in the app directory, or some global configuration registry, they are stored in the users home folder as invisible files. In windows, they hide things they don't want you messing with, so all non-newbie users tell it to show hidden files. in linux, files are hidden so they dont get in your way. currently, i have around 45 hidden files and directories in my home folder, but i didnt know that until i did a ls -a just now to illustrate this point.

The (massive) benefit of the Linux Way, is that you back up your home folder, and it gets your settings too, for every app you use.
[QUOTE=Joey French]
On top of that, when I install tarballs, I use sudo, and I am under the impression that this will setup programs globally. However, this seems not to be the case, as I have to run programs from the path to the home folder (Google Earth, Firefox, etc). What is going on here? My home folder is now full of mostly useless files (that I do not want there to begin with) or from programs I didn't know I had installed. Can I make them go somewhere else? Am I just being an anal neatfreak? Does everyone's home folder grow huge over time?

Thanks,
Joey French[/QUOTE]

as i said earlier, don't show hidden files, they are hidden for exactly that reason in linux. as for tarballs, the vast majority are compiled with "./configure; make; sudo make install", with make install being the command that stick stuff in more global folders. i don't use google earth or firefox specifically, so i can't really help too much on this one. one thing is that they were possibly installed somewhere (like /usr/local/googleearth) that isnt in your PATH variable. the common thing to do is to create a "symbolic link" (think commandline shortcut) from the executable to one of the directories that has links to all the apps installed. for example, if google earth is "/usr/local/googleearth/gearth", then you would want to do "ln -s /usr/local/googleearth/gearth /usr/local/bin". that creats a symbolic link in /usr/local/bin, where such things are stored.

as for the /opt thing, he was talking about the tarballs, not the config files. personally, i alwas stick compiled apps that dont have an install target into /usr/local, and i use /opt as a miscellanious folder, but thats just me.

im sorry if that was all incomprehensable gobbledegook, feel free to email me if you need clarification on anything.

---

### Post by mlind on 2006-06-20
[QUOTE=Joey French]Yes, I have long since set my hidden files to be visible, so no hope for me there. However, the movement to the /opt folder may be a good idea. It is not really a big deal, but it seems that my home folder is now full of them, and I was wondering what others has to say about their homes collecting debris over time.[/QUOTE]

You have to do house cleaning every now-and-then. Just remove any .dot folders
of applications you won't be installing again. If you use Azureus or Beagle, make
sure you check remove or package their logs or add a weekly/monthly cronjob for
this. Those two seem to make enormous log files...

As for tarball sources, if you don't configure them with --prefix=$HOME and install,
those will automatically go to /usr/local usually. sudo is just for aquiring root
privileges and has nothing to do with where extracted data will end up.

I wonder if there's any apps available for linux that would display graphical map
about your linux partitions and containing files. Would be easier to find useless files
this way. Windows has excellent app for this called "space-monger".

---

### Post by Joey French on 2006-06-22
Maybe I am giving the impression that I am new to linux, I am not. I am just curious as to why all config files would be in the home folder. It sort of makes sense, but it seems that everytime I even try out a new program, a new file from that program ends up at home. I can delete these files, sure, but I am curious why they would all be there in the first place (and why when a program is "completely removed" the config file is not taken with it). The /opt placement for tarballs is cool, I will begin using that route to get some of the other progs out of my home folder. So, to get progs to extract to /opt from now on, what prefix do I give it? Like for example, I want to extract the new firefox to my /opt when the tarball is in /home?

Thanks all!

Joey French

---

### Post by mssever on 2006-06-22
[quote=Joey French]So, to get progs to extract to /opt from now on, what prefix do I give it? Like for example, I want to extract the new firefox to my /opt when the tarball is in /home?[/quote] 
Generally speaking, you can do
```
./configure --prefix=/opt/foo #where foo is the name of your program
make
sudo make install
```

---

### Post by Kibbo on 2006-06-22
[QUOTE=Joey French]Maybe I am giving the impression that I am new to linux, I am not. I am just curious as to why all config files would be in the home folder. It sort of makes sense, but it seems that everytime I even try out a new program, a new file from that program ends up at home. I can delete these files, sure, but I am curious why they would all be there in the first place (and why when a program is "completely removed" the config file is not taken with it). 
Joey French[/QUOTE]

Linux newbie here, so I'm not sure if I'm properly addressing your questions.

From what I understand, every app (that would have a config file in the first place) will store a copy of it's config file in the home directory of every user.  That file will hold all the default settings for that app.  When a preference is changed in that app, it is changed in that file in the user's home directory.  

As to why that is the case, it probably follows from the fact that unix has always been a multi-user platform, and as such application configuration is designed to be local, not global.

As to why that file is not removed on an uninstall, have you been using the "--purge" modifier for apt-get?  I've never closely watched it, but I was under the understanding that it is supposed to remove the config files.

---

### Post by mssever on 2006-06-22
[quote=Kibbo]As to why that file is not removed on an uninstall, have you been using the "--purge" modifier for apt-get?  I've never closely watched it, but I was under the understanding that it is supposed to remove the config files.[/quote] 
I don't think that apt knows about per-user config files. They aren't in the list of installed files, so the purge routine would have to search every user's home directory to remove files. I think it would be great if it would do that, but in a multi-user scenario, users might become upset if the admin started deleting files from their home directories...

---

