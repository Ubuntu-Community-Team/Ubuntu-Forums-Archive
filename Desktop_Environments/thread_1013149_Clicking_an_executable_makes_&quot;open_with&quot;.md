---
title: "Clicking an executable makes &quot;open with&quot;"
date: 2008-12-16
forum: Desktop Environments
---

### Post by s3gfault on 2008-12-16
I had ubuntu gnome version, with wine installed.  The I installed kubuntu-desktop and switched to KDE.  Now when i try to launch an executable file by clicking on it, KDE will only try to open it with WINE.  So I uninstalled Wine (because i'm not really using it) and now instead of launching the executable i get an "open with" dialog.  I'm the owner of the file and it has the executable bit set```
$ ls -l
-rwxr-xr-x  1 david david  52576 2008-12-15 10:16 eclipse*
```from the konsole i can do a ./eclipse and launch the file and it loads up just fine.  But i would like to be able to click on it too, of course.

Any suggestions?

---

### Post by s3gfault on 2008-12-18
bump prime

---

### Post by s3gfault on 2008-12-21
bump

---

### Post by s3gfault on 2008-12-22
good morning.  Any suggestions?

---

### Post by Shazaam on 2008-12-22
Right-click the executable>Properties>Open With? Try changing it to what you want.

---

### Post by s3gfault on 2008-12-22
?
I don't want to open it with anything... this is a program I want to launch it.

---

### Post by Farmer of Bricks on 2008-12-22
> **s3gfault said:**
> I had ubuntu gnome version, with wine installed.  The I installed kubuntu-desktop and switched to KDE.  Now when i try to launch an executable file by clicking on it, KDE will only try to open it with WINE.  So I uninstalled Wine (because i'm not really using it) and now instead of launching the executable i get an "open with" dialog.  I'm the owner of the file and it has the executable bit set```
$ ls -l
-rwxr-xr-x  1 david david  52576 2008-12-15 10:16 eclipse*
```from the konsole i can do a ./eclipse and launch the file and it loads up just fine.  But i would like to be able to click on it too, of course.

Usually, *.exe files are windows programs, and therefore need to be opened with Wine. If you want to try opening it with another program,
1 right-click on the file
2 choose "properties'
3 where it says "file type", there should be a line saying what type of file it is, followed by a little wrench icon.
4 Click on that wrench
5 Now that you have a new properties window, look down near the bottom, where there (should be) a list of programs.
6 click "add"
7 In this new dialogue, find the program you wnat to open it with. 

Of course, if you're trying to run Eclipse, the Java SDK, it's provided in the repositories, and you can download and install it through a package manager, like Adept, Synaptic, or 
```
user@comp: sudo apt-get install eclipse
```

---

### Post by s3gfault on 2008-12-22
i'm sorry if this sounds rude, but why does everyone assume i mean a Windows *.exe file when i say the word executable? (this came up in IRC too).

This is eclipse, by the way, as you deduced.  The repositories do not have the latest version.

I just want to launch the program when i click on it.  Instead when i click on it Plasma makes an "open with" dialog. arg.

---

### Post by Carl Hamlin on 2008-12-22
> **s3gfault said:**
> i'm sorry if this sounds rude, but why does everyone assume i mean a Windows *.exe file when i say the word executable? (this came up in IRC too).

This is eclipse, by the way, as you deduced.  The repositories do not have the latest version.

I just want to launch the program when i click on it.  Instead when i click on it Plasma makes an "open with" dialog. arg.

-----BEGIN PGP SIGNED MESSAGE-----
Hash: RIPEMD160

Right. You're going to need to set the permissions on the executable to 'executable'. I'll bet you a quarter that right now the permissions on the executable disallow execution.

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.9 (GNU/Linux)

iEYEAREDAAYFAklQHcIACgkQyLm4ydrABvdl0ACfdjSOefaSOrqZlOvJzKox7AdX
PVAAoOZR4G78rAq78nzuDlUHtZ3jG2bQ
=2K9R
-----END PGP SIGNATURE-----

---

### Post by s3gfault on 2008-12-22
> **Carl Hamlin said:**
> -----BEGIN PGP SIGNED MESSAGE-----
Hash: RIPEMD160

Right. You're going to need to set the permissions on the executable to 'executable'. I'll bet you a quarter that right now the permissions on the executable disallow execution.

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.9 (GNU/Linux)

iEYEAREDAAYFAklQHcIACgkQyLm4ydrABvdl0ACfdjSOefaSOrqZlOvJzKox7AdX
PVAAoOZR4G78rAq78nzuDlUHtZ3jG2bQ
=2K9R
-----END PGP SIGNATURE-----right, you'll owe me a quarter then.  I'll take paypal.  You could have saved yourself that money by reading the first post :P
>  and it has the executable bit set

---

### Post by s3gfault on 2008-12-23
good morning.

---

### Post by s3gfault on 2008-12-24
hello forums, any suggestions on this problem?

---

### Post by Wisp558 on 2008-12-24
Can you set the "open with" menu to the command "sh" (or bash, I'm not an expert by any means...)? (assuming it's a shell script...)

---

### Post by s3gfault on 2008-12-24
> **Wisp558 said:**
> Can you set the "open with" menu to the command "sh" (or bash, I'm not an expert by any means...)? (assuming it's a shell script...)

Good idea!  I had the same good idea, but it was a no-go.  For one, the "open with" dialog i am presented with will only allow you to pick from programs that are registered somewhere in the kde system, i.e. menu items.  I tried using "Konsole" but that didn't work.  for 2, it's not a shell script, so it probably wouldn't work anyway. for 3, even if this did work, it would just be an ugly work around (i already have a work around, or two).

---

### Post by jamesisin on 2008-12-24
Out of curiosity, what happens if you try to run it from the command line?  That is to say, navigate to its containing folder (your Desktop?) and type its name (./eclipse)?

(Actually, I don't think you'll need the ./ and can just type eclipse.)

---

### Post by s3gfault on 2008-12-24
launches without a hitch.

---

### Post by jamesisin on 2008-12-24
You know, if I look at the properties for bash (under /bin) it lists Wine Windows Program Loader under Opens With.  As does mahjongg (under /usr/games).  I wonder if that isn't supposed to be there for normal operations?  (I am running Gnome.)  What do you see for those two files' properties?

---

### Post by s3gfault on 2008-12-24
i'm not there now to check but im sure the settings are the same as yours.  when i first tried kde4, i had wine installed, and it was trying to launch eclipse as a windows exe with wine.  then i unistalled wine and now i get this darn "open with" dialog

---

### Post by jamesisin on 2008-12-24
Well, take a look at those two (common) applications and match them if possible.  My guess is that either they say something different or you want to add Wine Windows Program Loader to that tab.  Probably they specify something else.  I'm very curious to know.  This is an intersting problem.

---

### Post by s3gfault on 2008-12-24
> **jamesisin said:**
> Well, take a look at those two (common) applications and match them if possible.  My guess is that either they say something different or you want to add Wine Windows Program Loader to that tab.  Probably they specify something else.  I'm very curious to know.  This is an intersting problem.well, I'll look but i think we may be miscommunicating here.  I could launch this program with Wine, or anything else i want just by choosing that thing from my "open with" dialog, but thats not the expected behavior.   what i need it to do is this:

1) i click a file
2) check for associated programs.
3) if it finds one, launch that program with the file i clicked on as arg 1
4) if it does not find one, check if the x perm bit is set
5) if it is not, launch the "open with" dialog
6) if it is, launch it.

this should be the default behavor. this is the way it works in gnome.  what i think happened is that when i had wine installed, it registered itself as the handler for every executable file accidently (instead of just windows ones).  then, when i removed wine something screwed up and now the process short circuits at step 5.

---

### Post by jamesisin on 2008-12-25
You are correct.  I think we are miscommunicating.

I don't think bash EVER runs under Wine.  This is why I am so curious what yours says.  I feel quite certain that my Wine is NOT running my bash, irregarding what the Open With tab has to say.  I may be on the wrong track, but at the very least you have to admit this is an interesting line of reasoning.

(I checked in my System Monitor, ps, and top; and Wine is not running.  I have a bash terminal and mahjongg open.)

---

