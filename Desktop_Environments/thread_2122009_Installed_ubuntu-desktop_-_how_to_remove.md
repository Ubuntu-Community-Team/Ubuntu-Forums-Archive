---
title: "Installed ubuntu-desktop - how to remove?"
date: 2013-03-03
forum: Desktop Environments
---

### Post by Kols on 2013-03-03
Yep, I just installed ubuntu-desktop on my lubuntu-box... 

Never mind why I did that, what I'd like to know, is how to remove it with the least amount of pain.

Steps I've done so far (probably to make fixing it harder, hehe)

```
sudo apt-get remove ubuntu-desktop
```

which only removed a ~50kb package. I then thought I'd auto-clean, to get rid of all the packages that came with ubuntu-desktop

```
sudo apt-get auto-clean
```

which seemed to remove a mix of lubuntu-installed packages, and new packages from ubuntu-desktop.

Without any backup - is it possible to remove all new packages installed by ubuntu-desktop, and keep the old packages that both OS'es use?
I'm thinking, get a list of those packages, and just 

```
sudo apt-get remove [ALL THOSE PACKAGES]
```

or something...

Please help me with this one!

cheers!=)

---

### Post by cortman on 2013-03-03
I'm sure one of [these links]("https://www.google.com/search?q=how+to+completely+remove+ubuntu-desktop") will provide the required information.

---

### Post by claracc on 2013-03-04
Follow the instructions given in this link: [http://www.psychocats.net/ubuntu/purelubuntu](http://www.psychocats.net/ubuntu/purelubuntu) to remove ubuntu desktop.

---

### Post by cortman on 2013-03-04
> **claracc said:**
> Follow the instructions given in this link: [http://www.psychocats.net/ubuntu/purelubuntu](http://www.psychocats.net/ubuntu/purelubuntu) to remove ubuntu desktop.

Psychocats FTW. :)

---

### Post by Kols on 2013-03-09
Hi again!

I ended up doing it the hard way. Backing up everything in home-folder except for most configs, and complete reinstallation. Actually, this turned out to be a better solution, because this time I had an incentive to partition to / and /home, and I'm now running 12.10.

Anyways, thanks for answering! I know know how to do it for later. Will mark thread solved!
 
What's really annoying, is that I couldn't seem to find any command that only removes the the newly installed packages. For example, if Lubuntu uses package 1 and 2 and Ubuntu installs package 3 but also installs package 2 if missing - why can't I run a command that only removes package 3?

Cheers!

---

### Post by Krytarik on 2013-03-09
> **Kols said:**
> What's really annoying, is that I couldn't seem to find any command that only removes the the newly installed packages. For example, if Lubuntu uses package 1 and 2 and Ubuntu installs package 3 but also installs package 2 if missing - why can't I run a command that only removes package 3?
Actually, there is:
> **autoremove**[INDENT]autoremove is used to remove packages that were automatically
installed to satisfy dependencies for other packages and are now no
longer needed.[/INDENT]

[...]

**--auto-remove**[INDENT]If the command is either install or remove, then this option acts
like running autoremove command, removing the unused dependency
packages. Configuration Item: APT::Get::AutomaticRemove.[/INDENT]

Source: [http://manpages.ubuntu.com/manpages/precise/en/man8/apt-get.8.html](http://manpages.ubuntu.com/manpages/precise/en/man8/apt-get.8.html)

Might not always work sufficiently though.

Btw, this:
> **Kols said:**
> I then thought I'd auto-clean, to get rid of all the packages that came with ubuntu-desktop

```
sudo apt-get auto-clean
```

which seemed to remove a mix of lubuntu-installed packages, and new packages from ubuntu-desktop.
... is, 1.) misspelled, and 2.) does this:
> **autoclean**[INDENT]Like clean, autoclean clears out the local repository of retrieved
package files. The difference is that it only removes package files
that can no longer be downloaded, and are largely useless. This
allows a cache to be maintained over a long period without it
growing out of control. The configuration option
APT::Clean-Installed will prevent installed packages from being
erased if it is set to off.[/INDENT]

Source: same as above.

Regards.

---

### Post by Kols on 2013-03-10
> **Krytarik said:**
> Actually, there is:

Source: [http://manpages.ubuntu.com/manpages/precise/en/man8/apt-get.8.html](http://manpages.ubuntu.com/manpages/precise/en/man8/apt-get.8.html)

Might not always work sufficiently though.

Btw, this:

... is, 1.) misspelled, and 2.) does this:

Source: same as above.

Regards.

...Not sure if everything is quoted now, but anyways.

