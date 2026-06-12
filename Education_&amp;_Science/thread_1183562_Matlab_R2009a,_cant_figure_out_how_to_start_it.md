---
title: "Matlab R2009a, cant figure out how to start it"
date: 2009-06-10
forum: Education &amp; Science
---

### Post by sinnadyr on 2009-06-10
Innstalled Matlab and let it write to /opt/matlab/ while installing. In this folder I find

```
bin	 install_matlab	  licenses	 rtw		sys			 update
extern  install_matlab.out  license.txt  simulink   toolbox		 X11
help	java				patents.txt  stateflow  trademarks.txt
```

After the innstallation was completed, I started matlab and it all worked out just fine. Then I closed the application, tried to start it up again but can not figure out how to do it :\

In ~/.matlab/R2009a/ I find

```
cwdhistory.m					  matlabprefs.mat
dastudio.prf					  matlab.prf
doc_toolbar_documents.cwd_r4.xml  shortcuts.xml
history.m						 sl_library_browser_repos
MATLABDesktop.xml				 toolbox_cache-7.8.0-2557220496-glnx86.xml
```


Thanks in advance for all your help

---

### Post by kleinric on 2009-06-10
what is in the bin directory? Thats where they usually put the binarys....
So its probably /opt/matlab/bin/matlab? or something like that...

If this doesn't come right, post back the contents of that directory and i'll see if i can find it...

---

### Post by phaed on 2009-06-10
The startup file is a bash script in the bin folder, which for you would be /opt/matlab/bin/matlab.  I had issues with permissions when I installed Matlab into the /opt folder, especially when I later tried to add some M files that start when Matlab starts, so I installed it in my home folder like this:

/home/USERNAME/.matlab

So my startup file is /home/USERNAME/.matlab/bin/matlab

That might fix the problem.

Also, if you want to add an entry for Matlab in your menus, make sure you type the command like this:

/path/to/bin/matlab -desktop

Notice the -desktop at the end.  Without that, Matlab will always close within seconds.  It took me forever to figure that out.

---

### Post by sinnadyr on 2009-06-10
Thank you so much! But how do I uninstall it so that I can reinstall it in my home directory?

A stupid friend of mine told me to install to /opt/ :P

---

### Post by lethalfang on 2009-06-10
Make a symbolic link of the bash script file into your PATH, e.g., 

```
sudo ln -s /opt/matlab/bin/matlab/bin/matlab /usr/bin
```

Then, to have a click-able icon in the Application menu: Edit Menu --> New Item, and the command would be "matlab -desktop"

---

### Post by lethalfang on 2009-06-10
> **sinnadyr said:**
> Thank you so much! But how do I uninstall it so that I can reinstall it in my home directory?

A stupid friend of mine told me to install to /opt/ :P

No need to un-install it.
But you need to change the ownership (from root to yourself) of the directory ~/.matlab

---

### Post by sinnadyr on 2009-06-10
> **lethalfang said:**
> No need to un-install it.
But you need to change the ownership (from root to yourself) of the directory ~/.matlab

Dont know much ownerships, could you explain a little further how I do that? 

and did you mean

```
sudo ln -s /opt/matlab/bin/matlab /usr/bin
```
?

Thank you guys so much for the replies

---

### Post by lethalfang on 2009-06-11
> **sinnadyr said:**
> Dont know much ownerships, could you explain a little further how I do that? 

and did you mean

```
sudo ln -s /opt/matlab/bin/matlab /usr/bin
```
?

Thank you guys so much for the replies


MATLAB's configuration files are stored in this directory: ~/.matlab
When you install MATLAB as root, the directory (~/.matlab) is created by root, and therefore those files can only be written as root. You would need to change the ownership from root to your own user_name:

```
sudo chown -R your_user_name ~/.matlab
```

The script file "matlab" that launches MATLAB, if you installed the program in /opt, is the following:
/opt/matlab/bin/matlab
But when you type "matlab" in the terminal, the shell cannot find "matlab" because /opt/matlab/bin is not in the default path that it looks for. 
/usr/bin is one of the directories the shell will look for when you type a command in the terminal, so you need to make a symbolic link to the script file in /usr/bin. You need root privilege to create files in /usr/bin, hence:

```
sudo ln -s /opt/matlab/bin/matlab /usr/bin
```

---

### Post by sinnadyr on 2009-06-11
Thanks a lot, now it all work as it should do!

By the way, used **sudo chown -R** instead of **sudo chmod -R** because I got this message:
```
sinnadyr@sinnadyr-laptop:/usr/bin$ sudo chmod -R sinnadyr /home/sinnadyr/.matlab/
chmod: invalid mode: `sinnadyr'

```

But what do the -R do? Thanks a lot man, really needed this

---

### Post by lethalfang on 2009-06-11
> **sinnadyr said:**
> Thanks a lot, now it all work as it should do!

By the way, used **sudo chown -R** instead of **sudo chmod -R** because I got this message:
```
sinnadyr@sinnadyr-laptop:/usr/bin$ sudo chmod -R sinnadyr /home/sinnadyr/.matlab/
chmod: invalid mode: `sinnadyr'

```

But what do the -R do? Thanks a lot man, really needed this

Oh yeah, it should've been chown (change ownership). I made a typo. Chmod means to change mode, e.g., being able to read/write/execute. 
-R is a flag that stands for "recursive," which means change ownership of the directory, **and** every file and subdirectory. Without it, it'll only change the directory itself.

---

### Post by paperplate9 on 2009-06-20
> **phaed said:**
> 
/path/to/bin/matlab -desktop

Notice the -desktop at the end.  Without that, Matlab will always close within seconds.  It took me forever to figure that out.

Oh man thanks for that tip, I always wondered why it would close if I didn't select that it was a 'run in terminal' app...and I'd have that ugly terminal window with useless debug/log stuff.

---

### Post by baytuni on 2009-09-21
Ok. I've tried to make a symbolic link as described, but it does not work. I ceated the symbolic link into /usr/bin and gives this following error. 

```
bop@hal:/usr/bin$ ls m*
ls: cannot access matlab: Too many levels of symbolic links
m4                           metacity-message       motd+shell
macptopbm                    metacity-theme-viewer  mousetweaks
mag                          metacity-window-demo   mozplugger-controller
magnifier                    metaflac               mozplugger-helper
mail                         mf                     mozplugger-linker
mail-lock                    mf-nowin               mp2enc
mailq                        mformat                mp3c
mail-touchlock               mft                    mp3info2
mail-unlock                  mgrtopbm               mpartition
mailx                        mid3iconv              mpeg2enc
make                         mid3v2                 mpegtranscode
make_driver_db_cups          midi2ly                mplex
make_driver_db_lpr           min12xxw               mrd
make-googleearth-package     minfo                  mren
makeindex                    mjpeg_simd_helper      mscompress
makeinfo                     mkbimage               msexpand
make-memtest86+-boot-floppy  mkcamlp4               msgattrib
make_method                  mkdiskimage            msgcat
make_services                mkfifo                 msgcmp
make_strings                 mkfontdir              msgcomm
man                          mkfontscale            msgconv

```
"
ls: cannot access matlab: Too many levels of symbolic links"
what does that supposed to mean?

---

