---
title: "Synaptic problems, bad repository?"
date: 2009-03-15
forum: General Help
---

### Post by yarnoiser on 2009-03-15
Okay, I was using this book titled "Ubuntu For Non-Geeks, 3RD Edition" to learn how to install packages for playing encrypted DVD's. Here are the commands I entered into the root terminal:

wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -o /etc/apt/ sources.list.d/medibuntu.list

then:

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -o -| apt-key add -&& apt-get update

finally:

apt-get install libdvdcss2

(-note: I did not use any sudo commands because I was using the root terminal)

Not only did it not work, but now when I try to open synaptic, the following error message displays:

An error occured
the following details are provided:

E:Type'--18:34:21--' is not known on line 1 in source list /etc/apt/
sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E:_cache->open()failed,please report.

I'm a beginner at this, so I had no idea what exactly the commands were doing. I assumed that they would not destroy anything, like, say, my primary ability to download updates and new files. Anyhow could someone out there tell me the following:

What exactly did the commands do? Did they switch synaptic from the ubuntu repository to something that no longer works?

How do I fix the problem? I would like to repair this glitch as quickly as possible and the book does not include instructions for undoing its projects.

What is the Repository dialog mentioned in the error message?

Any help would be appreciated.

---

### Post by taurus on 2009-03-15
Try running these commands from a terminal again.

```

sudo wget http://www.medibuntu.org/sources.list.d/hardy.list --output-document=/etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
sudo apt-get install libdvdcss2
```

---

### Post by oldos2er on 2009-03-15
"What exactly did the commands do?"

  'wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -o /etc/apt/ sources.list.d/medibuntu.list' uses wget to download the package list for Ubuntu Hardy, and writes it to the file /etc/apt/sources.list.d/medibuntu.list. 

  'wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -o -| apt-key add -&& apt-get update' uses wget again to download the public key for Medibuntu, adds it to your keyring, and updates your package list (or sources, if you prefer. The list is available graphically in Gnome via the menus System, Administration, Software Sources).

 'apt-get install libdvdcss2' should install the package libdvdcss2. But it encountered an error in /etc/apt/sources.list.d/medibuntu.list. Follow Taurus's instructions to fix it. Or, you could open a terminal and enter 'gksu gedit /etc/apt/sources.list.d/medibuntu.list' to edit the file.

 You are using 8.04 Hardy Heron, right?

---

### Post by yarnoiser on 2009-03-15
YAAAAAAAAAAAAAAAAAHOOOOOOOOOOOOOOOOOOOOOOOO! The instant I did what taurus sugested, the update manager came back online! I would also like to thank oldos2er for explaining what the commands mean. Thank you so much guys!

---

