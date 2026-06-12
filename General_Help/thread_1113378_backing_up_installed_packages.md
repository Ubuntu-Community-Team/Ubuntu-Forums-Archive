---
title: "backing up installed packages"
date: 2009-04-01
forum: General Help
---

### Post by em3ry on 2009-04-01
i'm running ubuntu 8.04 with gnome. after installing from cd i have manually installed many packages using synaptic. my hardware is buggy so someday i may have to reinstall the os from cd. (its already happened once). i would like to store a list of installed packages (using 'dropbox' online storage [2 gigabytes free]) and if i have to reinstall the os from cd then afterward just point synaptic to that list and have it reinstall those packages. is that or something like that possible?

---

### Post by cariboo on 2009-04-01
You can use aptoncd to create an iso of all the files in /var/cache/apt/archves. Aptoncd is in the repositories.

Jim

---

### Post by James_Lochhead on 2009-04-01
If you are not looking to back up specific settings you can do it this way:

In Ubuntu packages can be installed via the terminal using the command sudo apt-get install <package1> <package2> etc. All you have to do is make a text file with this command in plus every application you have installed. For example, if I have banshee and linux dc++ installed I would have:

sudo apt-get install banshee linuxdcpp

If you had to re-install you would just have to paste this command into the terminal and all the necessary packages would be downloaded and installed automatically.

---

### Post by todak on 2009-04-01
Using synaptic, go to **File> Save Markings As...**. Then a window will open so that you can give your file a name. If you want to save the entire state of installed packages and not just the changes you made, check the box in the lower left corner of the window. Then copy the file someplace portable. When you reinstall ubuntu, then use synaptic to **Read Markings...**, browse to the file you created and apply, then all of your packages in the list will be installed. This only applies to the version of Ubuntu you are using. The list created will also have packages you have installed from outside the repositories. You can edit these packages out of the list so that synaptic will not complain of not being able to find the package during the re-installation process. See [here]("http://ubuntuforums.org/showthread.php?t=1057608") for further info.

---

### Post by em3ry on 2009-04-01
great. exactly what i was looking for. thanx

---

