---
title: "No fetch from multiverse for days?"
date: 2006-08-07
forum: Desktop Environments
---

### Post by stevehaines on 2006-08-07
I have been trying to install Java for five days now using Synaptic, Automatix, Easyubuntu, Applications > Add/Remove. All the methods fail eventually with this error message in a terminal:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java5/sun-java5-bin_1.5.0-06-1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java5/sun-java5-bin_1.5.0-06-1_i386.deb)
  Connection failed

What am I doing wrong? Are others having problems downloading from multiverse? Thanks, Steve :(

---

### Post by catlett on 2006-08-07
You aren't going to believe this but just click on the url in your post. It will open a window with the java package for download.
You can open it with gdebi and install it automatically or download it and install it with ```
sudo dpkg -i nameofdeb
```

---

### Post by stevehaines on 2006-08-08
Thanks Catlett! Yes, Ubuntu "seemed" to download Java just like you said. I chose to have it installed . . . but it FLAT disappeared after apparently installing Java. I had to accept the Sun Java conditions, everything looked okay, and a blank directory named "/usr/share/java-1.5.0-sun-1.5.0.06" was created. But nothin is there, and Java doesn't work with Firefox.

I even downloaded and unpacked Sun Java's 1.5.0.7 new update, but now I can't find the Firefox/plugins directory to creat the symbolic link to the Java plugin. What gives? Mozilla/Firefox used to have a subdirectory named "plugins" in the older Hoary and Breezy Ubuntu. I think Dapper installed the browser in /usr/share/firefox, but there is no plugins subdirectory? TIA, Steve

---

### Post by catlett on 2006-08-08
That stinks. I thought the repository was back on line and you could just install the deb.
My firefox plugin folder is in /usr/lib/firefox
I also installed java with ```
sudo apt-get install sun-java5-jre sun-java5-plugin
```

So I guess we'll start with,
Do you have a plugin folder? Is firefox in /usr/lib/firefox?
What happened when gdebi tried to install the deb?
What happens when you run sudo apt-get install sun-java5-jre sun-java5-plugin now that the repository seems to work?

Just for the heck of it, here's my firefox plugin folder.
[IMG]http://i80.photobucket.com/albums/j180/brthomas503/plugin.jpg[/IMG]

---

