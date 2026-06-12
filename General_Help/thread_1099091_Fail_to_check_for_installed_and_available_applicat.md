---
title: "Fail to check for installed and available applications"
date: 2009-03-17
forum: General Help
---

### Post by 2roombas on 2009-03-17
Drats, now I have another problem I'm a newbie with a laptop running 8.04.  I was trying to install wine so I could add my beloved Bookworm game but ever since the Applications>Add/Remove says this...

[B]Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.[/B]

When I go t Systems>Administration>Synaptic Package manager I get this....
[B]
E: Type `F' is not known on line 17 in source list /etc/apt/sources.list
E: The list of sources could not be read. Go to the repository dialog to correct the problem.
W:  cache>open() failed please report.
[/B]
I researched and found another very similar problem...
[http://ubuntuforums.org/showthread.php?t=923806](http://ubuntuforums.org/showthread.php?t=923806)

... however it's also different enough that I'm not sure what to do!    I sure do wish Ubuntu had a System Restore feature like Windows does. I used that quite often when I made stupid boo-boos.:(

---

### Post by taurus on 2009-03-17
There is something wrong with line 17 in your /etc/apt/sources.list.  Until you fix that, you are not going to update or install anything from the repos.

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by 2roombas on 2009-03-17
> **taurus said:**
> 

```
gksudo gedit /etc/apt/sources.list
```

Here is what I get with that...

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy main universe
multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy main
universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-updates main
universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-updates
main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-security main
universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-security
main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-netbook-base
main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/)
hardy-netbook-base main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-dell-mini
main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-dell-mini
main universe multiverse restricted
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) intrepid main #WineHQ - Ubuntu
8.10 "Intrepid Ibex"

F
----------------------------------

What should I do next?

---

### Post by taurus on 2009-03-17
Is there really an **[COLOR="Red"]F[/COLOR]** at the end?  You need to remove that.  Also, it's a good idea to replace **intrepid** with **hardy** for the wine repo since you are running hardy, not intrepid.  Then, run

```
sudo apt-get update
```

---

### Post by 2roombas on 2009-03-17
> **taurus said:**
> Is there really an **[COLOR="Red"]F[/COLOR]** at the end?  You need to remove that.  Also, it's a good idea to replace **intrepid** with **hardy** for the wine repo since you are running hardy, not intrepid.  Then, run

```
sudo apt-get update
```

True. Yes, I thought that lone "F" looked rather odd.  How do I remove that from that list?

Also, I now see that the wine I tried to install was for 8.10 and not 8.04 too.  

The code you gave *sudo apt-get update* will do what exactly?

---

### Post by taurus on 2009-03-17
To edit /etc/apt/sources.list, run

```
gksudo gedit /etc/apt/sources.list
```
And once you have remove the F and replace the intrepid with hardy from the last line, after you've removed the F, save it and close down gedit editing window.  Then, update your repos with

```
sudo apt-get update
```
Now, try to install wine again with

```
sudo apt-get install wine
```

---

### Post by 2roombas on 2009-03-17
Do I remove the Ibex after Intrepid too?  Or just replace Intrepid"?

---

### Post by Peasantoid on 2009-03-17
You can just leave everything after the # symbol (it's a comment, i.e. something the application ignores).

---

### Post by 2roombas on 2009-03-17
Thank you so much!  My problem is fixed:D

---

### Post by fieroboom on 2009-03-18
> **2roombas said:**
> 

The code you gave *sudo apt-get update* will do what exactly?

Just wanted to answer this real quick so you know in the future...
According to the [apt-get man page](http://linux.die.net/man/8/apt-get):

"**update**
    update is used to resynchronize the package index files from their sources. The indexes of available packages are fetched from the location(s) specified in /etc/apt/sources.list. For example, when using a Debian archive, this command retrieves and scans the Packages.gz files, so that information about new and updated packages is available. An update should always be performed before an upgrade or dist-upgrade. Please be aware that the overall progress meter will be incorrect as the size of the package files cannot be known in advance."

You can view the manual for just about any program by opening a terminal and running:
```
man <program_name>
```

AND...
You can usually type that exact same thing into google and get the pretty html-formatted version of the same information.
:D
-Paul

---

