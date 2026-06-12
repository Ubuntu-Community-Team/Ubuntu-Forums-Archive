---
title: "How do I load programs from CD,s"
date: 2009-04-15
forum: General Help
---

### Post by noelc on 2009-04-15
I have attempted to load a couple of programs from Cd,s but either nothing happens or the program one loaded does not work. Am I doing something wrong. The same applies (For some) when I load useing "Wine"

How can I uninstall these programs.

---

### Post by codeseer on 2009-04-15
What types of programs are you trying to get off CDs?

---

### Post by SuperSonic4 on 2009-04-15
In nearly all cases cds contain software for windows, google or synaptic is best for linux stuff

---

### Post by night_fox on 2009-04-15
Did you try opening the .exe with wine instead of the autorum prompt?

---

### Post by noelc on 2009-04-15
I have attempted to load a couple of programs from Cd,s but either nothing happens or the programs loaded do not work. 


Am I doing something wrong. The same applies when I attempt to load useing "Wine" Nothing happens?


How can I uninstall these programs.

---

### Post by taurus on 2009-04-15
Sounds to me like you are trying to install/run windows programs from the CD in Ubuntu.  What are the names of those programs?

---

### Post by noelc on 2009-04-15
> **taurus said:**
> Sounds to me like you are trying to install/run windows programs from the CD in Ubuntu.  What are the names of those programs?

CS3 master collection

---

### Post by codeseer on 2009-04-15
> **noelc said:**
> CS3 master collection

I think some people have that working in Wine. I'll look around. But it's a pretty big program. You would most definitely need to get some libraries to help Wine out, like from Winetricks.

On a side note. Have you taken a look at [The Gimp]("http://www.gimp.org/about/introduction.html")?

Edit:

Here is the information on it: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=6584]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=6584")

It's not yet fully supported by Wine.

You could alternatively use the wide array of applications that are freely available on Linux to form your own 'CS3 Master Collection'. You could also install VirtualBox, if you have a spare copy of Windows, and install Windows within VirtualBox and then run CS3 from there; this would still need the required amount of memory in the system requirements of CS3 dedicated to the VirtualBox. Another option would be to use a copy of Windows to dual-boot, having Windows installed just for the use of CS3 essentially.

---

### Post by noelc on 2009-04-15
> **night_fox said:**
> Did you try opening the .exe with wine instead of the autorum prompt?

Yes first I highligthed the auto run for the entire CD clicked open with "Wine" = Nothing. Then I located the .exe only for the CS3 program followed the same process = nothing.

I,m told you can run CS3, and adobe flash useing wine.

---

### Post by codeseer on 2009-04-15
> **noelc said:**
> Yes first I highligthed the auto run for the entire CD clicked open with "Wine" = Nothing. Then I located the .exe only for the CS3 program followed the same process = nothing.

I,m told you can run CS3, and adobe flash useing wine.

I assume you mean the Flash design software; you can install the Flash plugin natively on Linux, if you need it for viewing websites.

---

### Post by noelc on 2009-04-15
> **codeseer said:**
> I think some people have that working in Wine. I'll look around. But it's a pretty big program. You would most definitely need to get some libraries to help Wine out, like from Winetricks.

On a side note. Have you taken a look at [The Gimp]("http://www.gimp.org/about/introduction.html")?

Edit:

Here is the information on it: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=6584]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=6584")

It's not yet fully supported by Wine.

You could alternatively use the wide array of applications that are freely available on Linux to form your own 'CS3 Master Collection'. You could also install VirtualBox, if you have a spare copy of Windows, and install Windows within VirtualBox and then run CS3 from there; this would still need the required amount of memory in the system requirements of CS3 dedicated to the VirtualBox. Another option would be to use a copy of Windows to dual-boot, having Windows installed just for the use of CS3 essentially.

I am aware of Gimp but prefer to use CS3 as all my video tutorial (100,s) are for CS3.

If I cant get it to work in "wine" then a virtual box is I think is my only other alternative. Sort of defeats the purpose of moving away from Windows tho

---

### Post by codeseer on 2009-04-15
> **noelc said:**
> I am aware of Gimp but prefer to use CS3 as all my video tutorial (100,s) are for CS3.

