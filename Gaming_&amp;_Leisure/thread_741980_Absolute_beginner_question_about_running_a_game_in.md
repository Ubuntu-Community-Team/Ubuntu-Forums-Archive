---
title: "Absolute beginner question about running a game in Ubuntu"
date: 2008-04-01
forum: Gaming &amp; Leisure
---

### Post by Bellicus on 2008-04-01
I downloaded a game called tremulous-1.1.0-installer.x86.run, but when i doubleclick it all i get is: 

Could not open the file /home/administrator/Desk…s-1.1.0-installer.x86.run.
gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.

There is two character codings from the menu, but none of them work. ](*,)

---

### Post by aoanla on 2008-04-01
> **Bellicus said:**
> I downloaded a game called tremulous-1.1.0-installer.x86.run, but when i doubleclick it all i get is: 

Could not open the file /home/administrator/Desk…s-1.1.0-installer.x86.run.
gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.

There is two character codings from the menu, but none of them work. ](*,)

Open a terminal.
In that terminal, type

. ~/Desktop/tremulous-1.1.0-installer.x86.run


(the initial . is important!)

If this doesn't work, then it is most likely the case that the file hasn't had its executable bit set (this is a property which tells linux that the file can be executed as a program, rather than simply read like a text file).

You can set this by typing

chmod +x ~/Desktop/tremulous-1.1.0-installer.x86.run

then try double-clicking the file again, or running it from the terminal as above.

---

### Post by Bellicus on 2008-04-01
I got the installer working now, what fixed it was "allow executing file as program" from properties for the file, but i got another problem now: when it gets to the installation path it says it got no write permission to /usr/local/games

---

### Post by aoanla on 2008-04-01
Right. And, indeed, it shouldn't - /usr/local/games is owned by root, and you're running the installer as you.

Generally, it is not advisable to run random scripts as root, because it means that it's easier for them to do horrible things to your system (either deliberately, or accidentally). If you trust the installer, you can run it as root by using sudo:

sudo ~/Desktop/tremulous-1.1.0-installer.run

which will then ask your for your administrator password, as normal for this kind of thing.

Otherwise, it may be possible to get the tremulous installer to install to your home directory (in which case, it wouldn't need to run as root because you own your home directory yourself). This is actually what the installer "should" probably do anyway, but clearly it doesn't.

---

### Post by Junkieman on 2008-04-01
Hi Bellicus

An easier way to install games would be to use synaptic package manager (accessed through your main menu) - the game you are looking for appears to be in the multiverse repository. It's a matter of searching for what you want and marking the game for installation. this method will also install extra  libraries that the game might need to work properly.

I cant be more specific without sitting in front of my pc, but hope it helps.

---

### Post by Bellicus on 2008-04-01
Sorry guys, but i have no clue what a scripts, root, multiverse repository or libraries is, so its hard to understand what you mean. But i found the synaptic package manager and are downloading lots of games now (tremulous one of them), hopefully i'll figure out how to run them, or else ill be back to bother people on the forum further. :)

---

### Post by aoanla on 2008-04-02
root = the "Administrator" account on a linux (or, generally, Unix) system.

script = an executable file which, unlike a compiled executable, is actually a set of plain text instructions for the computer to follow. Something like a DOS batch file, if you know what those are. Your tremulous ".run" file is certainly a script, and your initial issue with "running" it was due to it being ambiguous if you wanted to read it (because, after all, it is just text) or have linux follow it as instructions.

repository = a location, usually accessible via the internet, which contains a large number of programs, as "packages". In the case of Ubuntu, the available packages are split amongst four repositories - "main", "universe", "multiverse" and "restricted" - depending on who provides them and their legal status. It is these repositories which Synaptic, for example, checks when it gives you the list of software it can install, and which the update manager checks when it looks for updates to installed programs.
You don't need to worry about enabling any of the standard Ubuntu repositories, as they are all enabled by default in Gutsy/7.10 - in older releases, multiverse wasn't enabled by default, which is why the other respondant mentioned it.

libraries = on any computer system, not just linux and including Windows, a "library" is a file containing useful algorithms that can be used by other programs. This is intended to prevent developers from having to write everything from scratch, and also provides consistency and other useful things. For example, there are libraries for displaying graphics, sound, using a network, and for performing various mathematical operations. Indeed, almost everything "generally useful", and many things that aren't, are actually done by libraries - the specific code for a given application then only has to worry about the results of those operations. 
Of course, there are problems, therefore, if you install a program that expects a library that you don't have. In Windows, this is usually solved by packaging all the needed libraries with the program, preventing any issue. In Linux, the advantage of using a package-based installer (like Synaptic) is that the package containing a program also contains a list of other packages which it needs to be installed so that it will work - the majority of these will be providing libraries that the program requires.

---

