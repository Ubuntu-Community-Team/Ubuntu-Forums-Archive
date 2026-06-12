---
title: "Newbie needs help running... installing apps"
date: 2006-01-04
forum: General Help
---

### Post by Sopranosmainman on 2006-01-04
Hey guys finally got the linux up and running.. here are some questions now... i downloaded mozilla firefox.... extracted it to a folder.. but i cant open it up... can u guys please point me in that right direction... then i downloaded frostwire.... its an .rpm file... i know linux uses these alot.... but i have no clue on how to open/install/run these types of things. Any help would be greatly appreciated.... just tryin to take it one step at a time here and learn the basics. Thanks

---

### Post by Omnios on 2006-01-04
You need alien from synaptic to convert .rpm 's

```
sudo apt-get install alien
sudo alien package-name.rpm
sudo dpkg -i package_name.deb
```

 Note all .rpms work

 ALso if you get extra repositories and backports you can access a lot more and newer software with synaptic. Check out the repositories section on the forum

---

### Post by Sopranosmainman on 2006-01-04
ok i downloaded alien.. now i have no clue what to do... if u dont mind may i have a little tutorial on how to use it... and i dont even  have a clue of where to enter any code.... plz i am a complete newbie.... i appreciate all the help i can get....


Also i still cant run mozilla firefox or thunderbird... i have downloaded... extracted to folders and dont know what to do from there. THanks

---

### Post by Omnios on 2006-01-04
cd (change directory to to the directory you have the rpm in. Use ls (list) to check if the file is there. Then

```
sudo alien package-name.rpm

```

 this will make a deb (ubuntu uses deb's) then
 
```
sudo dpkg -i package_name.deb
``` 

 this should install the program

 As for a tarball (tared packages are commonly called tarballs) untar them and there should be a install text help file with instructions on how to install the package.

 ALso you will need build-essentials.



you know you can get firefox from synaptic. 

 Menu / sytem / Administration / Synaptic Package manager ?.

 WHen I first started I stuck to installing main programs such as firefox with synaptic as they are known to work with the current version of Ubuntu. If you want bleading edge do a forum search or google search for installing firefox in Ubuntu.

 If you need help with terminal commands I a web link page for that.

[]("http://ubuntuforums.org/showthread.php?t=45651")

 There is also a good link on that page

---

### Post by gingermark on 2006-01-05
[QUOTE=Omnios]you know you can get firefox from synaptic. 

 Menu / sytem / Administration / Synaptic Package manager ?.

 WHen I first started I stuck to installing main programs such as firefox with synaptic as they are known to work with the current version of Ubuntu. If you want bleading edge do a forum search or google search for installing firefox in Ubuntu.[/QUOTE]

Or in Kubuntu use Adept (K-Menu --> System --> Adept)

This really is the best way to install programs. When I was a newbie I tried to install converted debs with alien and even some deb files from Debian (which, as a rule of thumb, can break things).

When you first install Kubuntu the repository of programs Adept has access is to is limited, but you can enabe the others already in your sources.list file (in Adept click 'Adept' on the top menu and select 'Manage Repositories' the enable the greyed out addresses). This will give you access to almost any program you will need, and other repositories that you can add (such as the [Penguin Liberation Front](http://wiki.ubuntu-fr.org/doc/plf) one) can give you access to even more software you might need.

You should pick this all up pretty quickly.

P.S. Adept is a frontend for a command called apt, so if someone tells you to 'apt-get install' something, it's the same thing, just using the command line instead.

Oh and Omnios' page was this one: [http://ubuntuforums.org/showthread.php?t=45651](http://ubuntuforums.org/showthread.php?t=45651)

---

### Post by Kræn Knude on 2006-01-05
You wrote that you don't have any clue about where to enter code. Just in case you haven't figured this out, here's what you do:

Open the K- menu (you'll find it down in the bottom of your desktop)

Go to system -> Terminal Program (konsole)

This opens a textbox in which you can write commands.

Most people trying to help you, will give you a command since this is easier than to tell you where to point and click in a graphical user interface. It might feel like a big step entering commands, but it's no biggie, you'll get used to it in no time.

---

### Post by ap.sampson on 2006-01-05
All of your help is fine and dandy, except for one thing...firefox doesn't come from mozilla in RPM form.  As for getting Firefox from the Package Manager...you can, but its slower and only 1.07

For help installing Firefox 1.5, go here:
[https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

the directions are fairly straight forward.  If you have an questions, PM or email me.

Cheers!

PS: I agree with Omnios about adding repositories.

---

### Post by Sopranosmainman on 2006-01-05
Thanks guys, really helpful. i appreciate it!

---

