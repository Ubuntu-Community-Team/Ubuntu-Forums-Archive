---
title: "[SOLVED] configuration files and the etc directory"
date: 2009-01-04
forum: General Help
---

### Post by eckeroo on 2009-01-04
I've been trying to follow this thread for running a CD encoder called 'abcde'.

[http://ubuntuforums.org/showthread.php?t=109429](http://ubuntuforums.org/showthread.php?t=109429)

What I don't understand is the issue raised by GabrielWolff on post #7:

> 
Hey, I guess the above description is missing one big issue: don't you have to copy the .abcde.conf back to etc?

To which the Thread's original author replied on post #13:

> 
no, you don't have to copy it back (if you do that, all users will use the new file if they dont have their own .abce.conf in their home-dir)

My general question is this: how can each user use utilise their own configuration files for any program he/she uses instead of imposing just one configuration on all users in the /etc directory?

---

### Post by heindsight on 2009-01-04
most programs start by searching for a config file in the user's home directory (eg abcde searches for .abcde in your home dir) and if that's not found, it falls back on a systemwide config file (usually somewhere under /etc).

This isn't universal though, many programs start reading configuration from a global config file (in /etc) and then reads further configuration from a configuration file in the user home directory (in such cases options from the users config file will usually override options from the global file).

many programs also give you the option of specifying a configuration file on the command line. in such cases it will usually follow one of the two above mentioned default behaviours if the user doesn't specify a configuration file, but if the user specifies a configuration file on the commandline then it usually doesn't also read the default configuration files (either in the home directory or /etc).

The idea is that each user is allowed to customise the behaviour of the program to suit their own needs, but there is also some global configuration file (usually with a basic sensible configuration) which individual users can use as a starting point to base their custom configs on (by copying the global file and editing it), or users can just use the global configuration by simply not creating their own configurations.

---

### Post by eckeroo on 2009-01-04
Reading the instructions, I noticed this:
> 
# If you wish to override these system-wide settings, create your own
# [COLOR="Red"].abcde.conf[/COLOR] file in your home directory.

The configuration file in the user home directory is named .abcde.conf with a '.' before the a. Although this detail in the directory is not visible in either Nautilus or BASH, but it appeared to make abcde take notice of my config file in my home directory [before it was just called abcde.conf without a preceding '.' in the file name].

---

### Post by heindsight on 2009-01-04
yes, files starting with a . (dot-files) are normally hidden in the terminal you can use ls -a to see all the files including the hidden files, in nautilus you'll notice there's an option to show hidden files in the View menu.

configuration files in the home directory are (almost) always dot-files, programs tend to be quite specific about the naming of its configuration files, so for example abcde will look for a file called .abcde.conf in your home directory and if that doesn't exist then it just reads /etc/abcde.conf, it doesn't look further for other files in your home directory.

---