I do think I did both autoclean (correct spelling now=P ) and autoremove. The problem was, the extra ubuntu-packages weren't really redundant, as most of them can be used by both Lubuntu and Ubuntu. Even after removing AND purging ubuntu-desktop, all those extra packages lingered. Psychocat suggested a method where one would remove a long list of packages, which mostly were installed by the ubuntu-desktop package, but that one would always run the risk of removing SHARED packages, thus breaking your "main"-system. Therefore, reinstallation of the whole shebang. 

I don't regret that - as a result of the reinstallation, I've learned the following; How to add colors in prompt (not node-colors and such, I had that from before - but color assosiated with ls and grep, etc), that compton is much nicer than xcompmgr-dana, and that there is a an OS called elementaryOS. All good things!=D

---

### Post by Kols on 2013-03-10
Almost forgot; THANKS for the clarifying answer!

---

### Post by cortman on 2013-03-11
> **Kols said:**
> ...Not sure if everything is quoted now, but anyways.

I do think I did both autoclean (correct spelling now=P ) and autoremove. The problem was, the extra ubuntu-packages weren't really redundant, as most of them can be used by both Lubuntu and Ubuntu. Even after removing AND purging ubuntu-desktop, all those extra packages lingered. Psychocat suggested a method where one would remove a long list of packages, which mostly were installed by the ubuntu-desktop package, but that one would always run the risk of removing SHARED packages, thus breaking your "main"-system. Therefore, reinstallation of the whole shebang. 

I don't regret that - as a result of the reinstallation, I've learned the following; How to add colors in prompt (not node-colors and such, I had that from before - but color assosiated with ls and grep, etc), that compton is much nicer than xcompmgr-dana, and that there is a an OS called elementaryOS. All good things!=D

Psychocats' tutorial doesn't run those risks, it only removes non-shared packages installed by ubuntu-desktop. The author of psychocats has been an admin on this forum and knows Linux inside and out.

---

### Post by pinballwizard on 2013-03-11
> **cortman said:**
> Psychocats FTW. :)

Amen!

---

### Post by Kols on 2013-03-18
> **cortman said:**
> Psychocats' tutorial doesn't run those risks, it only removes non-shared packages installed by ubuntu-desktop. The author of psychocats has been an admin on this forum and knows Linux inside and out.

I will not debate you on that. I'll bookmark his site! I'm bound to frak something up soon=P

---

### Post by scottbomb on 2014-01-30
I have this problem as well. Not paying attention to everything I copied/pasted, I accidentally installed ubuntu-desktop. The page on Psychocat's website is for 12.10 and I'm running Kubuntu 13.10. I tried it anyway and got a list of "E: couldn't find..." and "E: Unable to locate..."

Does anyone have a new solution? I wish there were a rule in place stating that package installers should include a comprehensive uninstall utility or a least a list of packages dpkg can read and then remove.

---

### Post by westie457 on 2014-01-30
Did something similar a couple of weeks ago. Got round the cannot find and unable to locate errors the hard way.

It went something like this.

Copied the whole command off the Psychocats site into a text file using gedit.
Removed the error causing package names from the file (leave one space between package names). Once the editing was completed, copied and pasted into the terminal - crossed fingers- hit enter and waited.

All went well then ran ```
sudo apt-get update

sudo apt-get upgrade
```
To see if there was anything no longer needed by the OS.
If there is anything no longer needed ```
sudo apt-get autoremove
```

Hope this helps.

---

### Post by scottbomb on 2014-01-30
I went through and removed all the offending packages but ended up hosing my system. LibreOffice disappeared! Booted into Windows to finish the workday and will re-install tonight. Ugh.

---

### Post by vasa1 on 2014-01-30
@Westie, 
you can look in **/var/log/apt/history.log** for what has been installed
[LIST]
[*]Copy the entire long line that starts with "Install" to a text editor and remove everything from the start of the line until the first package name. Save the contents as mylist (or whatever)
[*]Open a terminal and move to the folder with mylist. Run **sed -i 's/), /)\n/g' mylist**. This introduces line breaks after each package
[*]Run **awk -F: '{ print $1 }' mylist > mylist1**. This gives you a file with just the package names usable by apt-get. But each package is on a separate line
[*]Fix that by running **awk 1 ORS=', ' mylist1 > mylist2**
[*]Manually remove the "**,**" at the very end of the file
[*]After these steps, you're left with something you can use in **apt-get purge**
[/LIST]
This solution is based on what actually happened on your system. What can break it is you did something like 
```
sudo apt-get install ubuntu-desktop, some_other_package1, some_other_package2 
```Then the install line in history.log would not reflect just the installation of packages pulled in by ubuntu-desktop.

---

