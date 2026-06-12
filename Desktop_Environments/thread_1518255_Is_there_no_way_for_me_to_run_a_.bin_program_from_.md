---
title: "Is there no way for me to run a .bin program from the gui?"
date: 2010-06-26
forum: Desktop Environments
---

### Post by odielag on 2010-06-26
I asked in Absolute Beginners forum, and so far it seems, there actually is no easy way to run a .bin program in the gui without using the terminal and typing.

[http://ubuntuforums.org/showthread.php?t=1518216](http://ubuntuforums.org/showthread.php?t=1518216)

This seems like a major design flaw if true. What gives?

---

### Post by Dr_Willis on 2010-06-26
just to be clear a '.bin' could be ANYTHING. (bin just means binary)
it could be a full GUI self installing app. it could be a script, it could be a command line only tool.

It could not even be an installer of any type. cue/bin and  many emulators use .bin files for their roms.

The use of .bin is one of those vague areas where there are no standards.

So in short with each .bin installer the people making the .bin should include VERY clear docs on how to execute/run it.

---

### Post by moongia on 2010-06-26
you can try app runner.

[http://hacktolive.org/blog/2009/app-runner-run-apps-easily-on-debian-ubuntu-linux/](http://hacktolive.org/blog/2009/app-runner-run-apps-easily-on-debian-ubuntu-linux/)

---

### Post by eltonw on 2010-06-26
> **odielag said:**
> I asked in Absolute Beginners forum, and so far it seems, there actually is no easy way to run a .bin program in the gui without using the terminal and typing.

[http://ubuntuforums.org/showthread.php?t=1518216](http://ubuntuforums.org/showthread.php?t=1518216)

This seems like a major design flaw if true. What gives?

How about this? Right click on the *.bin file,*[COLOR="Red"] change the permissions to make it executable[/COLOR]*, then click on it and run it.
To give an example, that is how I downloaded and installed the Google Earth app which is a bin file.

cheers...):P

---

### Post by Dr_Willis on 2010-06-26
Some .bin files are executables with a GUI, others are not. Some (such as the nvidia driver installers) require X to not even be running to work properly. 

Some may need to be ran as root, others ask for root permissions when ran, some  can be ran as a user. Theres too many variables. 

I have even seen 'bin' files that just print out a EULA and ask the user to enter 'Y' Then generate a package the user then installs via the package manager systems. 

So it all boils down to  a person needs to examine what the .bin is supposed to be doing and how best to do it.

That Apprunner tool mentioned above is a very neat idea. But it still boils down to a user needing to decide what to do with the bin.

Its not a 'design flaw' with linux or ubuntu. its a 'flaw' with the idea of using .bin as an extension for one thing, and  the use of 'executable installers' instead of 
the package manager system.

And just for the record. I have seen .bin installers that you can just double click on and the installer loads up with a gui and runs, i have also seen the reverse where you Cant run them in X at all, and must use the shell.  (actually you must use the console in the case of some X driver installers)

---