If I cant get it to work in "wine" then a virtual box is I think is my only other alternative. Sort of defeats the purpose of moving away from Windows tho

Have you looked at [GimpShop]("http://www.gimpshop.com/") then? People say that it is easy to follow tutorials designed for Photoshop while using Gimpshop. It essentially tries to mimic the layout of Photoshop.

---

### Post by tripolitan on 2009-04-15
For what its worth and if I were you, I would use equivalent native Linux applications instead. You have already made the biggest jump and switched operating systems, now all you have to do is discover all the wealth of its native applications. Running Windows programs under wine is a complete waste of time.

---

### Post by taurus on 2009-04-15
> **tripolitan said:**
> For what its worth and if I were you, I would use equivalent native Linux applications instead. You have already made the biggest jump and switched operating systems, now all you have to do is discover all the wealth of its native applications. Running Windows programs under wine is a complete waste of time.

And besides, some people think that wine is the silver bullet.  They think they can just install and run whatever windows program with it and when they find out they can't, they then get all mad.

---

### Post by tripolitan on 2009-04-15
You can blame that on the overzealous Linux enthusiasts/preachers who, in my opinion, cause more harm than good. I came to my conclusion after wasting a great deal of time (many weeks) wrestling with WINE.

---

### Post by noelc on 2009-04-16
> **tripolitan said:**
> For what its worth and if I were you, I would use equivalent native Linux applications instead. You have already made the biggest jump and switched operating systems, now all you have to do is discover all the wealth of its native applications. Running Windows programs under wine is a complete waste of time.

Yes that would be my preferance as I want to move completely away from Windows and will endevour to do so when I can find a platform thats supports my needs 100%. I assume all Linux applications are listed under programs>add/remove. Of course this assumes there is a Linux equvalent for most windows applications. 

Is there an equivalent to this? [http://www.ourpix.com/products.html](http://www.ourpix.com/products.html)

Or this? 

[http://www.adobe.com/products/photoshoplightroom/](http://www.adobe.com/products/photoshoplightroom/)

I will check our Gimp
to see if it has RAW processing ability or filter plug ins

So far though I must say I am impressed with Linux given I,ve only used it for a week now.

---

### Post by codeseer on 2009-04-16
"All" Linux applications aren't listed anywhere on your system. Some applications still require you to go to a website and download them and install them manually. However, the most common ones are listed in the Add/Remove section; the wider selection is located under the System->Administration->Synaptic Package Manager menu.

Gimp does support RAW, with a plugin such as [UFRaw]("http://ufraw.sourceforge.net/"), and does have a great number of plugins. There's also an extension for it that supports photoshop plugins somewhere; I'll look into this for you.

Here's some links related to that:

[http://www.rawtherapee.com/?mitem=2]("http://www.rawtherapee.com/?mitem=2")
[http://www.bibblelabs.com/products/bibble/bibble4.html]("http://www.bibblelabs.com/products/bibble/bibble4.html")
[http://www.cybercom.net/~dcoffin/dcraw/]("http://www.cybercom.net/~dcoffin/dcraw/")

Which program are you talking about in the 'ourpix' link? There's 4 listed there.

Concerning Lightroom, check out these:

Free:
[http://www.digikam.org/drupal/about/features9x]("http://www.digikam.org/drupal/about/features9x")
[http://picasa.google.com/linux/]("http://picasa.google.com/linux/")

Commercial:
[http://www.lightcrafts.com/products/index.html]("http://www.lightcrafts.com/products/index.html")

I guess it all depends in the functionality you're looking for.

Edit:

Here's the photoshop plugin support for Gimp:
[http://www.gimp.org/~tml/gimp/win32/pspi.html]("http://www.gimp.org/~tml/gimp/win32/pspi.html")

---

### Post by tripolitan on 2009-04-16
If you can find an operating system with applications that support your needs by 100%, stick to it. First program you linked works on MAC, the others have MAC equivalents. I could probably suggest using Cinelerra and GIMP (has many filters but not quite the same as PhotoShop) but Cinelerra is a resource hog.

Check these sites:
[http://www.linuxalt.com/](http://www.linuxalt.com/) and 
[http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software](http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software)

---

